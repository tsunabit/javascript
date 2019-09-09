# JSpractice
<!-- JavaScript practice -->

## JQueryのメモ  

### セレクタ
$(セレクタ).html(内容);  
$(セレクタ).css(プロパティ , 値);  
$(セレクタ).bind(イベント , 処理);  
$(セレクタ).attr(対象属性 , 内容);  
複数のセレクタを指定   
$(セレクタ , セレクタ).xxx();  


### JQueryで使えるセレクタ 
|セレクタ|説明|
|:--|:--|
|*|すべての要素|
|aaa|要素名による指定　例)p|
|#aaa|ID属性による指定　例)#content|
|.aaa|class属性による指定　例).toolBox|
|this|イベントが発生した要素そのものを取り出す　(例)this|
  
 ### イベント
 |イベント|説明|
 |:--|:--|
 |focus|フォーカスが当たったとき|
 |blur|他のコントロールにフォーカスが移ったとき|
 |click|クリックされたとき|
 |keydown,keyup,keypress|キーボードを操作したとき|


 ### 要素の選択
```
 <div id="grandparent">祖父
   <div id="parent">父
     <div id="sibling1">兄</div>
     <div id="sibling2">姉</div>
     <div id="target">わたし
       <div id="children1">息子</div>
       <div id="children2">娘</div>
     </div>
     <div id="sibling3">弟</div>
     <div id="sibling4">妹</div>
   </div>
 </div>
```
- children() ... 各要素内全ての「子」要素を選択  
- parent() ... 各要素内全ての「親」要素を選択  
- siblings() ... 各要素内全ての「兄弟」要素 を選択  
- next() ... 1つ次に来る「兄弟」要素を選択  
- prev() ... 1つ前に来る「兄弟」要素を選択  

```
ex)
$(function(){
    $("target").next().children().css("color","blue") ;
)}
```
  
### ブラウザの高さ/幅を取得する
$(window).width()  
$(window).height()

### メソッドチェーン   
セレクタが同じ場合は、以下のようにメソッドをつなげて記述する。   
```
$(セレクタ)
.メソッド1()
.メソッド2()

//findとendでより高度なメソッドチェーン
$(セレクタ)
find('img').attr().end
.メソッド2()
```

### アニメーション
「animate」メソッドをメソッドチェーンでつなげると、jQueryは同時にこれを処理することなく、
順番に処理する。これを「アニメーションキュー」と呼ぶ。
  
アニメーションキューを停止させるメソッド  
```
$(this).stop.(true , false);
$(セレクタ).stop.(キューをクリア , 最後のコマに移動);
```

---
よくわかる  
JavaScriptの教科書  
amazon  
https://www.amazon.co.jp/%E3%82%88%E3%81%8F%E3%82%8F%E3%81%8B%E3%82%8BJavaScript%E3%81%AE%E6%95%99%E7%A7%91%E6%9B%B8-%E3%81%9F%E3%81%AB%E3%81%90%E3%81%A1-%E3%81%BE%E3%81%93%E3%81%A8/dp/4839941874


