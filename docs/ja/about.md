# pnl について

[← ドキュメント目次](../../README.ja.md) · [English](../en/about.md)

## About pnl

pnl は 2 つのコマンドラインツールを提供します。

- **`pnl`**: プロジェクト側のインストール、ロックファイル、検証、パッケージ一覧を管理します。
- **`pnlx`**: 拡張のオーサリング、ラッパー生成、Rust bridge の再ビルドをサポートします。

生成されるインストールファイルは、Composer の `vendor/` ディレクトリではなく `@pnlx/` 以下に置かれます。アプリケーションはまず SDK 依存のために Composer を読み込み、続いてネイティブ拡張のために `@pnlx/autoload.php` を読み込みます。

プロジェクトは次のファイルで記述されます。

- `pnl.json`: 編集可能なプロジェクトマニフェスト。
- `pnlx-lock.json`: プラットフォーム固有のロックファイル。
- `@pnlx/pnlx-pathmap.json`: ネイティブライブラリおよびヘッダーのパスマッピング。
- `@pnlx/autoload.php`: PHP のエントリポイント。

### Requirements

- Rust 1.85+
- FFI 拡張を有効にした PHP 8.2+
- Composer 2.x
- Git 2.x
- POSIX `make`

macOS/aarch64 上で Homebrew によるパッケージ管理を用いて検証されています。

### Installation Sources

`pnl install` は複数のソース形式を受け付けます。

- ローカルファイルシステムのパス
- `file://` URL
- GitHub の HTTPS URL
- ブランチ指定（任意）付きの Git SSH URL
- ルートに `pnlx.json` を含む Git リポジトリ

```sh
pnl install packages/libusb
pnl install file:///absolute/path/to/libusb
pnl install https://github.com/m3m0r7/pnl-packages/tree/main/packages/libusb
```

### PHP Usage

アプリケーションは、生成されたエンティティクラスを通じてネイティブライブラリとやり取りします。C ライブラリは関数の集まりなので、エンティティは **static** で、インスタンス化しません。最初の static 呼び出しで自動的に boot します。

```php
require_once __DIR__ . '/@pnlx/autoload.php';

use Pnlx\Libusb\Libusb;

$result = Libusb::libusbInit(null);
```

生成されたコードは、static なエンティティメソッドと、任意で利用できるグローバルな PHP 関数の両方をサポートします。これは `features.use_functions` の設定によって制御されます。

> **ステータス:** pnl は初期段階の実装です。ローカルパス、`file://`、git ベースのインストールは現時点で動作します。リポジトリインデックスの解決、署名付きパッケージインデックス、FTP ダウンロードは設計中です。
