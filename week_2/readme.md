## 第二回　Firebase入門

##### 目的:
* データベースについて初歩的な知識の蓄える
* Firebaseにデータを保存
* htmlの入力スペースからデータベースに保存
(注意：第二回の講座は第一回が完了していることを前提に進みます。)

### データベースとは...?
Wikipediaによると、"データベース（英: database, DB）とは、検索や蓄積が容易にできるよう整理された情報の集まり。 通常はコンピュータによって実現されたものを指すが、紙の住所録などをデータベースと呼ぶ場合もある。 狭義には、データベース管理システム (Database Management System, DBMS) またはそれが扱う対象のことをいう。"

つまり、、、

それはたくさんの「データ」を集めて、後で使いやすい形に整理した情報のかたまり。(e.g. 電話帳・辞書・WINEの本）



（要件定義書データ項目一覧）
https://www.mhlw.go.jp/sinsei/chotatu/chotatu/shiyousho-an/dl/181025-1-05_01-1.pdf

#### Why Firebase..?
* NoSQL

#### データベースの型
<img src="https://proengineer.internous.co.jp/topics/wp-content/uploads/2017/01/column_image6411_01.jpg"  title="サンプル">


図１（階層型データベース）

<img src="https://proengineer.internous.co.jp/topics/wp-content/uploads/2017/01/column_image6411_04.jpg"  title="サンプル">

図２（データの例）

データ
```Javascript
key1 : value1
```

ドキュメント
```Javascript
key1 : value1
key2 : value2
key3 : value3
```

コレクション
```Javascript
users: {
  userdocument1
  userdocument2
  userdocument3
}
```

<データ型の例>
* 配列	
* ブール値
* バイト	
* 日時	
*  浮動小数点	
* 座標	
* 整数	
* Null	
* 文字列

## データベースにデータを保存
まず前回追加したCSS といらない必要でないHTMLは削除してください。
![Screen Shot 2019-10-09 at 13.17.33](file:///Users/natsukikataoka/Desktop/Screen%20Shot%202019-10-09%20at%2013.17.33.png)



bodyの一番上に以下を入力。
```
<script>

</script>
```
このscript tagの中にこれからはJavascriptを入力してデータベースを扱っていきます。


## 一意のIDをつけて保存
 .add() を利用　
Bodyの中のScriptに入力

```Javascript
db.collection("cities").add({
    name: "Tokyo",
    country: "Japan"
})
.then(function(docRef) {
    console.log("Document written with ID: ", docRef.id);
})
.catch(function(error) {
    console.error("Error adding document: ", error);
});
```
リロードした後に　Firebase/Console/Databaseから確認してみましょう。

## 値の追加。すでに追加されている場合は上書き 
<<< .set() >>>
```
    var db = firebase.firestore();

```

先ほど入力したScriptタグの中身を削除。
そしてBodyの中のScriptに入力。
```Javascript
db.collection("cities").doc("LA").set({
    name: "Los Angeles",
    state: "CA",
    country: "USA"
})
.then(function() {
    console.log("Document successfully written!");
})
.catch(function(error) {
    console.error("Error writing document: ", error);
});
```
自分のサイトにいき、ページのリロードした後に　Firebase/Console/Databaseから確認してみましょう。

### 入力したものをデータベースに保存
Bodyの中に入れてください。（Script tag ではありません）
```Html
  <p>Keyword入力してください</p>
  <input id="key_word" type="text" value="">
  <input type="button" id="key_word_button" value="Submit" onclick="submit();">
 <input type="button" id="key_button" value="Submit" onclick="show_me();">

```
Bodyの中のScriptに
```Javascript
function submit() {
      var target = document.getElementById("key_word").value;
      db.collection("NEW").doc(target).set({
    name: target
})
.then(function() {
    console.log("Document successfully written!");
})
.catch(function(error) {
    console.error("Error writing document: ", error);
}
```




これはtargetという変数に"<input></input>"で入力したものを保存。
(target＝入力した値)

そしてその値をデータベースに保存。
