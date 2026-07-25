# CLAUDE.md — 岡﨑ＩＴコンサルティング 名刺サイト

個人事業主（岡﨑 好信 / 岡﨑ＩＴコンサルティング株式会社）の「名刺代わり」1ページ静的サイト。
HTML / CSS / JS のみ・モバイルファースト。**保守フェーズ（残タスクなし）**。

- リポジトリ: **`OkazakiIT/okazaki-itc-site`（岡﨑さん所有・Public）**。MetamoL は共同編集者(write)＝両者 push で保守可。譲渡完了 2026-06-10（MetamoL の「Repositories」タブには出ない）
- 公開対象: `index.html` / `css/` / `js/` / `images/` / favicon類 / `ogp.jpg` / `robots.txt` / `sitemap.xml`
- 非公開: `client_source/`（依頼主の私的資料・`.gitignore` 済）

## 開発フロー（通常開発）

旧「Planner / Generator / Evaluator を独立サブエージェントで回す独立ハーネス」は **2026-07-14 に廃止**（オーナー指示。初期構築期は QA に効いたが、保守フェーズでは速度・コストを優先）。以降は通常フロー：

1. 要件確認 → 実装（委任するならワークスペース共通の `impl` 等）
2. ブラウザ実機で検証（`launch.json` の `business-card`／port 8123）
3. `git commit` → `git push`（**main＝即本番反映**）

### 品質チェックリスト（変更に関係する項目だけ確認）
1. 要件一致（必要セクションが揃い実データが入っている）
2. レスポンシブ（375 / 768 / 1024px で横スクロール・崩れ 0）
3. コンソール 0 件・JS 無効でも本文が読めるフォールバック
4. アクセシビリティ（alt／見出し階層／コントラスト比 4.5:1 以上／`:focus-visible`／aria／`prefers-reduced-motion`）
5. インタラクション（ハンバーガー開閉・aria 同期・Esc/リンクで閉じる・スムーススクロール・出現アニメ）
6. SEO / 共有（title・description・OGP・canonical・favicon・robots・sitemap）
7. パフォーマンス（画像サイズ・lazy・レンダリングブロック）
8. コード品質（セマンティック・未使用 CSS・デプロイ前 TODO）

## 環境の要点（ハマりどころ）

- **node / python が無い環境**。プレビューは PowerShell の簡易静的サーバー（`.claude/static-server.ps1`）＝`launch.json` の **`business-card`**（port 8123）
- **`.ps1` は ASCII のみで書く**（Windows PowerShell 5.1 が CP932 で読み、日本語コメントを壊して構文エラーにする）
- 画像最適化・OGP/favicon 生成は **.NET System.Drawing**（PowerShell）で実施（外部ツール不要）
- 日本語を含む git コミットメッセージは **UTF-8 ファイル＋`git commit -F`** で渡す（引数経由は文字化けし得る）
- 氏名は **「岡﨑」（﨑＝立つ崎）** で統一

## 触るときの注意（現役のガード）

- **公開URL（正）**：<https://okazakiit.github.io/okazaki-itc-site/>（GitHub Pages・`main`/root 配信・`.nojekyll`・HTTPS 強制・push で自動再デプロイ）
  - 📝 URL を `**` で囲むと末尾の `**` までリンクに食われて 404 になる。太字にせず `<...>` で囲む
  - ⚠️ 旧URL `metamol.github.io/okazaki-itc-site/` は**譲渡で消滅済み**（404・リダイレクト無し）＝ドキュメントやリンクに書かない
- ⚠️ **Google Search Console の所有権確認タグ（`index.html` の head）は削除禁止**（外すと所有権が失われる）。手順書＝`SEARCH_CONSOLE.md`
- 🔒 **個人情報ガード**：`client_source/`（顔写真の原本・職務経歴書・名刺PDF＝自宅住所/携帯番号）は `.gitignore` 済み。加えて `.git/hooks/pre-commit` が `client_source/` 配下・秘密ファイル・携帯番号/郵便番号の混入をブロックする（**このPCローカルのみ＝別PCでは要再設置**）。**リポジトリは Public なので一度 push すると履歴から消せない**
- **残タスク＝なし**。独自ドメイン・WebP 化は「対応しない」で確定。デザイン全面刷新（2026-07-14・クライアント承認済み）と名刺入稿データ（両面 55×91mm・PDF）納品まで完了＝`client_source/meishi/` の `card-source.html` を直して再出力すれば微調整可
- 完了済み Sprint（0〜8・A〜D）の内訳は **git 履歴が正本**（ここには残さない）
