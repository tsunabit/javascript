# JavaScriptPractice2018

### JavaScriptでHello World
```
<script type="text/javascript">
<!--
  // document.writelnは表示された文字列を表示するための命令
  document.writeln('Hello World');
  //-->
</script>
<!-- JavaScriptを利用てできない場合 -->
<noscript>JavaScriptが利用できません</noscript>

```
!-- -->はコメント。コード全体をコメントで囲っているのは、JavaScriptに対応していないブラウザで
JavaScriptのコードがそのまま露出してしまうのを避けるため

### script>タグを記述する場所は3つ
scriptタグの記述場所は、大きく以下の3つに分類できる。  
  1. bodyタグの配下(任意の場所)
  2. bodyタグの配下(/body>の直前)
  3. headタグの配下

#### 2. の補足
一般的なブラウザではスクリプトの読み込みや実行が完了するまで、以降の描画は行わない。  
このため、読み込みや実行に時間がかかるスクリプトは、そのままページ描画の遅れに直結する。  
そこで、ページ高速化の手法としてページの末尾(</body>の直前)にscriptタグを配置することがよく行われる。
#### 3. の補足
上記2. で賄えないケース。JavaScriptでは関数を呼び出すためのscriptタグよりも、  
関数定義のscriptタグを先に記述していなければならないというツールがある。
例えば、bodyタグの配下で呼び出す必要があるような関数は、headタグの配下で事前に読み込んでおく必要がある。

### スクリプトコードの外部化
```
<script type="text/javascript" src="外部ソースファイル名" [charset="文字コード"]>
</script>
(例)
<script type="text/javascript" src="helloEx.js">
</script>
```
スクリプトコードを外部化する場合、src属性で指定されたスクリプトファイルを(.jsファイル)を読み込む。
src属性が指定されている場合、<script>タグ配下の内容は無視される。

### アンカータグにスクリプトを埋め込む　JavaScript擬似プロトコル
scriptタグで記述する他、アンカータグにスクリプトを埋め込むことも可能。  
JavaScript擬似プロトコルとは、アンカータグのhref属性に「JavaScript:〜」の形式で、　　
あたかもURLであるかのようにJavaScriptを埋め込むことも可能。
この記法をJavaScript擬似プロトコルと言う。
```
<a href="JavaScript:スクリプトコード">リンクテキスト</a>
```

### noscriptタグ JavaScript機能がオフの場合に情報を表示させる
ブラウザでは、JavaScriptの機能を自由にオフにすることができる。その場合に表示すべき  
コンテンツを表すのがnoscriptタグ。  

### 連想配列とオブジェクト
JavaScriptにおいては、連想配列とオブジェクトは同一のもの。他の言語を学んだことがあ  
る人にとっては違和感を感じる。JavaScriptでは「連想配列」と「オブジェクト」という  
言葉は、単にその時々の使い方や文脈によって使い分けられているにすぎない。  

#### ドット演算子とブラケット構文
|例|説明|
|:--|:--|
|オブジェクト名.プロパティ名|ドット演算子|
|オブジェクト名['プロパティ名']|ブラケット構文|

両者の違いを理解するために、以下のような例を考える
```
× obj.123
○ obj['123']
```
ドット演算子ではプロパティ名は識別子と見なされるため、識別子の命名規則に従っていない  
「123」のような名前は使えない。しかし、ブラケット構文ではプロパティ名はあくまでも文字列  
として指定するため、このような制限はない。  

### 関数リテラル
JavaScriptでは、関数もデータ型の一種として扱われるのが特徴。  
つまり、JavaScriptでは関数も変数のように扱うことができる。

### 未定義値(undefine)
未定義値(undefine)は、ある変数が定義されていないことを表す値。
以下のようなケースで返される。
* ある変数が宣言済みであるものの値を与えられていない
* 未定義のプロパティを参照した
実は、undefineはGlobalオブジェクトのプロパティで定義されたプロパティ。
よって通常のプロパティのように値を代入することも可能。ただし、このような使い方はしない。

