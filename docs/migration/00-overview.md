# move プロジェクト — 引っ越し・再構築 概要

このディレクトリは、他のチャットで行ってきた壁打ちの内容を集約し、
`move` プロジェクトの引っ越し・再構築を進めるための作業メモ置き場です。

## ゴール（暫定）
- これまで散らばっていた議論・メモを一箇所に集約する
- 集約した内容をもとに、プロジェクトの引っ越し / 再構築の方針を固める
- ※ ゴールの詳細は壁打ちログを集めながら追記していく

## ディレクトリ構成
```
docs/migration/
  00-overview.md        ← 全体像・ゴール（このファイル）
  01-decisions.md       ← 決まったこと
  02-requirements.md    ← 要件
  03-open-questions.md  ← 未解決の論点
  04-source-chats/      ← 元チャットの生ログ（原文保存）
  05-business-context.md ← 事業の方向性・背景
  06-architecture.md     ← 全体アーキテクチャ（目標設計）
  07-gpts-inventory.md   ← GPTs棚卸し台帳（実行用）
```

## 集めた元チャット一覧
| # | 内容 | ファイル |
|---|------|----------|
| 01 | GitHubリポジトリの公開設定のヘルプ | [04-source-chats/01-github-visibility.md](04-source-chats/01-github-visibility.md) |
| 02 | ポスト投稿の内容相談（イケハヤさん引用） | [04-source-chats/02-post-draft-ikehaya.md](04-source-chats/02-post-draft-ikehaya.md) |
| 03 | AIエージェント作業場所の全体設計（Cloudflare移行） | [04-source-chats/03-architecture-cloudflare.md](04-source-chats/03-architecture-cloudflare.md) |
| 04 | Windows11の動きが重たい（メモリ） | [04-source-chats/04-windows11-slow.md](04-source-chats/04-windows11-slow.md) |
| 05 | 「WORKのクラウド」ってどういう意味？ | [04-source-chats/05-work-cloud-meaning.md](04-source-chats/05-work-cloud-meaning.md) |
| 06 | LINE返信（一回きりの連絡文） | [04-source-chats/06-line-reply.md](04-source-chats/06-line-reply.md) |
| 07 | 使ったGPTs/ブックマークのGPTsを一覧にするには？ | [04-source-chats/07-gpts-inventory-howto.md](04-source-chats/07-gpts-inventory-howto.md) |
