<!-- codex-environment: 2026-09 -->
# 名刺サイト

受託した事業紹介の静的サイト。`index.html`・`404.html`、`css/style.css`、`js/main.js` が主な編集先。ビルド不要。依頼主の素材原本は `client_source/`、公開範囲は `README.md`、公開前条件は `DEPLOY.md`。

素材原本を公開repoへ追加せず、確認済みの名称・事業内容・連絡先を推測で変更しない。検索確認タグは `SEARCH_CONSOLE.md` に対応するため削除しない。個人情報を環境指示へ複製しない。

対象ページをブラウザで表示し、375/768/1024px付近のレイアウト、ナビ、リンク、フォーカスを変更に応じて確認する。JavaScriptは `node --check js/main.js` でも構文確認できる。mainへのpushはGitHub Pagesへの公開に直結する。