### まとめ
|分類|データ型|概要|
|:--|:--|:--|
|基本型|数値型(number)|数値|
|基本型|文字列型(string)|シングルクオート/ダブルクオートで囲まれた0個以上の文字列|
|基本型|真偽型(boolean)|ture/false|
|基本型|特殊型(null/undefined)|値が未定義であることを表す|
|参照型|配列(array)|データの集合(各要素にインデックス番号でアクセス可能)|
|参照型|オブジェクト(object)|データの集合(各要素に名前でアクセス可能)|
|参照型|関数(function)|一連の処理(手続き)の集合|


### 等価演算(==)と同値演算(===)
同値演算(===)は変数の型も含めて比較する。変数の型も一致して初めてtureと判定される。  
不等価演算し(!=)と非同値演算し(!==)でも同様の関係。

### with命令
同じオブジェクトを繰り返し呼び出す場合、以下のようにwith命令を利用するとオブジェクト名を省略でき、コードがシンプルになる。ただし、with命令は便利な反面、「ブロック内の処理速度が低下する」「そもそもコードが読みにくくなる(withによって修飾されるメソッドが曖昧になりやすい)」などの問題がある。そのため、実際のアプリケーションでは利用すべきではありません。
```
with(document) {
    writeln(Math.abs(-15));
    writeln(Math.max(10, 15));
    writeln(Math.min(-10, 0));
}
```

### Arrayオブジェクト
Arrayオブジェクトは、配列型の値を扱うためのオブジェクトで、配列に対する要素の追加削除、結合、並べ替えを行うための昨日を提供する。
Arrayオブジェクトはリテラル表現を使って、
```
var ary = ['佐藤','鈴木','山田']
```
のように生成することもできますが、コンストラクタ経由で、次のように生成することもできる。コンストラクタ経由で次のように生成することもできる。
```
var ary = new Array('佐藤','鈴木','山田'); //指定要素で配列を生成
var ary = new Array(); //空の配列を生成
var ary = new Array(10); //指定サイズで空の配列を生成
```
ただし、コンストラクタを利用した構文は、意味的に曖昧になりやすい問題がある。  
例えば、
```
var ary = new Array(10);
```
は、「長さが10の配列」でしょうか、それとも「10という要素を持つ配列」でしょうか。いずれの意図であろうと、JavaScriptは前者として認識します。  
また、
```
var ary = new Array(-10);
```
は、「-10を要素として持つ」ことを意図したコードですが、JavaScriptは「-10の長さを持つ配列」を生成しようとして、結果、エラーとなります。
以上のような理由から、配列を生成するには最大限、配列リテラルを利用する。空の配列を生成するには、以下のように記述する。
```
var ary = [];
```

### 匿名オブジェクト(無名オブジェクト)
Objectオブジェクトの役割は、その他のオブジェクトに対して共通機能を提供することばかりではない。Objectオブジェクトを直接インスタンス化することで、ユーザーが自前のオブジェクトを定義するのに利用することもできます。
```
var obj = new Object();
```
このようなオブジェクトのことを「独自のオブジェクト名を持たない」という意味で匿名オブジェクトもしくは無名オブジェクトと呼ぶ。匿名オブジェクトは、作成した直後は、オブジェクト共通のプロパティ/メソッドの他はなんらのデータを持たない、言うなれば、からの器。この空っぽの器に対して、データ(つまり、プロパティ)を追加するには、以下のように記述するだけ。
```
obj.name  = 'ドクジロウ'
obj.birth = new Date(2005, 7, 15);
obj.old   = 5;
```
このように定義したプロパティは、通常のプロパティと同様、ドット演算子でアクセスすることができる。
```
document.writeln(obj.name);
```
匿名オブジェクトを利用すれば、その場限りしか使わず、再利用することのないようなちょっとした構造データを受け渡しする場合にも、いちいち記述するような「クラス」を定義する必要がありませんので、コードをシンプルに記述することができる(例えば、「関数で複数の値を返したい」などという場合は配列や匿名オブジェクトを利用すると便利)。  
なお、プロパティだけではなくメソッドを定義することもできる。ただし、一時的なデータの受け渡し目的で利用することが多い匿名オブジェクトで、メソッドを指定する機会はあまり多くないはず。  
また、匿名オブジェクトを生成するために、Objectオブジェクトではなく、以下のようにArray/Dateのような既存の組み込みオブジェクトを利用することもできる。
```
var obj = new Array();
obj.name = 'トクジロウ';
```
しかし、匿名オブジェクトを生成するために、これらの特定の目的を持ったオブジェクトをベースにする理由はない。かえって間違いやバグの元となる可能性がある。通常は、オブジェクトとして中性的な機能のみを持つObjectオブジェクトを使うべきです。

