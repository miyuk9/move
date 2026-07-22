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

## Q-03: 個人情報を含むVaultの正本と同期方式の最終確定
- D-06で「個人知識Vaultの正本はObsidian、GitHubには機微情報を置かない」と整理したが、実際の同期・バックアップ手段を確定する必要がある。
- 検討点:
  - Obsidian Sync（有料・E2E暗号化）を採用するか、OneDrive/Drive同期で済ませるか。
  - 「公開してよい部分」と「機微情報」をVault内でどう物理的に分けるか（別Vault or フォルダ分離）。
  - Cowork/Claude Codeに読ませてよい範囲の線引き。
- 出典: [08-context-os.md](08-context-os.md)

## Q-04: 「my_context.md 初版」と 01_Context/ 一式をいつ・どこで作るか
- リサーチの次アクションは「蓄積情報から my_context.md 初版とObsidianフォルダ一式を作成」。
- この壁打ち回収（docs/migration/）がその材料集めになっている。回収が一段落したら初版作成へ進む。
- 出典: [08-context-os.md](08-context-os.md)

## Q-05: 各AI・IDEの役割の最終確定（Cowork / Antigravity / Codex / Claude Code）
- チャット09（Cowork中心）と、Driveメモ「Windows作業手順」（Claude Code＋Codex＋Antigravityをスキル同期）で、登場ツールが多い。日常整理はCowork、仕組み作りはAntigravity、コードはClaude Code/Codex…と役割は概ね出ているが、実運用での住み分けを固める必要あり。
- 出典: [08-context-os.md](08-context-os.md) / Driveメモ「20260719_AIスキル共有_Windows作業手順.md」
