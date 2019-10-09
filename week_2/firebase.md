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

#### why Firebase..?
* NoSQL

#### データベースの型
![https://proengineer.internous.co.jp/topics/wp-content/uploads/2017/01/column_image6411_01.jpg](:storage/59478113-62d1-4bd1-8fd3-1e9fc7f0996b/9e7babcd.jpg)

図１（階層型データベース）


![https://proengineer.internous.co.jp/topics/wp-content/uploads/2017/01/column_image6411_04.jpg](:storage/59478113-62d1-4bd1-8fd3-1e9fc7f0996b/d443984a.jpg)
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

#### データベースにデータを保存
<<< .add() を利用　>>>
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

#### 値の追加。すでに追加されている場合は上書き 
<<< .set() >>>
Bodyの中のScriptに入力。
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
(注意：リロードを忘れずに。)

### 入力したものをデータベースに保存
Bodyの中に入れてください。
```Html
  <p>Keyword入力してください</p>
  <input id="key_word" type="text" value="">
  <input type="button" id="key_word_button" value="Submit" onclick="submit();">
  <input type="button" name="" value="delete cookie" onclick="delete_cookie();">
```
Bodyの中のScriptに
```Javascript
      var target = document.getElementById("key_word").value;
      
      db.collection("cities").doc(target).set({
    name: target
})
.then(function() {
    console.log("Document successfully written!");
})
.catch(function(error) {
    console.error("Error writing document: ", error);
```
これはtargetという変数に"<input></input>"で入力したものを保存。
(target＝入力した値)

そしてその値をデータベースに保存。
