# 要件（Requirements）

プロジェクトに求める要件・制約の記録。壁打ちログから抽出して追記していく。

## R-01: ローカルPCに重い処理を集中させない
- 作業PCは Windows11 で、AIアプリ複数常駐によりメモリ逼迫（86%）。搭載RAMが少ない可能性（要確認 Q-02）。
- **要件**: 重い処理（動画変換・長時間処理・常駐AI）はローカルに背負わせず、Cloudflareや外部サーバー/GitHub Actionsへ逃がす設計にする。
- 出典: [04-source-chats/04-windows11-slow.md](04-source-chats/04-windows11-slow.md) / [06-architecture.md](06-architecture.md)
