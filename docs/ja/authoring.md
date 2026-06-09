# パッケージの作成

[← ドキュメント目次](../../README.ja.md) · [English](../en/authoring.md)

## Package Lifecycle

新しいパッケージを作成します。

```sh
mkdir -p packages/example
cd packages/example
pnlx init
```

`pnlx.json` を編集し、パッケージの成果物を生成します。

```sh
pnlx validate
pnlx gen example
```

プロジェクトルートからインストールします。

```sh
pnl install packages/example
pnl install file:///absolute/path/to/example
pnl install https://github.com/m3m0r7/pnl-packages/tree/main/packages/libusb
```

インストール済みの bridge を再ビルドします。

```sh
pnlx build
```


## Writing `pnlx.json`

`pnlx.json` は拡張側のマニフェストです。パッケージを識別し、生成される PHP クラスを宣言し、bridge の生成と読み込みに必要なネイティブライブラリおよびヘッダーを記述します。

最小構成は次のとおりです。

```json
{
  "schema_version": "2026-07-01",
  "name": "vendor/package",
  "version": "0.1.0",
  "description": "PHP FFI wrapper for a native library.",
  "authors": [
    {
      "name": "Your Name"
    }
  ],
  "license": "MIT",
  "entrypoint": "src/generated/index.php",
  "class": "Pnlx\\Vendor\\Package",
  "platforms": [
    {
      "os": "darwin",
      "arch": "aarch64"
    }
  ],
  "requires": {
    "native-key": {
      "symbol_prefix": "native",
      "library_names": [
        "libnative.dylib",
        "libnative.so",
        "native.dll"
      ],
      "header_names": [
        "native/native.h"
      ],
      "version": ">=1.0.0 & <2.0.0",
      "required": true
    }
  },
  "dependencies": {}
}
```

各フィールド:

| フィールド | 型 | 必須 | 意味 |
| --- | --- | --- | --- |
| `schema_version` | string | yes | マニフェストのスキーマバージョン。現在の値は `2026-07-01`。 |
| `name` | string | yes | `vendor/package` 形式のパッケージ識別子。`@pnlx/packages` 配下のインストールパスを決定する。 |
| `version` | string | yes | パッケージの SemVer。これは拡張ラッパーのバージョンであり、必ずしもネイティブライブラリのバージョンではない。 |
| `description` | string | yes | 人間が読めるパッケージの概要。 |
| `authors` | array | yes | メンテナまたは上流のクレジット。`email` は任意。 |
| `license` | string | yes | パッケージのライセンス表記。上流ネイティブライブラリのライセンスが明確になるようにする。 |
| `entrypoint` | string | yes | 生成される PHP のエントリポイント。通常は `src/generated/index.php`。 |
| `class` | string | yes | 生成される PHP エンティティクラスの完全修飾名。名前空間を含める必要がある。 |
| `class_prefix` | string | optional | 生成されるクラス／コンテキスト名に付与するプレフィックス。クラス名の衝突を避ける場合を除き空のままにする。 |
| `platforms` | array | yes | ラッパーパッケージがサポートする OS/arch の組み合わせ。 |
| `requires` | object | yes | ネイティブライブラリの要件。少なくとも 1 エントリを含める必要がある。 |
| `dependencies` | object | yes | 他の pnl 拡張への依存。依存解決はまだ完成していない。 |

### Package Identity

`name` はインストールされるパッケージのパスを制御します。

```json
"name": "libusb/libusb"
```

これは次の場所にインストールされます。

```text
@pnlx/packages/libusb/libusb
```

生成される PHP の名前空間はこれとは独立しており、`class` から決まります。

```json
"class": "Pnlx\\Libusb\\Libusb"
```

これにより次が生成されます。

```text
src/generated/Libusb.php
src/generated/LibusbContext.php
```

### Native Requirements

`requires` はネイティブライブラリの識別子をキーとします。このキーは、ロックファイルや pathmap ファイル、bridge のパスで使われます。

libusb の例:

```json
"requires": {
  "libusb-1.0": {
    "symbol_prefix": "libusb",
    "library_names": [
      "libusb-1.0.dylib",
      "libusb-1.0.so",
      "libusb-1.0.dll"
    ],
    "header_names": [
      "libusb-1.0/libusb.h"
    ],
    "version": ">=1.0.0 & <2.0.0",
    "required": true
  }
}
```

要件のフィールド:

