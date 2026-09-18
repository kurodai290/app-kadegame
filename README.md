# CYBER TCG Firebase版

Firebaseの接続設定を入れたGitHub Pages用のCYBER TCGです。

## Firebase側で完了している設定

- Firebaseプロジェクト: cyber-tcg
- Webアプリ: CYBER TCG Web
- Realtime Database
- Authentication → 匿名ログイン

## GitHubへの入れ方

このZIPの中にある

- index.html
- game.html

をGitHubリポジトリにアップロードしてください。

古い `index.html` と `game.html` がある場合は、置き換えてください。

## 対戦方法

1. プレイヤー1が「ルームを作る」
2. 6文字のルームコードが表示される
3. プレイヤー2が同じコードを入力して「対戦に参加する」
4. 2人そろうと自動で対戦開始
5. 3人目以降は同じコードで「観戦する」

## 注意

現在のRealtime Databaseルールはテスト用です。
ゲームが正常に動くことを確認した後、公開運用する場合は安全なルールへ変更してください。

## 重要

FirebaseのWeb設定にはAPIキー等が含まれますが、Webアプリ用設定のAPIキーは通常のパスワードとは異なります。
ただし、Firebaseのサービスアカウント秘密鍵や秘密鍵ファイルは公開しないでください。
