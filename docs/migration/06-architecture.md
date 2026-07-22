# 全体アーキテクチャ（Target Architecture）

「AIエージェントの作業場所」を統合するための、引っ越し・再構築の目標設計。
出典: [04-source-chats/03-architecture-cloudflare.md](04-source-chats/03-architecture-cloudflare.md)

## 基本方針（役割分担）
> **GitHubを頭、Cloudflareを神経と手足、Obsidianを思考ノートにする。**

```
Obsidian / Claude Code   … 人間が考える・編集する / AIが実装する
        ↓
 GitHub ＝ 正本（設計図と履歴の保存場所）
        ↓ 自動デプロイ
 Cloudflare ＝ 実行場所（サイト公開・API・定時処理・配信・外部AI呼び出し）
```

- **全部をCloudflareに「寄せる」のはアリ。全部をCloudflareに「保存」する発想は違う。**
- 正本（ソース・履歴）はGitHub。Cloudflareはあくまで実行基盤。

## リポジトリ構成（目標）
```
GitHub
├─ apps/
│  ├─ web/             公開サイト
│  └─ cockpit/         AIエージェント管理画面
├─ workers/
│  ├─ api/             API
│  ├─ scheduler/       毎日の自動実行
│  └─ webhook/         SNSや外部サービス連携
├─ packages/
│  ├─ agents/          エージェントの定義
│  ├─ prompts/         プロンプト
│  └─ ui/              共通UI
├─ content/            記事・投稿・Markdown
├─ migrations/         DB変更履歴
└─ docs/               設計や運用ルール
```
- Claude CodeにこのGitHubリポジトリを触らせる。GitHubに変更が入ったらCloudflareへ自動デプロイ。
- APIトークンはリポジトリに置かず **Secrets** で管理。

## Cloudflare内の役割分担
| やりたいこと | Cloudflareのサービス |
|---|---|
| サイト・管理画面 | Workers ＋ Static Assets |
| AIアプリのAPI | Workers |
| ユーザー・投稿・タスク等の構造化データ | D1 |
| 画像・動画・音声 | R2 |
| 設定値・キャッシュ | KV |
| エージェント状態・リアルタイム処理 | Durable Objects |
| 毎日の定時実行 | Cron Triggers |
| 長めの複数工程 | Workflows |
| 投稿・画像生成の待ち行列 | Queues |
| OpenAI/Anthropic呼び出し管理 | AI Gateway |
| 独自ドメイン・DNS・SSL | Cloudflare |
| 受信メールの転送・AI処理 | Email Routing / Email Service |

### 自動投稿の流れ
- 単純な時間起動 → Cron Triggers
- 複数工程（画像生成→文章生成→承認→SNS投稿）→ Cron から Workflow を起動し、投稿は Queue へ流す（失敗時の再試行・遅延も Queues）

## 独自ドメインのメール（分離設計）
- 個人が読むメール → Gmail / Fastmail など
- AIへの受信窓口・通知メール → Cloudflare（Email Routing）
- 大量のメルマガ配信 → 専用配信サービス
- 補足: Email Service での送信は Workers Paid プランが必要（月3,000通まで）

## 管理画面（コックピット）のUI
巨大画面にしない。中心を6画面に絞る。**チャット中心ではなく「作業台」**（実行状況・承認待ちが最初に見える）。
```
今日     │ 今日動くエージェント / 承認待ち / エラー
実行履歴 │ 何をしたか / 入出力 / 使用モデル・コスト
タスク   │ 待機中 / 実行中 / 完了
知識     │ Obsidian由来の文書 / 検索 / エージェント別の参照範囲
素材     │ 画像 / 動画 / 投稿データ
設定     │ SNS / AIモデル / ドメイン / スケジュール
```

## 相談窓口（GPTs/エージェントの束ね方）
- 相談窓口は **一つ**。内容に応じて裏で専門家（調査役／技術相談／事業戦略／文章化）へ振り分ける。
- 「どのGPTに聞くか」を毎回人間が選ばない。
- 入口はやりたいことベース：`[相談したい][調べたい][比較したい][戦略を作りたい][成果物を作りたい]`
- 既存GPTsはすぐ捨てない。まず管理画面に外部の専門家として登録 → よく使う順にプロンプト・知識・検索を自前システムへ移す。

```
相談窓口 → 技術調査 → 設計相談 → 戦略 → 成果物（構成図 / 方針書 / タスク）
```

## Cloudflareに載せない部分
動画の重い変換、長時間のPython処理、特殊なDocker環境、ローカルPC操作 → 無理にWorkersへ移さない。
Cloudflareを司令塔にして、外部サーバーや GitHub Actions へ仕事を投げる。

## 移行順序（段階的に）
1. **サイト公開 ＋ 毎日の自動投稿**（最初の一本）
2. D1（データベース）
3. R2（画像・動画）
4. 管理画面（コックピット）

> いきなり全部引っ越すと、整理ではなく引っ越し作業そのものが新しい混乱になる。
