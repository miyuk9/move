# 決まったこと（Decisions）

壁打ちの中で「こうする」と決まった / 実行した事項の記録。

## D-01: リポジトリの公開範囲は Private
- **決定**: `miyuk9/move` は Private（非公開）で運用する。
- **経緯**: 誤って Public にしてしまい、Private に戻す手順を確認した（元チャット01）。
- **手順**: Settings → Danger Zone → Change repository visibility → Make private → リポジトリ名を入力して確定。
- **状態**: 対応済み想定（要確認）。
- **出典**: [04-source-chats/01-github-visibility.md](04-source-chats/01-github-visibility.md)

## D-02: 役割分担 — GitHub＝頭、Cloudflare＝手足、Obsidian＝思考ノート
- **決定**: 正本（ソース・履歴）はGitHubに置き、Cloudflareは実行基盤として使う。人間の思考・編集はObsidian。
- **含意**: 「全部Cloudflareに寄せる」は実行基盤としてはOK、ただし「全部Cloudflareに保存」はしない。
- **出典**: [06-architecture.md](06-architecture.md) / [04-source-chats/03-architecture-cloudflare.md](04-source-chats/03-architecture-cloudflare.md)

## D-03: 段階的な移行順序
- **決定**: いきなり全部移さない。①サイト公開＋毎日の自動投稿 → ②D1 → ③R2 → ④管理画面 の順。
- **理由**: 一括移行は「整理」ではなく「引っ越し作業そのものの混乱」を生む。
- **出典**: [06-architecture.md](06-architecture.md)

## D-04: 相談窓口は一つ（裏で専門家に振り分け）
- **決定**: GPTs/エージェントを並べず、相談窓口を一つにして内容に応じて裏で振り分ける。入口は「やりたいこと」ベース。
- **既存GPTs**: すぐ捨てず、外部の専門家として登録 → よく使う順に自前システムへ移管。
- **出典**: [06-architecture.md](06-architecture.md)

## D-05: 今の記憶置き場は Obsidian の「Inbox」1個
- **決定**: 設計が固まるまでは、覚えておきたいことは Obsidian の Inbox ノート1個に全部放り込む。週1で「知識/タスク/捨てる」に仕分け。確定したものだけGitHubへ移す。
- **出典**: [04-source-chats/03-architecture-cloudflare.md](04-source-chats/03-architecture-cloudflare.md)
