# CYBER TCG v2

今回の修正版は「ルームコード」「対戦開始」「観戦」「チャット」を分かりやすくしました。

## まず重要

GitHub Pagesだけでは、別のスマホ・PC同士のリアルタイム対戦はできません。
このゲームではFirebase Realtime Databaseを使います。

## ファイル

- index.html
- game.html
- README.md

## Firebase設定

index.html と game.html の両方にある `firebaseConfig` を、自分のFirebaseプロジェクトの設定に置き換えます。

Firebase Consoleで、

1. プロジェクトを作成
2. Webアプリを追加
3. 表示されたfirebaseConfigをコピー
4. Authentication → Sign-in method → Anonymous を有効化
5. Realtime Databaseを作成
6. index.html と game.html の `firebaseConfig` に貼り付け

を行ってください。

## 対戦方法

### プレイヤーA

「ルームを作る」を押します。

すると、

ROOM CODE: ABC123

のような6文字のコードが表示されます。

このコードをプレイヤーBへ伝えます。

### プレイヤーB

自分の名前を入力して、同じコードを入力します。

「対戦に参加する」を押します。

2人目が入った瞬間に対戦開始です。

### 観戦者

3人目以降は同じコードを入力して「観戦する」を押します。

観戦者は、

- 両プレイヤーのHP
- Energy
- スコア
- 場に出ているカード
- バトルログ
- チャット

を見られます。

観戦者はカードを出したり攻撃したりできません。

## チャット

画面下の「チャット」に文章を入力して「送信」を押します。
Enterキーでも送信できます。

チャットはFirebaseに保存されるため、同じルームにいる人全員に表示されます。

## カード

現在は5種類です。

打打だいず：ATK4、攻撃時追加1ダメージ
Laur：ATK3、攻撃時に自分のHPを1回復
TJ.hangneil：ATK6、攻撃時追加2ダメージ
sasakure.UK：ATK2、次の攻撃を強化
t+pazolite：ATK5、相手のEnergyを1減らす

## GitHub Pages

この3ファイルをGitHubリポジトリのルートにアップロードしてGitHub Pagesを有効にしてください。

注意：
`YOUR_API_KEY` などを残したままではFirebaseに接続できません。
