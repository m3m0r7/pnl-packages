# pnl Packages

[English](README.md)

このリポジトリには、PHP のネイティブライブラリ拡張向けのパッケージマネージャ兼ランタイムツールチェーンである [pnl](https://github.com/m3m0r7/pnl) の公式 `pnlx` 拡張パッケージが含まれています。

パッケージとは、`pnlx.json` を含むインストール可能な拡張のルートです。`pnl install` を実行すると、パッケージのファイルは `@pnlx/packages/<vendor>/<package>` へコピーされ、`src/generated` のソースは無視されたうえで、対象マシン向けに再生成されます。

`packages/repository-index.json` は全パッケージ・全バージョンを列挙した生成物のカタログです。これにより `pnl search` はクローンせずに HTTP 経由でこのリポジトリを一覧できます。パッケージやバージョンを変更したら再生成してください。

```sh
pnl repo index packages \
  --base-url https://github.com/m3m0r7/pnl-packages/tree/main/packages
```

## ドキュメント

- [pnl について](docs/ja/about.md) — pnl/pnlx の仕組み・必要なもの・インストール元。
- [パッケージの作成](docs/ja/authoring.md) — パッケージのライフサイクルと `pnlx.json` の全リファレンス（inline header・virtual library 含む）。
- [同梱パッケージ](docs/ja/packages.md) — 同梱パッケージの一覧とライセンス。