| フィールド | 必須 | 意味 |
| --- | --- | --- |
| `symbol_prefix` | optional | 残す C 関数のプレフィックス。名前がこれで始まる宣言だけがラップされる（例: `libnfc` は `nfc_*` をエクスポートする）。`""` を指定すると **すべての** 宣言が残り、インラインヘッダーは libclang のフィルタリングを通さずそのまま渡される。省略した場合は、ライブラリキーから導出したプレフィックスがデフォルトとして使われる。 |
| `library_names` | yes | `load_paths`、環境変数のパス、システムの既定パスから探索する共有ライブラリのファイル名候補。各エントリは文字列、またはオブジェクト `{ "name": "libc.dylib", "virtual": true }` のいずれか。詳しくは [Virtual libraries](#virtual-libraries) を参照。 |
| `header_names` | optional | 解決された include ルートから展開される、公開 C ヘッダーのパス候補。`header_inline` または `header_url` を指定する場合は省略する。 |
| `header_inline` | optional | マニフェストに直接埋め込む C 宣言。ディスクからヘッダーを読まず、この内容をそのまま使う。[Inline headers](#inline-headers) を参照。 |
| `library_url` | optional | ローカルのライブラリパスを探索する代わりに、ネイティブライブラリを取得するリモートソース（`http(s)`／`ftp`／`git`）。 |
| `header_url` | optional | C ヘッダーを取得するリモートソース（`http(s)`／`ftp`／`git`）。 |
| `version` | yes | ネイティブライブラリのバージョン制約（例: `>=1.0.0 & <2.0.0`）。 |
| `required` | yes | このネイティブ要件が必須かどうか。現状の生成処理は、ネイティブライブラリが必須であることを前提とする。 |

1 つの要件には、ちょうど 1 つのヘッダーソース（`header_names`、`header_inline`、`header_url` のいずれか）が必要です。

#### Inline headers

`header_inline` は、`pnlx.json` の中に直接 C API を宣言します。実際のヘッダーを同梱したり探索したりする必要のない、小さなライブラリやシステムライブラリに最適です。文字列は C ヘッダーとして扱われます。

```json
"requires": {
  "libc": {
    "symbol_prefix": "",
    "library_names": [
      { "name": "libc.dylib", "virtual": true },
      { "name": "libc.so.6", "virtual": true }
    ],
    "header_inline": "int printf(const char *format);\nint puts(const char *s);\n",
    "version": ">=0.0.0",
    "required": true
  }
}
```

- `symbol_prefix` を `""` に設定すると、インラインヘッダーはそのまま（libclang のパスを通さずに）使われます。そのため、公開したい宣言を正確に書いてください。
- 可変長引数関数（`...`）はラップできません。代わりに引数の数を固定したシグネチャを宣言してください（例: `int printf(const char *format);`）。

#### Virtual libraries

一部のライブラリはオペレーティングシステムが提供しており、解決すべき **ディスク上のファイルが存在しません**。最も代表的なのは `libc` で、macOS では dyld の共有キャッシュ内にしか存在しません。このようなエントリには `"virtual": true` を付けます。

```json
"library_names": [
  { "name": "libc.dylib", "virtual": true },
  { "name": "libc.so.6", "virtual": true },
  { "name": "msvcrt.dll", "virtual": true }
]
```

仮想ライブラリは **名前でリンク** され、ファイルとして存在することは一切要求されません。非仮想のエントリが解決できる場合、pnl は引き続き実際のディスク上の一致を優先し、仮想エントリはフォールバックとして使われます。

### Header And Bridge Generation

`pnlx gen <target>` は `pnlx.json` を読み、ヘッダーを解決し、生成された成果物を `src/generated` に書き出します。

生成されるファイル:

```text
src/generated/<target>.ffi.php
src/generated/<Class>.php
src/generated/<Class>Context.php
src/generated/function.aliases.php
src/generated/<target>.bridge.rs
src/generated/index.php
```

生成された PHP エンティティは、検出されたネイティブ関数に対応する具体的なメソッドを公開し、FFI 呼び出しをコンパイル済みの Rust bridge へ委譲します。生成された Rust bridge は `pnlx_bridge_*` 関数をエクスポートし、ネイティブライブラリへ直接リンクします。

### Preload And Postload Hooks

パッケージが生成されたエントリポイントの隣に次のファイルを持っている場合、生成される `index.php` はそれらを require します。

```text
src/generated/preload.php
src/generated/postload.php
```

`preload.php` は任意のグローバル関数登録の前に実行されます。`postload.php` はその後に実行されます。どちらも `$runtime` と `$runtimeVarName` にアクセスできます。
