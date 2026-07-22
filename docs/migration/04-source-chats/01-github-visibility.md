# 元チャット 01: GitHubリポジトリの公開設定のヘルプ

> 原文保存（壁打ちログ）。整理・要約は上位ドキュメント（01-decisions.md ほか）を参照。

## 内容
GitHubのリポジトリの公開設定のヘルプ

## 発言（本人）
間違えてパブリックにしちゃったのってどうやって直すんだっけ?

## 回答（AI）
GitHubのリポジトリを Public（公開）→ Private（非公開） に戻す手順です。

1. 上のメニューの Settings をクリック
2. 下のほうまでスクロールして、Danger Zone を開く
3. Change repository visibility をクリック
4. Change visibility → Make private を選ぶ
5. 確認のため、リポジトリ名 `miyuk9/move` を入力して確定

このリポジトリは今ほぼ空なので、気づいた時点でPrivateにすれば大きな問題にはなりにくいです。ただし、パスワード・APIキー・個人情報を一度でもコミットしていた場合は、Privateにするだけでなく、そのキーの無効化・再発行も必要です。
