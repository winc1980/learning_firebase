## 第一回　Firebase入門
メールで送った通り、nodejs と エディターはインストール済みを想定しています。

##### Firebaseとは？
Firebaseとは、Googleが提供している、世界で圧倒的に省エネで最も手軽に高品質のウェブ
アプリやモバイルアプリなどを開発することができるプラットフォームです。


### 目的
ネットに自分のウェブアプリ開発する。そのアプリをデプロイして実際に使ってみる。

## 進め方

#### ・デプロイする
#### ・Public / index.htmlを編集する

##  デプロイの仕方
Firebase にアクセス(https://firebase.google.com)

右上のボタンからログインしてコンソールに移動

プロジェクトを追加

アプリの名前を入力。

Google Analytics をオフにする。

コンソールのウェブアプリを追加するを押す。

ニックネームを入力

FirebaseHostingを許可する。

自分のパソコンのデスクトップに「firebase_app_1」というフォルダを作成

コマンドプロンプト・ターミナルを開いて以下を入力

```
cd 
```
```
cd Desktop
```
```
cd firebase_app_1
```
```
npm install -g firebase-tools
```

```
firebase login
```

```
Allow Firebase to collect CLI usage and error reporting information? (Y/n) Y
```

```
firebase init
```


<img width="1393" alt="Screen Shot 2019-10-09 at 13 11 55" src="https://user-images.githubusercontent.com/48721079/66452155-614fe580-ea9a-11e9-93d2-157f823fb3ec.png">

```
Use an existing project
```

```
自分のプロジェクト名
```

```
? What do you want to use as your public directory? Public
```

```
? Configure as a single-page app (rewrite all urls to /index.html)? (y/N) y
```

```Javascript
Firebase deploy
```

で書いてあるリンクに行ってみる。もしdeploy されていれば成功。

## 編集
以下を自分の作ったフォルダの　public / index.htmlのBodyスクリプトの中の一番下に入力。これらをScriptタグと呼ぶ。

```html
<h1>hello world</h1>

<!-- The core Firebase JS SDK is always required and must be listed first -->
<script src="/__/firebase/7.0.0/firebase-app.js"></script>
<!-- TODO: Add SDKs for Firebase products that you want to use
https://firebase.google.com/docs/web/setup#available-libraries -->
<!-- Initialize Firebase -->
<script src="/__/firebase/init.js"></script>
<!-- The core Firebase JS SDK is always required and must be listed first -->
<script src="https://www.gstatic.com/firebasejs/7.0.0/firebase-app.js"></script>
<!-- TODO: Add SDKs for Firebase products that you want to use
https://firebase.google.com/docs/web/setup#available-libraries -->
```
Firebaseのコンソールに戻り、設定からプロジェクト設定　→  一番下のCDNをクリック　→ コピーして同じくpublic / index.html にペースト

<img width="690" alt="Screen Shot 2019-10-09 at 13 17 33" src="https://user-images.githubusercontent.com/48721079/66452198-8e9c9380-ea9a-11e9-862b-0f8081801bda.png">


terminal/command prompt で以下のコマンドを入力

```
firebase deploy
```
そこでリンク先に行き、「Hello」と出ていれば成功。

## HTML と　CSS
Body の Script タグより上のコードを全て削除。

Body の中にGithubのweek_1フォルダにあるindex.htmlをコピー

さっき削除したコードの代わりに貼り付ける。


terminal/command prompt で以下のコマンドを入力

```
firebase deploy
```

