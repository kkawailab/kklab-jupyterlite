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
