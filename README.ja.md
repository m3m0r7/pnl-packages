# pnl Packages

[English](README.md)

このリポジトリには、PHP のネイティブライブラリ拡張向けのプロトタイプ的なパッケージマネージャ兼ランタイムツールチェーンである [pnl](https://github.com/m3m0r7/pnl) のサンプル `pnlx` 拡張パッケージが含まれています。

パッケージとは、`pnlx.json` を含むインストール可能な拡張のルートです。`pnl install` を実行すると、パッケージのファイルは `@pnlx/packages/<vendor>/<package>` へコピーされ、`src/generated` のソースは無視されたうえで、対象マシン向けに再生成されます。

## ドキュメント

- [pnl について](docs/ja/about.md) — pnl/pnlx の仕組み・必要なもの・インストール元。
- [パッケージの作成](docs/ja/authoring.md) — パッケージのライフサイクルと `pnlx.json` の全リファレンス（inline header・virtual library 含む）。
- [同梱パッケージ](docs/ja/packages.md) — 同梱パッケージの一覧とライセンス。

