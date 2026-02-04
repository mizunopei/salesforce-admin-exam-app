# SF Admin 問題集

Salesforce認定アドミニストレーター試験対策のためのPWA（Progressive Web App）学習アプリです。

## 機能

- **全問モード**: 年度別（2023/2024/2025）に全問を順番に解く
- **ランダムモード**: 指定した問題数をランダムに出題
- **一問一答（選択式）**: 選択問題をランダムに出題
- **一問一答（正誤問題）**: 正誤問題をランダムに出題
- **復習モード**: 間違えた問題を復習
- **オフライン対応**: PWAとしてインストール可能、オフラインでも学習可能
- **複数選択問題対応**: 「2つ選べ」などの問題で必要な選択数を表示

## 技術スタック

- React 18（CDN経由）
- Tailwind CSS
- Service Worker（オフラインキャッシュ）
- Cloudflare Pages（ホスティング）

## ローカル開発

### 前提条件

- Python 3.x
- 問題データJSONファイル（gitignoreで除外されています）

### セットアップ

1. 問題データファイルを配置:
   - `過去問0_修正済.json` (2023年度)
   - `2024年度_修正済.json` (2024年度)
   - `2025年度_修正済.json` (2025年度)
   - `一問一答.json` (正誤問題)

2. ビルドスクリプトを実行:
   ```bash
   python3 build.py
   ```

3. ローカルサーバーで起動:
   ```bash
   python3 -m http.server 8000
   ```

4. ブラウザで http://localhost:8000 を開く

## デプロイ

Cloudflare Pagesにデプロイされています。`main`ブランチへのプッシュで自動デプロイされます。

## ファイル構成

```
├── index.html          # メインアプリケーション
├── manifest.json       # PWAマニフェスト
├── sw.js              # Service Worker
├── build.py           # ビルドスクリプト
├── data/
│   ├── mc_questions.json   # 選択問題データ
│   └── tf_questions.json   # 正誤問題データ
└── functions/
    └── _middleware.js  # Cloudflare Pagesミドルウェア
```

## ライセンス

Private