### Globalオブジェクト
parseInt()とか、encodeURI()とか、eval()とか。。。

# 関数
### 関数を定義する3つの方法
 1. function命令で定義する
 2. Functionコンストラクタ経由で定義する
 3. 関数リテラル表現で定義する

#### 1. function命令で定義する
関数を定義する場合の最も基本的なアプローチ
```
関数定義 function.js
function triangle(base, height) {
	return base * height / 2;
}

HTML実装
<head>
<meta charset="UTF-8">
<title>Hello world</title>
<script type="text/javascript" src="function.js">
</script>
</head>
...
<script type="text/javascript">
  document.writeln('三角形の面積(関数)' + triangle(5, 2));
</script>

```

#### 2. Functionコンストラクタ経由で定義する
JavaScriptは組み込みオブジェクトとしてFunctionオブジェクトを用意している。  
関数は、このFunctionオブジェクトのコンストラクタを利用して定義することも可能。  
ただし、特別な理由がない限り、あえてFunctionコンストラクタを利用するメリットはない。  
```
HTML内での実装
<script tyep="text/javascript">
  var triangle2 = new Function('base, height', 'return base * height / 2;');
  document.writeln('三角形の面積(Functionコンストラクタ)' + triangle2(5, 2));
</script>
```
しかし、1点だけFunctionコンストラクタには、function命令にはない重要な特徴がある。  
それは「Functionコンストラクタでは、引数や関数本体を文字列として定義できる」という点。  
```
HTML内での実装
<script tyep="text/javascript">
  var param = 'base, height';
  var formula = 'return base * height / 2;';
  var triangle = new Function(param, formula);
  document.writeln('三角形の面積(Functionコンストラクタ)' + triangle(5, 2));
</script>
```

#### 3. 関数リテラル表現で定義する
JavaScriptにおいて、関数はデータ型の一種。つまり、  
関数を変数に代入したり、ある関数の引数として渡したり、あるいは、戻り値として関数を返すことすら可能  
です。  
これによって、JavaScriptではじつに柔軟なコーディングが可能になる。
```
<script type="text/javascript">
  var triangle = function(base, height) {
    return base * height / 2;
    };
  document.writeln('三角形の面積(関数リテラル)' + triangle(5, 2));
</script>
```

#### 関数リテラルとfunction命令の違い
 - function命令 → 関数を直接定義している
 - 関数リテラル  → 「function(引数, 引数){...}」と名前のない関数を定義した上で、変数に格納している

#### 変数宣言にvar命令は必須
var命令を使わずに宣言された変数は全てグローバル変数とみなす
```
<script type="text/javascript">
	scope = 'Global';
	function getValue() {
	scope = 'Local';
	return scope;
	}
	document.writeln(getValue());	// Localを出力
	document.writeln(scope);	// Localを出力
</script>
```

#### ブロックレベルのスコープは存在しない
JavaやC言語などでは存在するブロックレベルのスコープは存在しない
```
// Java
if(true) {
	int i = 5;
}
System.out.println(i);	// エラー

// JavaScript
if(true) {
	int i = 5;
}
document.writeln(i);	// 5を出力
```

