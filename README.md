# CYBER TCG GitHub版（対戦＋観戦）

この版では、元の「ルームIDだけをURLに付ける」方式から、Firebase Realtime Databaseを使う方式に変更しています。

## 追加したもの

- 第3者の観戦モード
- 2人が同じルームでリアルタイムに状態共有
- 相手の場のカード表示
- カードを場に出す
- Energy（コスト）
- 攻撃
- HP
- ターン制
- スコア
- 5枚のカードにそれぞれ効果
- ターン終了
- チャット
- GitHub Pagesで公開可能

## 重要：Firebaseの設定

GitHub Pagesだけでは、別のPC・スマホ間で対戦データを保存・共有するサーバー機能がありません。
そのためFirebase Realtime Databaseを使用します。Firebaseは無料枠がありますが、利用量によって条件が変わるのでFirebase側の最新料金・利用条件を確認してください。

### 1. Firebaseプロジェクトを作る

Firebase Consoleで新しいプロジェクトを作成します。

### 2. Webアプリを追加

プロジェクト設定からWebアプリを追加し、表示されたfirebaseConfigをコピーします。

### 3. Authentication

Authentication → Sign-in method → Anonymous（匿名）を有効にします。

### 4. Realtime Database

Realtime Databaseを作成します。

テスト中は、まずデータベースを作成して動作確認してください。
公開運用するときは、必ずFirebase AuthenticationとRealtime Databaseのセキュリティルールを設定してください。

### 5. 2つのHTMLのfirebaseConfigを書き換える

`index.html` と `game.html` の中にある

    const firebaseConfig={
      apiKey:"YOUR_API_KEY",
      ...
    };

を自分のFirebaseプロジェクトの値に置き換えます。

### 6. GitHubへアップロード

リポジトリのルートに

- index.html
- game.html
- README.md

を置きます。

GitHub Pagesを有効にすると、

    https://ユーザー名.github.io/リポジトリ名/

でロビーが開きます。

## 使い方

1. Aさんが「新しく対戦ルームを作る」
2. 表示されたROOM-xxxxをBさんに伝える
3. BさんがルームIDを入力して「対戦に参加する」
4. Cさん以降は同じルームIDを入力して「観戦する」
5. A/Bはカードを出して攻撃
6. 観戦者はゲーム状態とチャットをリアルタイムで見られます

## 注意

元のコードは、URLにルームIDを付けて画面を移動しているだけで、実際には別端末間でゲーム状態を同期していませんでした。
今回の版ではFirebaseを介して同期しています。
