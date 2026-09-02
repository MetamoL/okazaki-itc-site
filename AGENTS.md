# AGENTS.md — Codex作業入口

このリポジトリで作業する前に、まず `CLAUDE.md` を読み、公開や配信に関わる変更では `DEPLOY.md` も読む。構成の確認が必要なら `README.md` を参照する。

## 事故防止

- `main` への push は GitHub Pages の本番公開に直結する。`git push`・公開操作はオーナーの明示承認後にだけ行う。検証後の `git commit` は実施してよい。
- `client_source/` は非公開の原本置き場で、公開リポジトリに追加・ステージしない。一度 push した個人情報は履歴から消せない。
- `index.html` の Google Search Console 所有権確認タグは削除しない。手順は `SEARCH_CONSOLE.md` を読む。
- 変更前に `git status --short` で既存変更を確認し、他者の変更を戻さない。

## 確認

ビルドは不要。`index.html` をブラウザで開き、変更に応じて 375 / 768 / 1024px（公開前は `DEPLOY.md` 記載の幅）で表示とコンソールを確認する。