#### 関数リテラル/Functionコンストラクタにおけるスコープの違い
関数リテラルとFunctionコンストラクタは、いずれも匿名関するを定義するための機能を提供する。  
実は関数の中でこれらを利用した場合、スコープの解釈が異なる。
```
var scope = 'Global';

function checkScope() {
	var scope = 'Local';
	
	// 関数リテラル
	var f_lit = function() { return scope; };
	document.writeln(f_lit);	// Local
	
	// Functionコンストラクタ
	var f_con = new Function('return scope');
	document.writeln(f_con);	// Global
}
checkScope();
```

#### JavaScriptは引数をチェックしない
引数の数が、関数側で要求する数と異なる場合もこれをチェックしない  
以下の①~③の例は全て正常に終了する。
```
    <script type="text/javascript">
        function showMessage(value) {
            document.writeln(value);
        }
    </script>
<br>
    <script type="text/javascript">
        showMessage();			  // ①undefined
        showMessage('山田');		 // ②山田
        showMessage('山田', '鈴木');	// ③山田
    </script>
```
  
実際に与えられた引数の数と要求する引数の数を比較し、異なる場合にはエラーを返すという処理も実装可能。
```
    <script type="text/javascript">
        function showMessage(value) {
            if(arguments.length != 1 ) {
                throw new Error('引数の数が間違っています：' + arguments.length);
            }
            document.writeln(value);
        }
    </script>

<br>

    <script type="text/javascript">
        try {
            showMessage('山田' , '鈴木');
        } catch(e) {
            window.alert(e.message);
        }
    </script>
```

引数の数をチェックしないということは、JavaScriptでは全ての引数は省略可能であるということです。  
ただし多くのケースでは、引数がただ省略されただけでは、正しく動作しないことがほとんどです。  
そこで以下のように引数のデフォルト値を設定しておく必要があります。  
```
    <script type="text/javascript">
        function triangle(base, heigh) {
            if(base == undefined) {
                base = 1;
            }
            if(heigh == undefined) {
                heigh = 1;
            }
            return base * heigh / 2;
        }
    </script>

<br>

    <script type="text/javascript">
        document.writeln(triangle(5));  // 2.5
    </script>
```

---

### JavaScript Tips
コード全体をコメント構文で囲っているのは、JavaScriptに対応していない  
ブラウザでJavaScriptのコードがそのまま露出してしまうのを避けるため。  
古くからのお作法的な記述。現在はJavaScriptに対応していないブラウザは  
少なくなっておりコメントアウトは必ずしも必須ではない。

```
<script type="text/javascript">
<!--
// document.writelnは表示された文字列を表示するための命令
document.writeln('Hello World');
//-->
</script>
```

---

# テンプレート
|コマンド|説明|
|:--|:--|
|||
|||
|||
|||
|||

---

### 参考書
JavaScript本格入門 ～モダンスタイルによる基礎から現場での応用まで　　
https://www.amazon.co.jp/%E6%94%B9%E8%A8%82%E6%96%B0%E7%89%88JavaScript%E6%9C%AC%E6%A0%BC%E5%85%A5%E9%96%80-%EF%BD%9E%E3%83%A2%E3%83%80%E3%83%B3%E3%82%B9%E3%82%BF%E3%82%A4%E3%83%AB%E3%81%AB%E3%82%88%E3%82%8B%E5%9F%BA%E7%A4%8E%E3%81%8B%E3%82%89%E7%8F%BE%E5%A0%B4%E3%81%A7%E3%81%AE%E5%BF%9C%E7%94%A8%E3%81%BE%E3%81%A7-%E5%B1%B1%E7%94%B0-%E7%A5%A5%E5%AF%9B-ebook/dp/B01LYO6C1N?SubscriptionId=AKIAIXNEYMK6UFDZYSVQ&tag=tachbookrank-22&linkCode=xm2&camp=2025&creative=165953&creativeASIN=B01LYO6C1N
