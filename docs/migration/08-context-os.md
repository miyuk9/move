# コンテキストOS / 第二の脳（Personal Knowledge System）

各AI（ChatGPT / Claude / Gemini / Antigravity）に「自分」を理解させる共通コンテキストと、
それを継続的に育てる第二の脳の設計。プロジェクト通称は **「Life Design OS」**。
出典: [04-source-chats/09-context-os-second-brain.md](04-source-chats/09-context-os-second-brain.md)
きっかけ記事: https://note.com/ritsuto2525/n/n050a50b2449c

## 基本思想
> 「1枚の巨大なコンテキストファイル」ではなく、
> 「**小さなマスターコンテキスト＋分割された第二の脳**を継続的に育てる」。

- AIの記憶そのものを保存場所にしない。**Markdownファイルを共通の正本**にする。
- 毎回読み込む指示ファイルは簡潔・具体的に（目安200行未満）。

## フォルダ構成（Obsidian内）
```
01_Context/
├─ my_context.md        ← 現在の重要事項＋詳細ファイルの場所を示す短い索引（全部入りにしない）
├─ profile.md
├─ values_vision.md
├─ work_business.md
├─ writing_voice.md
├─ ai_working_rules.md
└─ context_changelog.md
```

## AIの役割分担
| AI | 役割 | 主な使いどころ |
|---|---|---|
| **ChatGPT** | 日々の対話と整理 | 音声壁打ち / アイデア深掘り / 会話終了時の要約 / 最新リサーチ / 企画・教材整理 |
| **Claude Cowork** | Obsidianのファイル作業（今回の目的に最も近い） | フォルダ内Markdown等の作成・編集・分類（差分提示→承認） |
| **Antigravity** | 仕組み作り・反復作業 | Web制作 / 複雑な自動処理 / Skills / エージェント管理 |
| **Claude Code / Antigravity IDE** | コード中心の開発 | アプリ・サイトの実装 |
| **Gemini Notebook**（旧NotebookLM） | 大量資料の分析（保存場所にはしない） | 音声ジャーナル横断 / 教材・文体分析 / 大量PDF要約 / 共通テーマ抽出 |

## 会話終了時の要約フォーマット（第1段階の要）
会話の最後に必ずこの形式でまとめ、Obsidian `00_Inbox/AI-Chats` に保存：
1. 相談の目的
2. 分かったこと
3. 採用した案
4. 採用しなかった案と理由
5. 未解決
6. 次に行うこと
7. 設計判断ログ
8. 発信・教材に使える内容

> ※ この docs/migration/ の整理（決定/要件/未解決/設計/事業）は、実質この8項目フォーマットを実践している。

## 自動化の3段階
1. **手動＋形式統一**: 上の8項目でまとめてObsidian受信箱へ保存。
2. **半自動（Cowork/Antigravity）**: 週1で受信箱を読ませ、保存先候補/重複/統合候補/次アクション/my_context.mdへ反映すべき安定情報 を提出 → 人が承認して反映。
3. **Make等を追加**: 例＝Android音声→Drive音声受信箱→Make検知→文字起こし・要約→「取り込み待ち」→Cowork/Antigravityが分類案→確認後に正式保存。
   - Makeは視覚型で分かりやすい。n8nは自由度高いが保守負担増、現段階では不要。

## 保存場所と正本の切り分け（重要）
- **個人の知識・コンテキスト（Vault）の正本 = Obsidian**（同期は Obsidian Sync、E2E暗号化可・履歴あり）。
- **GitHubは個人Vaultの正本にしない**。GitHubは以下に限定：
  - Webサイト・プログラム（コード）
  - 公開可能な教材
  - 個人情報を除いたテンプレート
  - Obsidianの追加バックアップ
- **顧客情報・家族情報・健康/経済情報を含むVault全体はGitHubに置かない。**

> ⚠️ これは 06-architecture.md の「GitHub＝正本」と一見矛盾する。実際は対象が違う（コード/アプリ vs 個人知識）。→ 01-decisions.md D-06 で整理、残る論点は 03-open-questions.md Q-03。

## 全体フロー
```
【入力】音声・録音・メモ・スクショ
   ↓
【一時保管】ChatGPTプロジェクト / Google Drive / Obsidian 00_Inbox
   ↓
【分析】ChatGPT / Gemini Notebook / Grok
   ↓
【整理・ファイル操作】Claude Cowork / Antigravity
   ↓
【正本】Obsidian
   ↓
【利用】発信・教材・商品設計・Life Design OS・教室運営
```

## 次の作業（記事＆リサーチが提案していたもの）
- 蓄積情報から **my_context.md 初版** と Obsidian用フォルダ一式（01_Context/）を作成する。
