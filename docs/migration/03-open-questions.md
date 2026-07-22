# 未解決の論点（Open Questions）

まだ決まっていない / 確認が必要な事項。

## Q-01: 機密情報のコミット有無の確認
- Private 化とは別に、パスワード・APIキー・個人情報を **過去に一度でもコミットしていないか** の確認が必要。
- もしあれば、該当キーの **無効化・再発行** が必須。
- 出典: [04-source-chats/01-github-visibility.md](04-source-chats/01-github-visibility.md)

## Q-02: 作業PCの搭載メモリ量の確認
- Windows11がメモリ86%で重くなっている。AIアプリを複数常駐させる使い方に対して搭載RAMが不足の可能性（4GB or 8GBの疑い）。
- 「パフォーマンス→メモリ」で搭載量を確認し、増設要否を判断する。
- **設計への含意**: 重い処理をローカルPCに背負わせず、Cloudflare（実行基盤）や外部サーバー/GitHub Actionsへ逃がす方針（→ 06-architecture.md）が、この制約とも整合する。
- 出典: [04-source-chats/04-windows11-slow.md](04-source-chats/04-windows11-slow.md)
