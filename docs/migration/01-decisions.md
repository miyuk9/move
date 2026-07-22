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

## D-06: 「正本」は対象で使い分ける（GitHub と Obsidian の役割整理）
- **背景**: チャット03は「GitHub＝正本」、チャット09は「Obsidian＝正本」と、一見矛盾する助言があった。対象が異なるだけで両立する。
- **決定（整理）**:
  - **コード・アプリ・公開コンテンツ**（サイト/Workers/プロンプト/公開教材/テンプレート）の正本 → **GitHub**（D-02のまま）
  - **個人の知識・コンテキストVault**（profile/価値観/顧客・家族・健康・経済など機微情報を含む）の正本 → **Obsidian**（同期はObsidian Sync）
  - 個人情報を含むVault全体は **GitHubに置かない**。GitHubへは「個人情報を除いた公開可能物」と「バックアップ」のみ。
- **含意**: 「頭＝GitHub、手足＝Cloudflare、思考ノート＝Obsidian」に、「**個人知識の金庫＝Obsidian**」が加わる。
- **出典**: [08-context-os.md](08-context-os.md) / [06-architecture.md](06-architecture.md)

## D-07: 会話の締めは「8項目フォーマット」で残す
- **決定**: AIとの会話の最後に必ず 1.目的 2.分かったこと 3.採用案 4.不採用案と理由 5.未解決 6.次にやること 7.設計判断ログ 8.発信・教材に使える内容 の8項目でまとめ、Obsidian受信箱へ保存。
- **注記**: この docs/migration/ の運用（決定/要件/未解決/設計）は実質この実践版。
- **出典**: [08-context-os.md](08-context-os.md)
