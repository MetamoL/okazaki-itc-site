# CLAUDE.md — 岡﨑ＩＴコンサルティング 名刺サイト

個人事業主（岡﨑 好信 / 岡﨑ＩＴコンサルティング株式会社）の「名刺代わり」1ページ静的サイト。
HTML / CSS / JS のみ。AWS S3 + CloudFront などの静的ホスティングを想定。モバイルファースト。

- リポジトリ: GitHub `MetamoL/okazaki-itc-site`（Private）。最終的にクライアントへ譲渡予定（譲渡後、制作側は共同編集者として残る）。
- 公開対象: `index.html` / `css/` / `js/` / `images/` / favicon類 / `ogp.jpg` / `robots.txt` / `sitemap.xml`
- 非公開（リポジトリに含めない）: `client_source/`（依頼主の私的資料。`.gitignore` 済）

---

## 開発体制：通常開発（2026-07-14 変更）

旧ルール「Planner / Generator / Evaluator を独立サブエージェントで回す独立ハーネス」は **廃止**（オーナー指示・2026-07-14）。以降は通常の開発フローで進める：

1. 要件確認 → 実装（ワークスペース共通のモデル運用に従う。委任するなら `impl` 等）
2. ブラウザ実機で検証（`launch.json` の `business-card`／port 8123）
3. `git commit` → `git push`（main＝即本番反映）

### 品質チェックリスト（検証時、変更に関係する項目だけ確認）
1. 要件一致（必要セクションが揃い実データが入っている）
2. レスポンシブ（375 / 768 / 1024px で横スクロール・崩れ 0）
3. コンソール 0 件・JS 無効でも本文が読めるフォールバック
4. アクセシビリティ（alt／見出し階層の論理性／コントラスト比 4.5:1 以上／`:focus-visible`／aria／`prefers-reduced-motion`）
5. インタラクション（ハンバーガー開閉・aria 同期・Esc/リンクで閉じる・スムーススクロール・出現アニメ）
6. SEO / 共有（title・description・OGP・canonical・favicon・robots・sitemap）
7. パフォーマンス（画像サイズ・lazy・レンダリングブロック）
8. コード品質 / 保守性（セマンティック・未使用 CSS・デプロイ前 TODO）

---

## 環境・動作確認の要点
- **node / python が無い環境**のため、プレビューは PowerShell の簡易静的サーバー（`.claude/static-server.ps1`）。`launch.json` の設定名 **`business-card`**（port 8123）で起動。
- `.ps1` は **ASCII のみ**で書く（Windows PowerShell 5.1 が CP932 で読み、日本語コメントを壊して構文エラーにするため）。
- 画像最適化・OGP/favicon 生成は **.NET System.Drawing**（PowerShell）で実施（外部ツール不要）。
- 日本語を含む git コミットメッセージは **UTF-8 ファイル＋`git commit -F`** で渡す（PowerShell の引数経由は文字化けし得る）。氏名は **「岡﨑」（﨑＝立つ崎）** で統一。

## 現在地（随時更新）
- **2026-07-14：開発体制を独立ハーネスから通常開発へ変更**（オーナー指示）。初期構築期（Sprint 0〜D）は独立ハーネスで QA し、Evaluator が実装者の見落とし（コントラスト 4.49:1・`:focus-visible` 欠如等）を検出した実績はあるが、完成後の保守フェーズでは速度・コストを優先。
- Sprint 0〜8 ＋ 完成度向上 Sprint A〜D 完了。すべて独立ハーネス（独立Generator→独立Evaluator）で QA 合格・退行ゼロ。
  - A: ヒーローのフレーズ単位改行・余白／ナビ現在地ハイライト(aria-current)／セクション区切り
  - B: 数字ストリップ(30年以上/12年/2010年〜/2013年)／新聞カードの contain 全面表示／CTA文言＋mailto件名・本文プリセット
  - C: スキップリンク／モバイルメニューのフォーカス管理(閉時フォーカス不可化＋復帰)／`404.html`／印刷スタイル
  - D: JSON-LD(Person+Organization)／ヒーローLCP最適化(preload＋fetchpriority)。WebPは環境にエンコーダ無く見送り(壊れ参照なし)
- **公開済み（GitHub Pages）**：**https://metamol.github.io/okazaki-itc-site/**（Public・`main`/root配信・`.nojekyll`・HTTPS強制。`git push`で自動再デプロイ）
- **協働体制（譲渡完了・2026-06-10）**：リポジトリは **`OkazakiIT/okazaki-itc-site`（岡﨑さん所有）**。MetamoL は共同編集者(write)として再追加済み・push 実証済み。両者 `push` で保守可。
  - 公開URL：**https://okazakiit.github.io/okazaki-itc-site/**（Pages built・全アセット200・絶対URLも新URLに統一済み。旧 metamol URL は無効・リダイレクトなし）。
  - ローカル remote は `OkazakiIT/okazaki-itc-site` に切替済み。
- 残タスク：**なし**。独自ドメイン・WebP化は「対応しない」のまま。
- 保守フロー：ファイル編集 → `git commit` → `git push`（main）で本番反映。
