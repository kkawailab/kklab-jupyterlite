# kklab-jupyterlite

ブラウザだけで動く Jupyter 環境 [JupyterLite](https://github.com/jupyterlite/jupyterlite) を GitHub Pages で公開するリポジトリです。

## ✨ サイトを開く

**https://kkawailab.github.io/kklab-jupyterlite/**

サーバー不要で、Python カーネル（Pyodide / WebAssembly）がブラウザ内で動作します。

## 使い方

1. 上記 URL を開くと JupyterLab（Lite 版）が起動します
2. `intro.ipynb` を開いてセルを実行してみてください（`Shift + Enter`）
3. `%pip install numpy` のように、Pyodide 対応パッケージを追加インストールできます

作成したノートブックはブラウザのローカルストレージに保存されます（サーバーには送信されません）。

## 収録チュートリアル

[kklab-jupyterlite-tutorials](https://github.com/kkawailab/kklab-jupyterlite-tutorials) のノートブック集を収録しています（日本語）。
詳しい学習パスはサイト内の `README.md` を参照してください。

| ディレクトリ | 内容 |
|---|---|
| `jupyterlite/` | JupyterLite の基本操作入門 |
| `python/` | Python 文法入門（ライブラリ読み込み・日本語フォント設定の解説付き） |
| `r/` | R 文法入門・R 統計演習（xeus-r カーネル用） |
| `numpy/` `pandas/` `matplotlib/` | 基礎ライブラリ（初級・中級） |
| `seaborn/` `scipy/` `statsmodels/` | データ分析・統計 |
| `sklearn/` | 機械学習 |
| `folium/` `ipywidgets/` | 地図可視化・ウィジェット |
| `exercises/` | 練習問題集（計 129 問） |

## カーネル

- **Python (Pyodide)** — ほとんどのノートブックで使用。`piplite.install()` / `%pip install` でパッケージ追加可
- **R (xeus-r)** — `r/` 配下のノートブック用。`environment.yml` でビルド時に組み込み

## 仕組み

- `main` ブランチへ push すると GitHub Actions（`.github/workflows/deploy.yml`）が起動
- `jupyter lite build --contents content --output-dir dist` で静的サイトをビルド
- GitHub Pages へ自動デプロイ

## ノートブックの追加

`content/` ディレクトリに `.ipynb` ファイルを追加して push すると、サイトに反映されます。

## ローカルでのビルド（任意）

```bash
pip install -r requirements.txt
jupyter lite build --contents content --output-dir dist
jupyter lite serve --contents content  # http://localhost:8000 で確認
```
