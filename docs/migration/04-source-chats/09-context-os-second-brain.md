# 元チャット 09: ChatGPTにCowork的機能はある？ → my_context.md / 第二の脳の自動化リサーチ

> 原文保存（壁打ちログ）。ChatGPTのCowork相当機能の話から、note記事をきっかけに「my_context.md（共通コンテキスト）＋第二の脳」を各AIで育てる情報アーキテクチャのリサーチへ発展。
> 要約・確定版は 08-context-os.md を参照。設計上の重要論点（正本はObsidianかGitHubか）は 01-decisions.md / 03-open-questions.md に反映。

## 発言（本人）
チャットGPTにコワークのような機能ある？

## 回答（AI）— ChatGPTのCowork相当
Claudeの「Cowork」に近い機能はChatGPTにもあるが、単一機能名ではなく複数の組み合わせ。
- いちばん近いのは「ChatGPT Work」＝資料やアプリで仕事を最初から最後まで進める機能。文書/スライド/表計算/グラフ/PDF/画像の作成・編集、Gmail/Google Drive/Slack/Notion連携。ただし独立ボタンがあるわけではなく仕事用機能の総称に近い。

| したいこと | 使う機能 |
|---|---|
| 一つのテーマを継続して進める | プロジェクト |
| 資料・指示・過去会話をまとめる | プロジェクト |
| 文章やHTMLを横で見ながら修正 | Canvas |
| PDF・画像・スライド・表を作る | Work機能 |
| Webサイトやプログラムを作る | Codex |
| 複数人で資料や会話を共有 | 共有プロジェクト |

- 「Life Design OS」なら、プロジェクトを作る→設計書/HTML/画像/メモを入れる→専用ルール設定→依頼、という形がCoworkに近い。
- ＝ ChatGPTの「プロジェクト＋Work＋Canvas」。ただしCoworkのようにPC内フォルダ全体を直接渡す方式とは少し異なる（添付・プロジェクト保存・Drive連携・Codexで進める）。

## 発言（本人）
いま、https://note.com/ritsuto2525/n/n050a50b2449c この記事のようなことをしたくて、いろんなAIで自動化できないか、何を使うか、どこに保存するかなどを探求中。リサーチしてほしい。

## 回答（AI）— リサーチ結果
記事の目的：X・AIとの会話履歴・作業フォルダ・動画資料・noteなどから情報を集め、自分を理解させる共通ファイル **my_context.md** を作る。完成ファイルをChatGPT/Claude/Gemini/Antigravityに読ませ、毎回の自己紹介を減らす設計。

### 結論（美幸さんに最も合う役割分担）
> - Obsidianを情報の正本にする
> - ChatGPTで話す・考える・整理する
> - Claude CoworkまたはAntigravityでファイルを整理・更新する
> - Gemini Notebookで大量資料を分析する
> - Makeなどの自動化は運用が固まってから追加する

AIの記憶そのものを保存場所にせず、**Markdownファイルを共通の正本**にするのが重要。

### 記事のままでは注意が必要な点
- 「全会話履歴を分析して」は文字どおり実行されるとは限らない。記憶は自動整理されるが全ては表示されない → 重要な会話は記憶任せにせず終了時に要約して外部保存。
- my_context.md 一つに全部詰めると長すぎ・古い情報や矛盾が混ざる。毎回読む指示ファイルは簡潔・具体的に、目安200行未満（Claude Code公式推奨）。

分割案：
```
01_Context/
├─ my_context.md        ← 現在の重要事項＋詳細ファイルの場所を示す短い索引
├─ profile.md
├─ values_vision.md
├─ work_business.md
├─ writing_voice.md
├─ ai_working_rules.md
└─ context_changelog.md
```

### 各AIの役割
- **ChatGPT（日々の対話と整理）**: プロジェクトにチャット/ファイル/指示/記憶をまとめる。Plusは1プロジェクト最大25ファイル。Drive/Slackリンクも追加可（常時自動同期ではない）。向く作業＝音声壁打ち/アイデア深掘り/会話終了時の要約/最新リサーチ/企画・教材整理/定期確認。Scheduled TasksもあるがローカルObsidian更新役とは分ける。
- **Claude Cowork（Obsidianのファイル作業）**: 今回の目的に最も近い。指定フォルダ内のMarkdown/Word/PDF/Excel/PowerPointを読み、作成・編集・整理を複数ステップで実行。Pro/Max/Team/Enterprise、Windows/Mac/Web/Android対応。例：「00_Inboxを確認→プロジェクト/判断ログ/発信素材/保留事項に分類。既存を勝手に変更せず更新候補と差分を先に見せて」。記事の統合プロンプト実行場所としてもCoworkが適。
- **Antigravity（仕組み作りと反復作業）**: 既に使用中なので活用。複数エージェント/ワークスペース管理、ファイル横断処理、ルール、Skills、Web制作、自動処理。使い分け→日常の文書・フォルダ整理=Cowork / Web制作・複雑な仕組み=Antigravity / コード中心=Claude Code or Antigravity IDE。
- **Gemini Notebook（大量資料の分析）**: NotebookLMの後継名。PDF/Markdown/Word/PPT/CSV/音声/Web/YouTube/Googleドキュメント等。Drive取り込み資料は数分おき同期あり。向く→音声ジャーナル横断分析/過去教材分析/文体分析/大量PDF・動画要約/共通テーマ抽出。分析場所であり保存場所にはしない。

### 自動化の設計（3段階）
- **第1段階：手動＋保存形式を統一**。会話の最後に必ず次形式でまとめてObsidian `00_Inbox/AI-Chats` に保存：
  1. 相談の目的 2. 分かったこと 3. 採用した案 4. 採用しなかった案と理由 5. 未解決 6. 次に行うこと 7. 設計判断ログ 8. 発信・教材に使える内容
- **第2段階：Cowork/Antigravityで半自動化**。週1回、受信箱を読ませて 保存先候補/既存重複/統合候補/次アクション/my_context.mdへ反映すべき安定情報 を提出。AIが更新案→人が承認して反映。
- **第3段階：Makeなどを追加**。例：Android音声保存→Driveの音声受信箱→Makeが検知→文字起こし・要約→「Obsidian取り込み待ち」→Cowork/Antigravityが分類案→確認後に正式保存。Makeは視覚型で分かりやすい。n8nは自由度高いが保守負担増、現段階では不要。

### 保存場所
- 正本は引き続き **Obsidian** 推奨。Windows/Mac/Androidで使うため同期は **Obsidian Sync** が管理しやすい（E2E暗号化可、バージョン履歴あり）。
- **GitHubは正本ではなく**、次に限定：Webサイト/プログラム、公開可能な教材、個人情報を除いたテンプレート、Obsidianの追加バックアップ。
- 顧客情報・家族情報・健康/経済情報を含むVault全体はGitHubにそのまま置かない。

### 最終構成
```
【入力】ChatGPT音声・Android録音・メモ・スクリーンショット
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

記事の考え方は良いが、美幸さんの場合は
> 「1枚の巨大なコンテキストファイルを作る」から、「小さなマスターコンテキストと、分割された第二の脳を継続的に育てる」へ
変更するのが適している。

（※ChatGPTがHTMLレポート「マスターコンテキスト＆第二の脳 自動化リサーチ」を作成。次の作業提案：蓄積情報から my_context.md 初版とObsidian用フォルダ一式を作成すること。）
