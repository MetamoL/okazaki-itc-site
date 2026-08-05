# デプロイ手順 & 公開前チェックリスト

現行の配信は **GitHub Pages**（`OkazakiIT/okazaki-itc-site` の `main`/root）。**`main` への push で自動再デプロイ**（2〜3分で反映）。公開URL＝<https://okazakiit.github.io/okazaki-itc-site/>
（当初計画していた AWS S3 + CloudFront 構成は不採用。旧手順は git 履歴を参照）

---

## 1. 公開対象 / 対象外

**公開する**
```
index.html / 404.html
css/style.css
js/main.js
images/*.jpg
favicon.svg / favicon-32.png / apple-touch-icon.png
ogp.jpg
robots.txt / sitemap.xml
```

**サイトの構成要素ではない**
```
client_source/   ← 依頼主の素材原本（PDF・原寸画像など）。★.gitignore 済＝リポジトリに入れない
.claude/         ← 開発用（検証サーバー等）
*.md             ← ドキュメント（README / CLAUDE / DEPLOY / SEARCH_CONSOLE）。
                   リポジトリには置くが sitemap にも導線にも載せない
```

---

## 2. push 前チェック

- [ ] 375 / 768 / 1280px で横スクロールが無い
- [ ] ブラウザのコンソールにエラーが無い
- [ ] 絶対URL（`og:url` / `og:image` / `canonical` / 構造化データ / `robots.txt` / `sitemap.xml`）が公開URLと一致している
- [ ] OGP を X / Facebook のシェア確認で通す（画像・文言を変えたときだけ）
- [ ] `index.html` に `[ Sprint x で実装 ]` 等の残骸が無い

---

## 3. 画像メモ

公開画像は `client_source/` の原寸から縮小・再圧縮済み（hero 3.1MB→約150KB 等、合計 約470KB）。WebP 化・独自ドメインは「対応しない」で確定。
