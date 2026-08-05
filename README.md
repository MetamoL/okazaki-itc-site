# 岡﨑ＩＴコンサルティング 名刺サイト

個人事業主（岡﨑 好信 / 岡﨑ＩＴコンサルティング株式会社）の「名刺代わり」となる1ページ完結・モバイルファーストの静的サイト。バックエンド無し（HTML / CSS / JS のみ）。

- **公開URL**: <https://okazakiit.github.io/okazaki-itc-site/>（GitHub Pages・`main` への push で自動公開）
- 状態: デザイン刷新（2026-07-14・クライアント承認済み）まで完了し、現在は**保守フェーズ（残タスクなし）**。作業の経緯は git 履歴を参照。
- 関連ドキュメント: 開発の約束事＝`CLAUDE.md` ／ デプロイ手順・公開前チェック＝`DEPLOY.md` ／ Google 検索への登録＝`SEARCH_CONSOLE.md`

## ディレクトリ構成

```
okazaki-itc-site/
├── index.html          … サイト本体（1ページ完結）
├── 404.html            … 404 ページ
├── css/
│   └── style.css       … 共通スタイル（デザイントークンで一元管理）
├── js/
│   └── main.js         … 共通スクリプト（ナビ開閉・スクロール演出）
├── images/             … 公開用の画像（ポートレート・実績写真など）
├── ogp.jpg / favicon.svg / favicon-32.png / apple-touch-icon.png
├── robots.txt / sitemap.xml
└── client_source/      … ★依頼主からの素材置き場（公開対象外・リポジトリに含めない）
    ├── pdf/            …   テキスト元のPDF
    ├── images/         …   顔写真・ロゴ・実績写真など
    └── meishi/         …   名刺入稿データ（card-source.html から再出力）
```

## 公開対象 / 対象外

- **サイト本体**: `index.html` / `404.html` / `css/` / `js/` / `images/` / favicon類 / `ogp.jpg` / `robots.txt` / `sitemap.xml`
- **サイトの構成要素ではない**: `client_source/`（素材の元データ。★リポジトリに入れない）・`.md` ドキュメント（リポジトリには置くが導線に載せない）

## ローカル確認

`index.html` をブラウザで開くだけで表示できる（ビルド不要）。
確認用のブレークポイント: 375px（スマホ） / 768px（タブレット） / 1024px〜（PC）。
