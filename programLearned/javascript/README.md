### 目錄:
<a name="top"></a>

|名稱|資源連結|
| :--- | :--- |
|javascript|https://www.fooish.com/javascript/function.html |
|javascript|https://www.w3schools.com/js/js_examples.asp|
|ECMAScript|http://es6.ruanyifeng.com/#docs/destructuring|

|基礎區(javascript:ECMAScript 5)|
| :--- |
|[使用javascript的方式(寫入或嵌入)](#a1)|
|<a href="#a2">宣告基本類型(string,number,object,array,variable)與function注意事項</a>|
|<a href="#a3">this解說</a>|
|<a href="#a4">取得類型名稱</a>|
|<a href="#a5">改變css樣式</a>|
|<a href="#a6">輸出的文字的各個方式(alert,console,document)</a>|
|<a href="#a7"> ++ 與 - - 注意事項</a>|
|<a href="#a8">string常用屬性</a>|
|<a href="#a9">Math常用屬性</a>|
|<a href="#a10">Date常用屬性</a>|
|<a href="#a11">Array常用屬性</a>|
|<a href="#a11-2">Array-list用法</a>|
|<a href="#a12">常用的幾種迴圈與敘述(if.else if.else.break.continue,switch)</a>|
|<a href="#a13">try catch用法</a>|
|<a href="#a14">Iterator用法</a>|
|<a href="#a15">function閉包用法</a>|
|<a href="#a16">function caLLback .call() .apply()用法</a>|
|<a href="#a17">convert the js object to JSON</a>|
|<a href="#a18">Check string matches a regex in JS</a>|
|<a href="#a19">IIFE用法:即刻執行函數(immediately invoked function expression)</a>|
|<a href="#a20">雙重function()使用與變數的優先序</a>|
|<a href="#a21">canvas畫圖(神奇寶貝球)</a>|

|ECMAScript 6(javascript 新版本)|
| :--- |
|<a href="#a0601">let,const變數語法</a>|
|<a href="#a0602">變數解構賦值(set)</a>|
|<a href="#a0610">yeild與Generator迭代</a>|
|<a href="#a0611">promise的使用</a>|

|應用知識|
| :--- |
|<a href="#c1">取得目前的row數</a>|
|<a href="#c2">得到select的 value</a>|
|<a href="#c3">javascript = = 與 = = = 的差別:</a>|
|<a href="#c4">鍵盤按鍵觸發</a>|
|<a href="#c5">输出每个 li 元素的文本</a>|
|<a href="#c6">抓取name=cancelBox的每一個input輸入框</a> |
|<a href="#c7">將序號重新排列 </a>|
|<a href="#c8">將array裡塞入其他字串 </a>|
|<a href="#c9">window.open應用 </a>|
|<a href="#c10">基本陣列宣告方法 </a>|
|<a href="#c11">二維陣列</a>|
|<a href="#c12">用二維陣列存放所有text:tdtext[第幾個tr][第幾個td]</a>|
|<a href="#c13">.serialize()序列化表單值</a>|
|<a href="#c14">eval():可计算某个字符串，并执行其中的的JavaScript 代码。</a> |
|<a href="#c15">select option新增.清空</a>|
|<a href="#c16">避免Enter直接submit</a>|
|<a href="#c17">增加row於table的第一行</a>|
|<a href="#c18">當按下enter時執行doquery函數</a>|
|<a href="#c19">array .join方法:返回字串 .push:加入陣列</a>|
|<a href="#c20">若name或id只有一個時可以直接使用name呼叫屬性</a>|
|<a href="#c21">jQuery收合延展功能:http://jsfiddle.net/eK8X5/10885/</a>|
|<a href="#c22">字串拆解(subString)</a>|
|<a href="#c23">用name檢查多個checkbox是否勾選</a>|
|<a href="#c24">處理javascript浮點數精準問題:</a>|
|<a href="#c25">轉換溫度(零式與攝氏):</a>|
|<a href="#c26">javascript:跳轉上下頁面:</a>|
|<a href="#c27">window(self,top,parent)知識</a>|
|<a href="#c28">javascript:讀取文字檔檔案</a>|
|<a href="#c29">javascript:製作基本頁籤</a>|
|<a href="#c30">Fullcalender使用範例</a>|

將option指向初始位置
document.getElementById("xxxx").selectedIndex = 0;

將指定的標籤隱藏(不會佔版面空間)
document.getElementById("xxx").style.display="none";

能見度(Visibility) 隱藏元素時 仍會佔版面空間
document.getElementById("xxx").style.visibility="hidden";

將標籤顯示於同一行
document.getElementById("xxx").style.display="inline";

將標籤區塊顯示
document.getElementById("xxx").style.display="block";

查看選單的指標
var SheetNo = document.getElementById("SheetNo");
SheetNo.selectedIndex
<================================================><br>
<a id="a1" href="#top">使用javascript的方式(寫入或嵌入)</a>
```
寫入式:
<script>//內容</script>

嵌入式:
<script src="myScript.js"></script>
```
<==============================================><br>
<a id="a2" href="#top">宣告基本類型(string,number,object,array,variable)與function注意事項</a>
```
<script>
//可一次宣告多個類型
var a,b,c;
a="123";b=2;c=a+b;

var person = "John Doe",carName = "Volvo",price = 200;

//string類型
var answer1 = "It's alright";

//number類型
var x1 = 34.00;
var x2 = 34;
var x3 = 3.14;
var x = 123e5;//12300000
var y = 123e-5;//0.00123
var z = 0xFF;//255

//轉換其它進制
var myNumber = 128;
document.getElementById("demo").innerHTML = "128 = " + 
myNumber + " Decimal, " +//10進制
myNumber.toString(16) + " Hexadecimal, " +//16進制
myNumber.toString(8) + " Octal, " +//8進制
myNumber.toString(2) + " Binary."//2進制


//物件類型(取用:person.firstName or person["firstName"] )
//使用object方法:person.fullName() 若直接使用:person.fullName則會印出function(){return this.firstName + " " + this.lastName;}
var person = {
    firstName : "John",
    lastName  : "Doe",
    age       : 50,
    eyeColor  : "blue"
	fullName : function() {
       return this.firstName + " " + this.lastName;
    }
};

var person = new Object();
person.firstName = "John";
person.lastName = "Doe";
person.age = 50;
person.eyeColor = "blue"; 

//使用陣列存取物件資料
var auntie = ['陳小美', 22, {
    strength: 34,
    agility: 25,
    intelligence: 96
}, true];

//取出小美的力量值:34
console.log(auntie[2].strength); 


//陣列類型(取用:cars[0])
var cars = ["Saab","Volvo","BMW"];

//function注意事項
//函數的聲明高於變數(undefine)的聲明,若變數有值則高於函數
function b(){
          console.log(3);
          }
var b=2; 
console.log(b);//b為函數 

var a = 1;
(function(){
  //在下方宣告var a = 100;時 等價 已在這行宣告 var a; 並在原行a=100;(若原行宣告 a=100 則部會觸發)
  console.log(a);    //  undefined:因為javascript會將variable變數宣告放置最前面
  var a = 100;
  console.log(a);    // 100
})();

function getScore () {
    // 局部變數 - function scope
    // 作用範圍只在函數內部
    var num1 = 2;
    var num3 = 4;
    
    // 如果沒加 var 宣告變數，這個變數則是一個全域變數
    num2 = 5; // 存取到全域變數 num2
    num4 = 6; // 宣告一個新的全域變數 num4

    // 函數也可以宣告在其他函數內部 (nested function) - function scope
    function add() {
        // 內部函數可以存取到外部函數的局部變數
        return name + ' scored ' + (num1 + num2 + num3);
    } 
    return add();
}

</script>
```
<============================================================><br>
<a id="a3" href="#top">this解說:https://software.intel.com/zh-cn/blogs/2013/10/09/javascript-this</a>
```
**Javascript裡的this看的是究竟是誰調用該函式，而不是看該函式被定義在哪個物件內**
**調用函式的前方並未有物件，則函式內this就指向全域物件**
ex:
	var obj = {
	x: 20,
	f: function(){ console.log(this.x); }
	};

	obj.f(); //由於調用f函式時，點前面物件為obj，故f內的this指向obj，則輸出為20。

ex:	
	obj.innerobj = {
		x: 30,
		f: function(){ console.log(this.x); }
	}

	obj.innerobj.f(); //由於調用f函式時，點前面物件為obj.innerobj，故f內的this指向obj.innerobj，則輸出為30	


ex: 
	var x = 10;
	var f = function(){
		console.log(this.x);
	};

	f(); //由於調用f函式時，前方並未有[物件]的形式，故f內的this指向全域物件，則輸出全域變數的x(10)。

ex:
	var x = 10;
	var obj = {
		x: 20,
		f: function(){
			console.log(this.x);
			var foo = function(){ console.log(this.x); }
			foo(); // (2)
		}
	};

	obj.f();  // (1)
	輸出20 10，
	因為(1)obj.f()調用時，f前面物件為obj，故f內的this指向obj。
	但因為調用f內的(2)foo函式時是用foo()，調用的前方並"未有物件"，故foo內的this指向全域物件，所以輸出會是全域變數的x的值。

	若要讓foo內使用obj.x的值，解法如下：
	var x = 10;
	var obj = {
		x: 20,
		f: function(){
			console.log(this.x);
			var that = this; //使用that保留在這個函式內的this
			var foo = function(){ console.log(that.x); } //使用that取得obj
			foo();
		}
	};

	obj.f();

ex:
	var x = 10;
	var obj = {
		x: 20,
		f: function(){ console.log(this.x); }
	};

	obj.f(); // (1)

	var fOut = obj.f;//得到的是obj物件裡的方法,所以沒有obj.x
	fOut(); //(2)

	var obj2 = {
		x: 30,
		f: obj.f
	}

	obj2.f(); // (3)

	(1)obj.f()的f所指向的是obj，這比較沒有問題，輸出的會是20；
	(2)fOut()裡的this，則是因為調用時前方無物件，則this所指的是全域物件，輸出的會是10
	(3)obj2.f()則是obj2去呼叫f，故f內的this指向的是obj2，輸出的會是30。


	***.this指向利用call或apply所指派給this的物件***
	call與apply都是呼叫該函式並讓該函式的this指向給予call或apply的第一個參數。
	至於call和apply的差別則是在於其後面給予被調用之函式的參數放入的方法不同，
	一個是直接攤平放在第二個以後的參數；
	一個是直接放入一個裡面放要給予之參數的陣列。
	公式

	1.(A物件.)函式.call(B物件,參數1,參數2,參數3, ......); //函式的this指向B物件(若B物件為null，則指向全域物件)
	2.(A物件.)函式.apply(B物件,[參數1,參數2,參數3, ......]); //函式的this指向B物件(若B物件為null，則指向全域物件)
ex:
	call:
		var obj = {
			x: 20;
			f: function(){ console.log(this.x); }
		};

		var obj2 = {
			x: 30;
		};

		obj1.f.call(obj2); //利用call指派f的this為指向obj2，故輸出為30
```
<=================================================><br>
<a id="a4" href="#top">取得類型名稱</a>
```
typeof 放入欲取得的類型
ex:console.log(typeof "") => 輸出:string 
```
<====================================================><br>
<a id="a5" href="#top">改變css樣式</a>
```
function change(){
	document.getElementById('demo').style.fontSize='35px';//改變字體大小
	document.getElementById('demo').style.backgroundColor="yellow";//改變背景顏色
	document.getElementById('demo').style.display='none';//隱藏元素
	document.getElementById('demo').style.display='block'//顯示元素

	//直接用cssText設定
	var foo = document.getElementById('foo');
    foo.style.cssText = 'font-size: 20px; color: purple;';// 將 foo 的字體大小設為 20px、字體顏色設為紫色
}
```
<=======================================================><br>
<a id="a6" href="#top">輸出的文字的各個方式(alert,console,document)</a>
```
<script>
x = 2 + 3 + "5" ;
console.log(x); => 輸出:55
document.write(5 + 6);
document.getElementById("demo").innerHTML = 5 + 6;
window.alert(5 + 6);
console.log(5 + 6);
</script>
```
<=====================================================><br>
<a id="a7" href="#top"> ++ 與 -- 的注意事項</a>
```
//++--放後面:執行後再加(減),++--放前面:執行前先加(減)在輸出
<script>
var y = 5;
document.getElementById("demo1").innerHTML = y++; //輸出5(因為執行完敘述句在加)
document.getElementById("demo2").innerHTML = y; //輸出6
</script>
```
<======================================================><br>
<a id="a8" href="#top">string常用屬性</a>
```
*length:*
<script>
var txt = "ABCDEFGHIJKLMNOPQRSTUVWXYZ";
console.log(txt.length);
</script>

*連接字串(使用 \):*
<script>
console.log("Hello \
Dolly!");//輸出:Hello Dolly!
console.log("Hello"+
"Dolly!");//輸出:Hello Dolly!
</script>

*indexOf(放入字串):尋找第一個符合的指標*
<script>
var str = "Please locate where 'locate' occurs!";
var pos = str.indexOf("locate");
document.getElementById("demo").innerHTML = pos;
</script>

*match(/欲搜尋的字串/g):*
<script>
function myFunction() {
    var str = "The rain in SPAIN stays mainly in the plain 123"; 
    var res = str.match(/ain/g);//若都沒有則會是null,若有則會輸出:ain,ain,ain(已逗號分別)
	var res = str.match(/\d+/g);//將所有數字輸出出來 =>1,2,3
    document.getElementById("demo").innerHTML = res;
}
</script>

*replace(被取代字串,取代字串):*
<script>
function myFunction() {
    var str = "Please visit Microsoft!";
    var txt = str.replace("Microsoft","W3Schools");
    document.getElementById("demo").innerHTML = txt;
}
</script>

*toUpperCase():英文轉大寫,toLowerCase():英文轉小寫*
<script>
function myFunction() {
    var text = document.getElementById("demo").innerHTML;
    document.getElementById("demo").innerHTML = text.toUpperCase();
}
</script>

*split(分隔字串):*
<script>
function myFunction() {
    var str = "a,b,c,d,e,f";
    var arr = str.split(",");//回傳陣列
    document.getElementById("demo").innerHTML = arr[0];
}
</script>

*substr(x,y):代表從0開始到第x個開始擷取後y個字元*
<script>
 var str = "789456123";
 var x=str.substr(1,3);//x=894,x[0]=8(取第一個字元(string))
</script>
```
<=======================================================><br>
<a id="a9" href="#top">Math常用屬性</a>
```
*.PI:*
<script>
document.getElementById("demo").innerHTML = Math.PI;//輸出:3.141592653589793
</script>

*.round(float):四捨五入*
<script>
document.getElementById("demo").innerHTML = Math.round(4.45);//輸出:4
</script>

*.ceil(數字):無條件進位法*
<script>
document.getElementById("demo").innerHTML = Math.ceil(4.001002);//輸出:5
</script>

*.floor(數字):無條件捨去法*
<script>
document.getElementById("demo").innerHTML = Math.floor(4.99999);//輸出:4
</script>

*.pow(數字,次方):*
<script>
document.getElementById("demo").innerHTML = Math.pow(8,2);//輸出:64
</script>

*.sqrt(數字):開根號*
<script>
  document.getElementById("demo").innerHTML = Math.sqrt(64);//輸出:8
</script>

*.abs(數字):絕對值(轉正)*
<script>
document.getElementById("demo").innerHTML = Math.abs(-4.4);//輸出:4.4
</script>

*.random():亂數產生0~0.9~的數字*
<script>
document.getElementById("demo").innerHTML =
Math.floor(Math.random() * 10) + 1;
</script>
```
<========================================================><br>
<a id="a10" href="#top">Date常用屬性</a>
```
*取得今天時間*
<script>
document.getElementById("demo").innerHTML = Date();
</script>

*取得今年年分*
<script>
var d = new Date();
document.getElementById("demo").innerHTML = d.getFullYear();
</script>

*取得星期*
<script>
var d = new Date();
var days = ["Sunday","Monday","Tuesday","Wednesday","Thursday","Friday","Saturday"];
document.getElementById("demo").innerHTML = days[d.getDay()];
</script>

*時鐘顯示時分秒*
<script>
function startTime() {
    var today = new Date();
    var h = today.getHours();
    var m = today.getMinutes();
    var s = today.getSeconds();
    m = checkTime(m);
    s = checkTime(s);
    document.getElementById('txt').innerHTML =
    h + ":" + m + ":" + s;
    var t = setTimeout("startTime()", 1000);
}
function checkTime(i) {
    if (i < 10) {i = "0" + i};  // add zero in front of numbers < 10
    return i;
}
</script>
<body onload="startTime()">
<div id="txt"></div>
</body>
```
<============================================================><br>
<a id="a11" href="#top">Array常用屬性</a>
```
*.concat(可放多個array):合併陣列(依序往後加)*
<script>
var myGirls = ["Cecilie", "Lone"];
var myBoys = ["Emil", "Tobias", "Linus"];
var myChildren = myGirls.concat(myBoys);
document.getElementById("demo").innerHTML = myChildren;
</script>

*.join(可放入字串或數字):將陣列輸出*
<script>
var fruits = ["Banana", "Orange", "Apple", "Mango"];
document.getElementById("demo").innerHTML = fruits.join("");//加空字串輸出:BananaOrangeAppleMango
document.getElementById("demo").innerHTML = fruits.join();//不加字串輸出:Banana,Orange,Apple,Mango
document.getElementById("demo").innerHTML = fruits.join("*");//加*號輸出:Banana*Orange*Apple*Mango
</script>

*.pop():刪除最後一個*
<script>
var fruits = ["Banana", "Orange", "Apple", "Mango"];
document.getElementById("demo1").innerHTML = fruits;//Banana,Orange,Apple,Mango
fruits.pop();
document.getElementById("demo2").innerHTML = fruits;//Banana,Orange,Apple
</script>

*.shift():刪除第一個*
<script>
var fruits = ["Banana", "Orange", "Apple", "Mango"];
document.getElementById("demo1").innerHTML = fruits;
fruits.shift();
document.getElementById("demo2").innerHTML = fruits;
</script>

*.push(可放多個字串或數字)*
<script>
var fruits = ["Banana", "Orange", "Apple", "Mango"];
document.getElementById("demo").innerHTML = fruits;

function myFunction() {
    fruits.push("Kiwi",123);
    document.getElementById("demo").innerHTML = fruits;//Banana,Orange,Apple,Mango,Kiwi,123
}
</script>

*.reverse():順序顛倒*
<script>
var fruits = ["Banana", "Orange", "Apple", "Mango"];
document.getElementById("demo").innerHTML = fruits;

function myFunction() {
    fruits.reverse();
    document.getElementById("demo").innerHTML = fruits;
}
</script>

*.slice(開始,結束):回傳範圍內的陣列元素(回傳array)*
<script>
var fruits = ["Banana", "Orange", "Lemon", "Apple", "Mango"];
var citrus = fruits.slice(1,3);
document.getElementById("demo").innerHTML = citrus;//Orange,Lemon
</script>

*.sort():排序*
大到小:
<script>
var points = [40, 100, 1, 5, 25, 10];
document.getElementById("demo").innerHTML = points;    
function myFunction() {
    points.sort(function(a, b){return b - a});
    document.getElementById("demo").innerHTML = points;//100,40,25,10,5,1
}
</script>

小到大:
<script>
var points = [40, 100, 1, 5, 25, 10];
document.getElementById("demo").innerHTML = points;    
function myFunction() {
    points.sort(function(a, b){return a - b});
    document.getElementById("demo").innerHTML = points;//1,5,10,25,40,100
</script>

*.toString():輸出為字串*
<script>
var fruits = ["Banana", "Orange", "Apple", "Mango"];
document.getElementById("demo").innerHTML = fruits.toString();//Banana,Orange,Apple,Mango
</script>
```
<====================================================><br>
<a id="a11-2" href="#top">Array-list用法</a>
```javascript

var list = [
    { date: '12/1/2011', reading: 3, id: 20055 },
    { date: '13/1/2011', reading: 5, id: 20053 },
    { date: '14/1/2011', reading: 6, id: 45652 }
];

list.push({ date: '12/1/2011', reading: 3, id: 20056 });

alert(list[1].date);
```
<====================================================><br>
<a id="a12" href="#top">常用的幾種迴圈與敘述(if.else if.else.break.continue,switch)</a>
```
*for:*
var x = "", i;
for (i=0; i<5; i++) {
	x = x + "The number is " + i + "<br>";
}

*while:*
var text = "";
var i = 0;
while (i < 10) {
    text += "<br>The number is " + i;
    i++;
}

*do while:*
var text = ""
var i = 0;
do {
    text += "<br>The number is " + i;
    i++;
}
while (i < 10);  

*break用法:*
var text = "";
var i;
for (i = 0; i < 10; i++) {
    if (i === 3) { break; }
    text += "The number is " + i + "<br>";
}

*continue用法:*
var text = "";
var i;
for (i = 0; i < 10; i++) {
    if (i === 3) { continue; }
    text += "The number is " + i + "<br>";
}

*for in 迴圈用法:* 輸出:John Doe 25
var txt = "";
var person = {fname:"John", lname:"Doe", age:25}; 
var x;
for (x in person) {
    txt += person[x] + " ";
}
```
<======================================================><br>
<a id="a13" href="#top">try catch用法</a>
```javascript
 var txt = "";
 try {
        adddlert("Welcome guest!");
    }
    catch(err) {
        txt = "There was an error on this page.\n\n";
        txt += "Click OK to continue viewing this page,\n";
        txt += "or Cancel to return to the home page.\n\n";
		txt += "The error is "+err;
        if(!confirm(txt)) {
            document.location.href = "https://www.w3schools.com/";
        }
    }
```
<======================================================><br>
<a id="a14" href="#top">Iterator用法</a>
```javascript
    var c = console;
    var ai = arrayIterator(['x', 'y', 'z']); 
        
    function arrayIterator(array){
        var i = 0,j = 0;
        var obj = {
            //取得下一個數值
            next: function(){
                return i < array.length ?{value: array[i++]} :{value: undefined};
            },

            //若還有下一個則回傳true,否則回false        
            hasNext: function(){
                return j++ < array.length
            },

            //回第一個
            toBegin:function(){
                i=0,j=0;
                return true;
            }
        }
        return obj; 
    } 

     while(ai.hasNext()){
      c.log(ai.next());
     }
  /*
    c.log(typeof ai.next().value); //string
    c.log(ai.next()); // { value: "y", done: false }
    c.log(ai.next()); // { value: "z", done: false }
    c.log(ai.next()); // { value: undefined, done: true }
  */
   
```
<======================================================><br>
<a id="a15" href="#top">function閉包用法</a>
```javascript
ex1:
function makeAdder(x) {
  return function(y) {
    return x + y;
  };
}

var add5 = makeAdder(5);
var add10 = makeAdder(10);

console.log(add5(2));  // 7  =>function(2) {return 5 + 2;};
console.log(add10(2)); // 12 =>function(2) {return 10 + 2;};
/*
add5 與 add10 都是閉包。他們共享函式的定義，卻保有不同的環境：
在 add5 的作用域環境，x 是 5。
在 add10 的作用域環境， x 則是 10。
*/

//------------------------------------------------------------------
ex2:字體大小按鈕
function makeSizer(size) {
  return function() {
    document.body.style.fontSize = size + 'px';
  };
}

var size12 = makeSizer(12);
document.getElementById('size-12').onclick = size12;

//------------------------------------------------------------------
ex3:閉包模擬私有方法
function Counter() {
    var privateCounter = 0;
    function changeBy(val) {
        privateCounter += val;
    }
    return {
        increment: function() {
            changeBy(1);
        },
        decrement: function() {
            changeBy(-1);
        },
        value: function() {
            return privateCounter;
        }
    };   
  };
/*
每個閉包都以各自的閉包，在參照不同版本的 privateCounter 變數。
var counter1 = Counter();
var counter2 = Counter();
alert(counter1.value()); /* Alerts 0 */
counter1.increment();
counter1.increment();
alert(counter1.value()); /* Alerts 2 */
counter1.decrement();
alert(counter1.value()); /* Alerts 1 */
alert(counter2.value()); /* Alerts 0 */
*/
```
<======================================================><br>
<a id="a16" href="#top">function callback用法</a>
```javascript
//首先先技術解釋
function aaa(){
  console.log(123);
}
aaa();
bbb();
function bbb(){
  console.log(234);
}
// => 123
// => 234
這是 function 的定義方式，作用等同於 Ruby 的 method，如果前面先使用會等後面宣告補上才執行，& 再來

var ccc = function(){
  console.log(345);
}
ccc();
ddd();
var ddd = function(){
  console.log(456);
}
// => 345
// => Error : ddd is not a function
//這是 lambda / anonymous function 的宣告方式，本身是把一支程式丟到一個變數內，所以還沒出現的不能執行，再來，所謂的 callback

//func是一個函式
function temp(func){
    if(func && typeof(func)==='function'){
        func(123);
    }
}
temp(function(source){console.log(source)});
// => 123

//每一秒執行一次
window.setTimeout( function(){ ... }, 1000);

/*

這其實都是callback寫法就是，總歸到後面就是寫支程式丟到另外一支程式內跑，你可以丟 N 層下去，但同名變數希望過個水（換個名稱）有的沒的
至於 JavaScript 的 call() 和 apply() 不建議新手摸，因為那個比較偏 prototype 的寫法了 … 那邊很邪惡，真的要研究有兩本書可以看：『JavaScript Good Parts』和『JavaScript Design Pattern』但除非你在寫核心，否則很少要自幹 prototype，所以除非你想點滿 JavaScript 技能才繼續下去唄，以下是單純的小 DEMO 達到類似 OOP 的動作，但這票東西後來 ECMAScript6 有擴充類似的用法，所以哪天都用不到了才是
*/

var Car = function(color){this.color = color;}
Car.prototype.getColor = function(){return this.color;}
Car.prototype.setColor = function(color){return this.color = color;}
blue_car = new Car('blue');
red_car = new Car('red');
blue_car.getColor(); // => 'blue'
red_car.getColor(); // => 'red'
blue_car.setColor('light_blue');
red_car.setColor('dark_red');
blue_car.getColor(); // => 'light_blue'
red_car.getColor(); // => 'dark_red'

//同場加映你說的call() & apply() 和一般作法的差別

var dogSay = function(say){console.log(say);};
dosSay('wow!!');
// => 'wow!!' // 一般的作法，有進有出
var meowSay = function(a,b,c){console.log(this.say);console.log(a,b,c)};
meowSay.call({say:'meow!!'} , 1 , 2 , 3)
// => 'meow!!' ; 1 2 3
meowSay.call({say:'meow!!'} , [1 , 2 , 3])
// => 'meow!!' ; [1 2 3] undefined undefined
meowSay.apply({say:'MEOW!!'} , 1 , 2 , 3)
// => Arguments list has wrong type // 需對等數量
meowSay.apply({say:'MEOW!!'} , [1 , 2 , 3])
// => 'MEOW!!' ; 1 2 3

//区分apply,call就一句话,
　　foo.call(this, arg1,arg2,arg3) == foo.apply(this, arguments)==this.foo(arg1, arg2, arg3)
```
<==================================================><br>
<a id="a17" href="#top">convert the js object to JSON</a><br/>
```javascript
var j={"name":"binchen"};
JSON.stringify(j); // '{"name":"binchen"}'
```
<==================================================><br>
<a id="a18" href="#top">Check string matches a regex in JS</a><br/>
```javascript
/^([a-z0-9]{5,})$/.test('abc1');   // false

/^([a-z0-9]{5,})$/.test('abc12');   // true

/^([a-z0-9]{5,})$/.test('abc123');   // true
```
<==================================================><br>
<a id="a19" href="#top">IIFE用法:即刻執行函數(immediately invoked function expression)</a><br/>
```javascript
//一個一般的函式會是以下這樣
var funcA = function(){
    console.log('hello!');
};
//去執行他
funcA();  //會在console中印出'hello!'

//而IIFE看起來會是以下這樣
(function funcB(){ //IIFE的開頭
    console.log('hello!') //函式內執行的內容
}()); //IIFE的結尾
//不需要特別去執行就會直接在console中印出hello!

funcB();  //但是當我們去做呼叫時會出現「funcB is not defined」的錯誤，因為在IIFE開頭的括號是代表這段程式碼是作為一個述句執行裡面的運算式，並不是以function去宣告函式，所以他也不會被存在全域變數中，也就不可能呼叫的到了。


//IIFE可以是匿名函式(就是不幫函式取名字)，因為他馬上就會執行了，之後也不需要再呼叫他，所以有沒有名字都無所謂。
(function(str){   //我們在這裡加入str用來裝執行時傳入的參數。
    console.log(str);
}('hello'));   //我們把字串'hello'傳入IIFE中
//不需要執行便會直接在console中印出hello
---------------------------------------------------------------------------------------------------------
var a = !function(str){
      console.log(str);
}('HELLO');
//console印出:HELLO
console.log(a);//回傳true=> !(undefined=false)=true
---------------------------------------------------------------------------------------------------------
//建立一個一般的函式，並觀察temp在各個地方的變化
function funcA(str){
    var temp = '';
    console.log('(1)：' + temp);
    if(str !== ''){
        var temp = str;
        console.log('(2)：' + temp);
    }
    console.log('(3)：' + temp);
};
funcA('hello');  
//執行後會在console上印出：
//(1)：''
//(2)：hello
//(3)：hello
//會發現在if內宣告的同名變數temp會在if中設定新的值後，會連整個函式funcA原本的temp值都改變了。

//接著在函式內使用IIFE，再觀察temp的變化
function funcB(str){
    var temp = '';
    console.log('(1)：' + temp);
    if(str !== ''){
        (function(){
        var temp = str;
        console.log('(2)：' + temp);}());
    }
    console.log('(3)：' + temp);
};

funcB('hello');
//執行後會在console上印出：
//(1)：''
//(2)：hello
//(3)：''
//可以看到temp這個變數在IIFE中被改變的內容並不會遺留到IIFE外的任何地方，這樣就可以避免在同個環境執行時，共用同個變數名稱會影響到原本的內容。

//***若用es6的let變數宣告則等於上面用IIFE效果***
function funcC(str){
    let temp = '';
    console.log('(1):' + temp);
    if(str != ''){
        let temp = str;
        console.log('(2):' + temp);
    };
    console.log('(3):' + temp);
};

funcC('hello!');
//會印出以下結果
//(1):''
//(2):hello!
//(3):''

```
<==================================================><br>
<a id="a20" href="#top">雙重function函式使用</a><br/>
1.雙重函式之使用
```javascript
 function a(str) {
    var myVar = 'Local'
        function b(aaa) {
        // b 的外層為 a()       
        console.log(aaa) // Local
        }
        console.log(str) // Local
        console.log(b);
    return b;//這邊需要return否則會報錯,並且會執行b(111)
}
```
```html
<button onclick="a(147)(111);">123</button>
```
console:
```txt
147
function b(aaa) {
      // b 的外層為 a()     
      window.runnerWindow.proxyConsole.log(aaa) // Local
    }
111
```
---------------------------------------------
2.變數宣告優先序
```javascript
 function bar(foo) {
    // 此二，誰優先看 Code 誰在後就可覆寫前
    //優先: 2
    var foo = 'varFoo'  

    // 優先:1
    var foo = function () { console.log('函式表達') }

    // 優先: 3
    function foo(){ console.log('函式宣告') }
    // 將 傳入變數 foo 刪除，才可見 this.foo的值 

    //優先:4(傳入的參數=this.foo)
    this.foo = 'thisFoo';  
    
    console.log(foo)
}
```

<==================================================><br>
<a id="a21" href="#top">canvas畫圖(神奇寶貝球)</a>

- 需先將html標籤寫出來 : ```<canvas id="myCanvas"></canvas>```
- 使用js抓取標籤

```javascript
//這一行去抓取canvas的標籤
let canvas = document.getElementById("myCanvas");
//接著指定繪圖方式
let ctx = canvas.getContext("2d");
//讓canvas的高度和寬度等於整個畫面，讓整個視窗都是你的畫布
canvas.height = window.innerHeight
canvas.weidth = window.innerWeight
```
- 劃一條線(黑白) : 左到右

```javascript
//在繪製任何東西之前，我們都要來個開始，像全天下所有的故事一樣
ctx.beginPath();
//我們用moveTo(x,y)來指定線的起點座標
ctx.moveTo(50,50)
//之後使用lineTo(x,y)來指定與前一個座標相連的點
ctx.lineTo(100,50)
//用stroke()來繪製相連點的線
ctx.stroke()
```
- 畫一個三角形,並設定顏色.填滿顏色

```javascript
    //使用lineWidth指定線條寬度
    ctx.lineWidth = 3
    //使用strokeStyle指定線條顏色
    ctx.strokeStyle = "#0000FF"
    //用fillStyle指定填滿色彩
    ctx.fillStyle = "#FF0000"
    ctx.beginPath()
    ctx.moveTo(50,50)
    ctx.lineTo(100,50)
    ctx.lineTo(50,100)
    ctx.lineTo(50,50)
    ctx.closePath()
    //用fill()填滿圍起來的範圍
    ctx.fill()
    ctx.stroke()
```
- 畫一個四角形
- ps:使用rect()來畫，沒有接著stroke()就不會有框線，沒有fill()就不會填滿

```javascript
ctx.beginPath()
//沿用寬度及色彩設定
ctx.lineWidth = 3;
ctx.strokeStyle = "#0000FF"
ctx.fillStyle = "#FF0000"
/*使用rect(x,y,w,h)繪製四角形
x,y一樣是座標，w和h是四邊形的寬和高*/
ctx.rect(50,50,80,100);
ctx.fill()
ctx.stroke()
```
- 畫圓

```javascript
ctx.beginPath()
//沿用寬度及色彩設定
ctx.lineWidth = 3;
ctx.strokeStyle = "#0000FF"
ctx.fillStyle = "#FF0000"
/*
使用arc(x,y,r,s,e)畫一個圓
x,y是圓心的座標，r是半徑，s和e是起點和終點的角度
Math.PI=180度,以順時針旋轉
*/
ctx.arc(50,50,25,0,Math.PI*2)
ctx.fill()
ctx.stroke()
```
- 畫出一顆神奇寶貝球

```javascript
//畫一個下半圓，指定顏色為白色
ctx.beginPath()
ctx.lineWidth = 2;
ctx.fillStyle = "#FFFFFF"
ctx.arc(200,200,100,0,Math.PI)
ctx.fill()
ctx.stroke()

//畫一個上半圓，指定顏色為紅色
ctx.beginPath()
ctx.fillStyle = "#FF0000"
ctx.arc(200,200,100,Math.PI,Math.PI*2)
ctx.fill()
ctx.stroke()

//畫中間的線和圈圈，指定顏色為白色
ctx.beginPath()
ctx.fillStyle = "#FFFFFF"
//從圓的左邊開始
ctx.moveTo(100,200)
//連到中間後接著一個上半圓
ctx.arc(200,200,30,Math.PI,Math.PI*2)
//繞過去後再畫一條直線到圓的右邊
ctx.lineTo(300,200)
//最後沿著線繞回來畫一個下半圓
ctx.arc(200,200,30,0,Math.PI*2)
ctx.fill()
ctx.stroke()

//畫一個圓形，中間的那個圈圈按鈕
ctx.beginPath()
ctx.arc(200,200,15,0,Math.PI*2)
ctx.stroke()
```

<==================================================><br>
<a id="a0601" href="#top">let,const變數語法</a><br/>
let變數:
```javascript
//let:宛如java需先宣告才能使用
// var 的情况
console.log(foo); // 输出undefined
var foo = 2;

// let 的情况
console.log(bar); // 报错ReferenceError
let bar = 2;

因tmp已被內部let綁住,所以讀取步道var 
var tmp = 123;
if (true) {
  tmp = 'abc'; // 錯誤ReferenceError
  let tmp;
}

//let不允许在相同作用域内，重复声明同一个变量。
// 报错
function func() {
  let a = 10;
  var a = 1;
}

// 报错
function func() {
  let a = 10;
  let a = 1;
}

//不能在函数内部重新声明参数。
function func(arg) {
  let arg; // 报错
}

function func(arg) {
  {
    let arg; // 不报错
  }
}
```
const變數:
```javascript
/*const:一旦声明，常量的值就不能改变。
        一旦声明变量，就必须立即初始化，不能留到以后赋值。
        只声明不赋值，就会报错。
*/

const foo = {};
// 为 foo 添加一个属性，可以成功
foo.prop = 123;
foo.prop // 123
// 将 foo 指向另一个对象，就会报错
foo = {}; // TypeError: "foo" is read-only

const a = [];
a.push('Hello'); // 可执行
a.length = 0;    // 可执行
a = ['Dave'];    // 报错

//将对象冻结，应用Object.freeze方法。
const foo = Object.freeze({});
// 常规模式时，下面一行不起作用；
// 严格模式时，该行会报错
foo.prop = 123;
```
<==================================================><br>
<a id="a0602" href="#top">變數解構賦值(set)</a><br/>
```javascript
舊的作法:
    let a = 1;
    let b = 2;
    let c = 3;

新的作法:
    let [a, b, c] = [1, 2, 3];

例子:
    let [foo, [[bar], baz]] = [1, [[2], 3]];
    foo // 1
    bar // 2
    baz // 3

    let [ , , third] = ["foo", "bar", "baz"];
    third // "baz"

特殊案例:
    let [head, ...tail] = [1, 2, 3, 4];
    head // 1
    tail // [2, 3, 4]

    let [x, y, ...z] = ['a'];
    x // "a"
    y // undefined
    z // []

不完全解構:
    let [x, y] = [1, 2, 3];
    x // 1
    y // 2

    let [a, [b], d] = [1, [2, 3], 4];
    a // 1
    b // 2
    d // 4

利用 Generator 函数賦值:
    function* fibs() {
        let a = 0;
        let b = 1;
        while (true) {
            yield a;
            [a, b] = [b, a + b];
        }
    }

    let [first, second, third, fourth, fifth, sixth] = fibs();
    console.log(first,second,third,fourth,fifth,sixth);//0,1,1,2,3,5
    /*
    0   1
        1   1  
            1   2
                2   3
                    3   5
    0   1   1   2   3   5
    */

默認值:解构赋值允许指定默认值。
例子:
    let [foo = true] = [];
    foo // true

    let [x, y = 'b'] = ['a']; // x='a', y='b'
    let [x, y = 'b'] = ['a', undefined]; // x='a', y='b'

    let [x = 1] = [undefined];//x=1
    let [x = 1] = [null];// x=null(null算是值)

默认值可以引用解构赋值的其他变量，但该变量必须已经声明:
    let [x = 1, y = x] = [];     // x=1; y=1
    let [x = 1, y = x] = [2];    // x=2; y=2
    let [x = 1, y = x] = [1, 2]; // x=1; y=2
    let [x = y, y = 1] = []; //ReferenceError: y is not defined

对象的解构赋值:
let { bar, foo } = { foo: "aaa", bar: "bbb" };
foo // "aaa"
bar // "bbb"

let { baz } = { foo: "aaa", bar: "bbb" };
baz // undefined

let { foo: baz } = { foo: 'aaa', bar: 'bbb' };
//baz = "aaa";
//foo = error: foo is not defined

let obj = { first: 'hello', last: 'world' };
let { first: f, last: l } = obj;
f // 'hello'
l // 'world'


```
<==================================================><br>
<a id="a0610" href="#top">yeild與Generator</a><br/>
```javascript
yeild與Generator必須一起生存
Generator函數必須物名稱前加上*:function *foo(){}
next():做至下一個yeild,並回傳object:{value:值,done:是否還有}

//最簡單的說明範例:
function *foo() {  
    a += 1;  
    yield '';  
    return;
}
var f = foo();
var s1 = f.next(); 
console.log(s1); //回傳yeild:{value: '',done: false}
var s2 = f.next();
console.log(s2); //return沒yeild:{value: undefined,done: true}

 //还可以这样写 
var foo = function *() {     
    var x = 1;  
    var y = yield (x + 1); 
    var z = yield (x + y);//若 yield x + y;等價 yield x;
    return z;
}() 
//當next()時,回傳(value:下一個yeild的值,done:是否還有):object
    // 你必须先执行一下Generator函数，才能把遍历器返回给某个变量
    // 第一次执行next()不可以传参(前面沒yeild)
    var a = foo.next(); //a.value=2,因yield (x + 1);

    //next(3):裡面的3取代前一個yeild:yield (x + 1)>> y=3;  
    var b = foo.next(3);//b.value=4:x=1,y=3;
    var c = foo.next(4);//c.value=4(yield (x + y)=4)
```
<==================================================><br>
<a id="a0611" href="#top">promise的使用</a><br/>
```javascript
const reqPromise = async 參數 => new Promise((resolve, reject) => {
  request.get(參數, (error, response, response_body) => {
    if (error) reject(error)
    let data = JSON.parse(response_body)
    resolve([null, resDataFormat(data)])
  })
}).catch(error => {
  return [error, null]
```
<=====================================================><br>
<a id="b1" href="#top">與其他語言衝突$字符號解決辦法</a>
```
有使用其它的 JavaScript Library 也是用 "$" 怎麼辦？有辦法，用下面這一行就解決了：
jQuery.noConflict();

比較想用 $ 來操作 jQuery 怎麼辦？也有取巧的辦法：
(function($) {
  // 在此區塊內我們使 $ 參照 jQuery 物件
  // 在此區塊內使用 $ 不會與其它函式衝突
})(jQuery);

var $alias = jQuery.noConflict();
接下來你就可以使用 $alias 取代 $。
```
<====================================================><br>
<a id="b2" href="#top">基本操作與串接(Chaining)</a>
```
jQuery 程式碼由 $ (或jQuery) 開始 → 後面會接著圓刮號「()」→ 
而圓刮號裡面的參數是你想叫 jQuery 幫你找什麼 (取得哪個(些)元素) → 接著是你想叫 jQuery 執行什麼動作 (或處理事件)。例如：
// 選取 id 為 el 的元素，並綁定 onclick 事件
// 叫jQuery將其CSS的背景顏色屬性改成灰色
$('#el').click(function() {
  $('#el').css('background-color', 'green');
});  

串接 (Chaining)
在 jQuery 中，幾乎所有成員都會返回自己執行後的結果 - 
也是一個 jQuery 物件，因此你可以連續地使用函數 (Chaining)。以下我們用一個範例來說明 Chaining 是怎麼一回事：

$('#el').css('color', 'blue').css('background-color', 'red');
上面這段程式碼由兩段函式組成：

// 先將文字改成藍色
$('#el').css('color', 'blue');
// 再將背景顏色改為紅色
$('#el').css('background-color', 'red');
```
<=======================================================><br>
<a id="b3" href="#top">選取DOM元素</a>
```
#tag selector:#
在 jQuery 中
$('a'); // 取得頁面中所有的 <a> 標籤元素

在 JavaScript DOM 中
document.getElementsByTagName('a');


#id selector:#
在 jQuery 中
$('#el'); // 取得 id 為 el 的元素

在 JavaScript DOM 中
document.getElementById('el');


#class selector:#
在 jQuery 中
$('.item'); // 取得 class name 為 item 的所有元素

在 JavaScript DOM 中
document.getElementsByClassName('item');

#jQuery Selectors 取回的元素的型態 (type) 是什麼？#
jQuery 物件 ($) 會將匹配到的元素以"陣列 (array)"型態返回一個 jQuery 物件
，也就是說你可以像下面這樣取得被匹配到元素的個數：

// 我們想知道選取到幾個 <a>?
$('a').length; // 直接用 JavaScript array 的 length 屬性取得
$('a').size(); // 或用 jQuery object 的 size 方法

ex:
$('#container').style.display = 'none';
// 錯誤 style is not defined

$('#container').get(0).style.display = 'none';
//正確

Example:
$('#container a'); // 取得 id 為 container 之元素其內部的所有連結 <a>
$('div > p'); // 取得 div 父元素其下所有的 p 子元素
$('tr:first'); // 取得第一個找到的 tr 標籤元素
$('input[name="email"]'); // 取得其 name 屬性值為 email 的 input 元素

例外:JavaScript DOM 物件 --> jQuery 物件
反過來，如果你想將 DOM 轉為 jQuery 物件，只要將 DOM 傳入 $():
$(domElements);
例如：
var $jqueryObject = $(document.getElementById('id'));
```
<====================================================><br>
<a id="b4" href="#top">屬性與樣式(Attributes,CSS)</a>
```
#jQuery 對於 HTML Tag 屬性的操作 (Attributes)#
#取得選取到的元素之屬性值：#
.attr(attributeName)
ex:
取得第一個連結的 title 值：
$('a').attr('title');

#替選取到的元素設定屬性值：#
.attr(attributeName, value)
ex:
替所有連結的 title 屬性設為 Enjoy jQuery：
$('a').attr('title', 'Enjoy jQuery');

#key/value object 的方式來替所有匹配到的元素設定多個屬性值：#
.attr(attributes)
ex:
同時改變 alt 和 title 屬性：
$( "#greatphoto" ).attr({
    alt: "Beijing Brush Seller",
    title: "photo by Kelly Clark"
});

#移除元素屬性也很簡單：#
.removeAttr(attributeName)
ex:
移除所有連結的 title 屬性：
$('a').removeAttr('title');
// 上面同等於這樣做
$('a').attr('title', null);

#jQuery 對 class 這個屬性有特別的處理#
對於 class，jQuery 另外提供個別的函式來作 class 增刪的動作

增加 class:
.addClass(className)
ex:
幫所有的段落加入 selected 和 highlight 類別：
$('p').addClass('selected highlight');//用空白隔開多個 class。

移除 class：
.removeClass(className)
ex:
移除 id 為 wrapper 的元素其 blue 這個類別：
$('#wrapper').removeClass('blue');

#val，一個很常用到的方法，用來取得和設定表單元素的 value 值：#
.val() // get
.val(value) // set
例如，取得表單元素的值：

// 取得下拉選單 (select box) 的值
$('select.foo').val();

// 取得 checkbox 欄位的選取值
$('input:checkbox:checked').val();

// 取得 radio 欄位的選取值
$('input:radio[name=bar]:checked').val();
例如，設定表單元素的值：

// HTML
<input type="text">
// 設定欄位值
$('input').val('Hello World!');
// 設定後的結果
<input type="text" value="Hello World!">

#樣式的操作 (CSS)#
取得第一個段落的字體顏色：
$('p').css('color'); 

替所有段落的透明度設為半透明：
$('p').css('opacity', '0.5');
// 設 opacity 就可以，jQuery 已經幫你處理好跨瀏覽器問題

替所有段落的字體設為紅色，背景設為藍色：(屬性中包含 -，記得加上引號)
$('p').css({
  color: 'red',
  'background-color': 'blue'
});

元素的位置及寬高 - 常用的屬性獨立出來
.width() // 取得元素寬度
.width(value) // 設定元素寬度
.height() // 取得元素高度
.height(value) // 設定元素高度

*取得的值是元素內容寬、高度，不包含 padding, border, margin。*
ex:
取得第一個匹配到的段落元素高度 (px) (無參數)
$('p').height();

設定每個匹配到的段落元素其高度設為 100px (沒指定單位時預設為 px) (有參數)
$('p').height(100);
```
<========================================================><br>
<a id="b5" href="#top">篩選元素 (Traversing)</a>
```
#過濾元素 (Filtering)#
jQuery 有提供一些函數幫助我們方便的「濾出」我們要的目標元素：

#取得第 index 個元素 (index 從 0 開始)#
.eq( index )
ex:
取得匹配的第 3 個元素
$('p').eq(2);
*相較於 .get(index) 得到的是 DOM 物件；.eq(index) 則是 jQuery 物件。*

#找出所有符合表達式條件的元素 (可用逗號分開多個 selector)#
.filter(selector)
ex:
取得類別為 highlight 的所有段落元素：
$('p').filter('.highlight');

#刪除所有符合表達式條件的元素#
.not(selector)
ex:
從選取到的段落元素中，刪除掉類別為 green 的及 id 為 blueone 的元素：
$('p').not('.green, #blueone');

#元素 (節點) 間位置的相互關係:#
*依縱向關係來查訪 (Finding):*
// 取得上一階層的父元素
.parent([selector])

// 取得全部的父元素集合 (祖先元素)
.parents([selector])

// 取得(僅)下一階層的所有子元素之集合 (不含 text nodes)
.children([selector])

// 取得全部的子元素 (含 text nodes)
// 也可以用來取得 iframe 的 content document
.contents()
ex:
// 將 li 的父元素 (可能是 <ul> 或 <ol>) 背景改為紅色
$('li').parent().css('background-color', 'red');
// 將 li 的所有祖先元素背景都改為紅色 (直到 <html> 元素)
$('li').parents().css('background-color', 'red');
// 將 li 的所有 <p> 祖先元素背景都改為紅色
$('li').parents('p').css('background-color', 'red');
// 將有 .selected class 的 div 所有子元素顏色改為藍色
$('div').children('.selected').css('color', 'blue');

*依橫向關係來查訪 (Finding):*
// selector 用來過濾，如果我們只要符合條件的元素
// 取得其後緊鄰的兄弟元素 (同輩元素)
.next([selector])

// 取得從下一個直到最後一個同輩元素
.nextAll([selector])

// 前一個同輩元素
.prev([selector])

// 從前一個直到最開頭的同輩元素
.prevAll([selector])

// 取得其所有同輩元素的集合
.siblings([selector])

#依表達式條件來查訪元素 (Finding)#
.find(selector)
ex:
我們想取得段落下的 span 元素：
// HTML
<p><span>Hello</span> World</p>
// jQuery
$('p').find('span');

//如果寫以下語句,則會直接將p底下span裡所有文字給輸出(無法用get(0))
$('p').find('span').text();
```
<========================================================><br>
<a id="b6" href="#top">DOM 操作 (Manipulation)</a>
```
#改變元素內容 (Changing Contents)#
.html() - 類似 JavaScript DOM 中的 innerHTML
// 取得匹配元素的 HTML 內容 (無參數)
.html()

// 設定匹配元素的HTML內容 (有參數)
.html(htmlString)

ex:
// HTML
<div></div>
// jQuery
$('div').html('<p>Hello World</p>'); 
// 得到的結果
[<div><p>Hello World</p></div>]

#.text() 純文字內容#
// 取得一個字串包含著所有匹配元素的純文字內容 (無參數)
.text()

// 例如 HTML
<p><em>Test1.</em>Test12.</p><p>Test3</p>
// jQuery
$('p').text();
// 得到的結果
Test1.Test2.Test3

// 設定所有匹配元素的純文字內容 (有參數)
// text 裡面的 "<" 與 ">" 會自動被轉成 HTML entities
.text(text)

#插入內容 (Inserting)#
相關函式有 .append(), .prepend(), .before(), .after() 等。

.append(content) - 在每個匹配的元素內部最後面加入內容 (內部插入)
// 例如 HTML
<p>I would like to say: </p> 
// jQuery
$('p').append('<b>Hello</b>'); 
// 得到的結果
[<p>I would like to say: <b>Hello</b></p>]

.prepend(content) - 在每個匹配的元素內部最前面加入... (內部插入)
// 例如 HTML
<p>I would like to say: </p> 
// jQuery
$('p').prepend('<b>Hello</b>'); 
// 得到的結果
[<p><b>Hello</b>I would like to say: </p>]

.before(content) - 在每個匹配的元素前面加入... (外部插入)
// 例如 HTML
<p>I would like to say: </p> 
// jQuery codes
$('p').before('<b>Hello</b>'); 
// 得到的結果
[<b>Hello</b><p>I would like to say: </p>]

.after(content) - 在每個匹配的元素後面加入... (外部插入)
// 例如 HTML
<p>I would like to say: </p> 
// jQuery
$('p').after('<b>Hello</b>');
// 得到的結果
[<p>I would like to say: </p><b>Hello</b>]

#移動元素 (Moving)#
如果在前面這些函式的參數中帶入 "jQuery" 或 "DOM" 物件則代表移動它們。

.append(jQuery or DOM)
// 例如 HTML
<p>I would like to say: </p><b>Hello</b>
// jQuery
$('p').append( $('b') );
// 得到的結果
[<p>I would like to say: <b>Hello</b></p>]

#把自己包起來 (Inserting Around)#
.wrap(html) - 各別包住匹配到的元素
// 例如 HTML
<div class="container">
  <div class="inner">Hello</div>
  <div class="inner">Goodbye</div>
</div>

// jQuery
$('.inner').wrap('<div class="new"></div>');

// 得到的結果
<div class="container">
  <div class="new">
    <div class="inner">Hello</div>
  </div>
  <div class="new">
    <div class="inner">Goodbye</div>
  </div>
</div>

.wrapAll(html) - 一起包住所有匹配到的元素
// 例如 HTML
<div class="container">
  <div class="inner">Hello</div>
  <div class="inner">Goodbye</div>
</div>

// jQuery
$('.inner').wrapAll('<div class="new" />');

// 得到的結果
<div class="container">
  <div class="new">
    <div class="inner">Hello</div>
    <div class="inner">Goodbye</div>
  </div>
</div>

.wrapInner(html) - 各別包到匹配的元素裡面
// 例如 HTML
<div class="container">
  <div class="inner">Hello</div>
  <div class="inner">Goodbye</div>
</div>

// jQuery
$('.inner').wrapInner('<div class="new"></div>');

// 得到的結果
<div class="container">
  <div class="inner">
    <div class="new">Hello</div>
  </div>
  <div class="inner">
    <div class="new">Goodbye</div>
  </div>
</div>

#刪除元素 (Removing)#
.empty() - 刪除匹配到的元素其所有子節點
// 例如 HTML
<div class="container">
  <div class="hello">Hello</div>
  <div class="goodbye">Goodbye</div>
</div>

// jQuery
$('.hello').empty();

// 得到的結果
<div class="container">
  <div class="hello"></div>
  <div class="goodbye">Goodbye</div>
</div>

.remove([selector]) - 從 DOM 中刪除所有匹配到的元素
// 例如 HTML
<div class="container">
  <div class="hello">Hello</div>
  <div class="goodbye">Goodbye</div>
</div>

// jQuery
$('.hello').remove();

// 得到的結果
<div class="container">
  <div class="goodbye">Goodbye</div>
</div>

// 我們也可以多帶入一個 selector 參數，來過濾匹配到的元素
// 例如這樣寫和上面會得到一樣的結果
$('div').remove('.hello');

#複製元素 (Copying)#
.clone([true]) - 複製匹配元素的副本
// 例如 HTML
<div class="container">
  <div class="hello">Hello</div>
  <div class="goodbye">Goodbye</div>
</div>

// jQuery
$('.hello').clone().appendTo('.goodbye');

// 得到的結果
<div class="container">
  <div class="hello">Hello</div>
  <div class="goodbye">
    Goodbye
    <div class="hello">Hello</div>
  </div>
</div>

// 但如果沒用 .clone() 則會得到這樣的結果
<div class="container">
  <div class="goodbye">
    Goodbye
    <div class="hello">Hello</div>
  </div>
</div>
如果想要連綁定的事件一起複製，則加個 true 參數 .clone(true)。
```
<========================================================><br>
<a id="b7" href="#top">事件處理 (Events)</a>
```
https://www.fooish.com/jquery/events.html
```
<===================================================><br>
<a id="c1" href="#top">取得目前的row數</a>
```
var num = document.getElementById("mytable").rows.length;

//table 由上往下增加row
<script>
var i = 2 ;
function myFunction() {   
    var table = document.getElementById("myTable");
    var row = table.insertRow(0);
    var cell1 = row.insertCell(0);
    var cell2 = row.insertCell(1);
    cell1.innerHTML = "Row"+i+ "cell1";
    cell2.innerHTML = "Row"+i+ "cell2";
    i++;
}
</script>
```
<=======================================================><br>
<a id="c2" href="#top">得到select的 value</a>
```
<script type="text/javascript">

   function changeFunc() {
    var selectBox = document.getElementById("selectBox");
    var selectedValue = selectBox.options[selectBox.selectedIndex].value;
    alert(selectedValue);
   }

  </script>
 </head>
 <body>
  <select id="selectBox" onchange="changeFunc();">
   <option value="1">Option #1</option>
   <option value="2">Option #2</option>
  </select>
 </body>
 ```
<======================================================><br>
<a id="c3" href="#top">javascript = = 與 = = = 的差別:</a>
```
兩個等於（==）會對被判別的變數做轉換型別的動作（coercion又稱為implicit type conversion）。
這就是爲什麽有時候不懂一個語言特性會覺得怪怪的。舉例來說：


左邊是int type右邊是string type，但是因為兩個等於會把 string 轉型為int，所以實際比對是
1 = 1
所以是true。 


如果是三個等於（===），那麼就不會有轉換型別的問題，因此
1 === "1" //false
就是false。 


對於物件的等於判斷

和其他oo語言一樣，因為物件指向的都是某一個記憶體位置，所以如果直接把兩個object 做判別會等於false。 

var b = {name: "hello"};
a === b; //false


特別的例子：NaN

NaN意思是:Not A Number，而他的Type其實是number。不過他比較特別是沒有任何數值可以和他相等，就算是NaN自己也不行。換句話說
NaN === NaN //false
 
因此只能使用isNaN()這個Function來判別。 
```
<===============================================================><br>
<a id="c4" href="#top">鍵盤按鍵觸發:</a>
```
keypress
65～90大写
97～122小写

	$(document).keypress(function(event) {
		var keycode = (event.keyCode ? event.keyCode : event.which);
		if (keycode == '81' || keycode == '113') {
		        $('#queryButtonId').click();
		}

		if (keycode == '84' || keycode == '116') {
		        $('#transFileButtonId').click();
		}
	}); 
```
<===========================================================><br>
<a id="c5" href="#top">输出每个 li 元素的文本：</a>
```
$("button").click(function(){
  $("li").each(function(){
    alert($(this).text())
  });
});
```
<============================================================><br>
<a id="c6" href="#top">抓取name=cancelBox的每一個(.each())input輸入框 </a>
```
.prop代表input裡面的屬性
$("input[name='cancelBox']").each(function(){
				if($(this).prop("checked")) {
					barcodeList += $(this).val() + ",";
				}
			});
			
			if (!barcodeList.length > 0) {
				alert("請勾選項目");
				return;
			}
```
<======================================================><br>
<a id="c7" href="#top">將序號重新排列 </a>
```
	var rowCount = document.getElementById("tabContent").rows.length;
	for(var q=0;q<rowCount;q++){
		//將第q個name為count的td裡面的字串設為rowCount-q
		$("td[name='count']:eq("+q+")").text(rowCount-q);	
	};
```
<=======================================================><br>
<a id="c8" href="#top">將array裡塞入其他字串 </a>
```
<button onclick="myFunction()">Try it</button>

<p id="demo"></p>

<script>
var fruits = ["Banana", "Orange", "Apple", "Mango"];
document.getElementById("demo").innerHTML = fruits;

function myFunction() {					    (覆蓋穿插的字串,可多個或一個)
    fruits.splice((整數)第幾個字串之後, (整數)覆蓋幾個字串?, "Lemon", "Kiwi" );
    document.getElementById("demo").innerHTML = fruits;
}

使用.join方法
var arr = new Array(3)
arr[0] = "George"
arr[1] = "John"
arr[2] = "Thomas"

document.write(arr.join("."))
輸出:George.John.Thomas
</script>
```
<==============================================================><br>
<a id="c9" href="#top">window.open()在jsp應用 </a>
:http://www.w3school.com.cn/jsref/met_win_open.asp#windowfeatures
```
	function doDetailQuery(this){
		//得到tr裡面第一個td資料(當要取得當下的標籤時)
		var potName = this.children[0].innerHTML;
		var POTDEPT= ""; 
		if(document.getElementsByName("POTDEPT")[0].checked){                        
		 	POTDEPT=document.getElementsByName("POTDEPT")[0].value; 
	 	}else if(document.getElementsByName("POTDEPT")[1].checked) {                        
		 	POTDEPT=document.getElementsByName("POTDEPT")[1].value; 
	 	 }
	 	 var sDate = document.getElementById("sDate").value;	
	 	 var eDate = document.getElementById("eDate").value;
		var url = 
	    		"<%=request.getContextPath()%>/html/servlet/HttpDispatcher/Csr050105/detail?" +
	    		"potName=" + potName+ "&sDate=" + sDate+"&eDate=" + eDate+"&POTDEPT=" + POTDEPT; 		
		printWindow = window.open(url,"_blank","toolbar=0, location=0, directories=no, status=no, menubar=0, scrollbars=0, resizable=0, copyhistory=yes, width=950, height=720,left=0,top=0");
	}

用window.open連結form表單並先跳至等待載入的頁面(Emr_WindowOpen.jsp)再轉至form的submit:
		window.open('<%=request.getContextPath()%>/html/emr/pages/Emr_WindowOpen.jsp','ExportPDF'+winCount,'top=0, left=0, resizable=yes');
		var AjaxParam = new Array();
		document.getElementById("id_div_Ajaxparam").innerHTML = "";
		AjaxParam.push("<form id='id_form_Ajaxparam' name='pdf'>");
		AjaxParam.push("<input type='hidden' name='ReasonType' value='"+typeNum+"' >");
		AjaxParam.push("<input type='hidden' name='idList' value='" + idList + "' >");
		AjaxParam.push("<input type='hidden' name='isDuplexPrint' value='" + isDuplexPrint + "' >");
		AjaxParam.push("</form>");
		document.getElementById("id_div_Ajaxparam").innerHTML = AjaxParam.join("");
		pdf.target="ExportPDF"+winCount;
		pdf.method="POST"; 	
		pdf.action = "<%=request.getContextPath()%>/html/servlet/HttpDispatcher/Emr0104/doPrint";
		pdf.submit();

Emr_WindowOpen.jsp:
	<%@ page language="java" contentType="text/html; charset=BIG5" pageEncoding="BIG5" %>
	<body style="background-color:#F5FFD9;">載入中，請等待...</body>
```
<==============================================================><br>
<a id="c10" href="#top">基本陣列宣告方法 </a>
```
var person = [];
person[0] = "John";
person[1] = "Doe";
person[2] = 46;
var x = person.length;         // person.length will return 3
var y = person[0];             // person[0] will return "John"
```
<================================================================><br>
<a id="c11" href="#top">二維陣列:</a>
```
var tdtext=[];
var i=0,j=0,d2=7;
for (var c = 0 ; c <= d2 ; c++) {
  tdtext[c] = new Array(d2);
}
```
<==================================================================><br>
<a id="c12" href="#top">用二維陣列存放所有text:tdtext[第幾個tr][第幾個td]</a>
```
var tdtext=[];
var d2=7;
 for (var c = 0 ; c <= d2 ; c++) {
   tdtext[c] = new Array();
 }

function myfunction(pot){
  var i=0;
$("tr[name='trbox']").each(function(){
    //得到tr裡面所有td
  $(this).children().each(function(){ 
	//將td裡面的字串放入陣列中 
	tdtext[i].push($(this).text());
  });
  i++;
});
  alert(tdtext[0][pot]);
}
```
<====================================================================><br>
<a id="c13" href="#top">.serialize()序列化表單值:</a>
```
Form.serialize($("id_form_Ajaxparam"));//將指定的form放入序列化中

<form action="">
First name: <input type="text" name="FirstName" value="Bill" /><br />
Last name: <input type="text" name="LastName" value="Gates" /><br />
</form>

$("div").text($("form").serialize());

輸出:FirstName=Bill&LastName=Gates
```
<====================================================================><br>
<a id="c14" href="#top">eval():可计算某个字符串，并执行其中的的 JavaScript 代码。</a>
```
eval("x=10;y=20;document.write(x*y)")

document.write(eval("2+2"))

var x=10
document.write(eval(x+17))

輸出:
200
4
27
```
<======================================================================><br>
<a id="c15" href="#top">select option新增.清空</a>
```
var option = document.createElement("option");//若要增加很多個OPTION必須依樣新增多個
var noteType = document.getElementById("SELECT ID");
noteType.options.length = 0;//清空選項
noteType.add(option);//新增選項
```
<======================================================================><br>
<a id="c16" href="#top">避免Enter直接submit</a>
```
if (event.keyCode == 13) 
{
event.returnValue = false;
}
```
<=======================================================================><br>
<a id="c17" href="#top">增加row於table的第一行</a>
```
$("table名").prepend("<tr></tr>");
```
<=======================================================================><br>
<a id="c18" href="#top">當按下enter時執行doquery函數</a>
```
onkeydown="e = window.event;(e.keyCode==13)?doQuery():false;"	
```
<=======================================================================><br>
<a id="c19" href="#top">array .join方法:返回字串 .push:加入陣列</a>
```
var AjaxParam = new Array();
	document.getElementById("id_div_Ajaxparam").innerHTML = "";
	AjaxParam.push("<form id='id_form_Ajaxparam' name='form_tab'>");
	AjaxParam.push("<input type='hidden' name='SheetNo' value='"+sheetNo+"' >");
	AjaxParam.push("<input type='hidden' name='BeginDay' value='" + document.getElementById('BeginDay').value + "' >");
	AjaxParam.push("<input type='hidden' name='EndDay' value='" + document.getElementById('EndDay').value + "' >");
	AjaxParam.push("<input type='hidden' name='ChartNo' value='" + document.getElementById('ChartNo').value + "' >");
	AjaxParam.push("</form>");
	document.getElementById("id_div_Ajaxparam").innerHTML = AjaxParam.join("");
	form_tab.target="iframeTableView";//指定在名為iframeTableView的子視窗打開
	form_tab.method="POST";//傳遞方式
	form_tab.action = "<%=request.getContextPath()%>/html/servlet/HttpDispatcher/Emr0107/doTableView";  	
	form_tab.submit();	
```
<=====================================================================><br>
<a id="c20" href="#top">若name或id只有一個時可以直接使用name呼叫屬性</a>
```
<form id='id_form_Ajaxparam' name='form_tab'></form>

form_tab.target="iframeTableView";//指定在名為iframeTableView的子視窗打開
form_tab.method="POST";//傳遞方式
form_tab.action = "<%=request.getContextPath()%>/html/servlet/HttpDispatcher/Emr0107/doTableView";  	
form_tab.submit();
```
<=====================================================================><br>
<a id="c21" href="#top">jQuery收合延展功能```:http://jsfiddle.net/eK8X5/10885/```</a>
```
HTML:
<div class="container">
    <div class="header"><span>Expand</span>

    </div>
    <div class="content">
        <ul>
            <li>This is just some random content1.</li>
            <li>This is just some random content2.</li>
            <li>This is just some random content.</li>
            <li>This is just some random content.</li>
        </ul>
    </div>
</div>

CSS:
.container {
    width:100%;
    border:1px solid #d3d3d3;
}
.container div {
    width:100%;
}
.container .header {
    background-color:#d3d3d3;
    padding: 2px;
    cursor: pointer;
    font-weight: bold;
}
.container .content {
    display: none;
    padding : 5px;
}

JS(jQuery):
$(".header").click(function () {

    $(this).toggleClass('expand').nextUntil().slideToggle(500);

});
```
<================================================================><br>
<a id="c22" href="#top">字串拆解:</a>
```
//代表從0開始屬到第三個開始擷取後五個字元
idList.substr(3,5);
```
<=================================================================><br>
<a id="c23" href="#top">用name檢查多個checkbox是否勾選:</a>
```
//因有多個name=SheetNo的checkbox
var sheetList = document.getElementsByName('SheetNo');
	var isChecked = false;
	for(var i=0 ; i<sheetList.length ; i++){
		if(sheetList[i].checked){
			isChecked = true;
			break;
		}
	}
	if(!isChecked){
		alert("請勾選 「病歷類型」 後再執行查詢！");
		return false;
	}
```
<==================================================================><br>
<a id="c24" href="#top">處理javascript浮點數精準問題:</a>
```
//浮點數相加
function FloatAdd(arg1, arg2)
{
  var r1, r2, m;
  try { r1 = arg1.toString().split(".")[1].length; } catch (e) { r1 = 0; }
  try { r2 = arg2.toString().split(".")[1].length; } catch (e) { r2 = 0; }
  m = Math.pow(10, Math.max(r1, r2));
  return (FloatMul(arg1, m) + FloatMul(arg2, m)) / m;
}
//浮點數相減
function FloatSubtraction(arg1, arg2)
{
  var r1, r2, m, n;
  try { r1 = arg1.toString().split(".")[1].length } catch (e) { r1 = 0 }
  try { r2 = arg2.toString().split(".")[1].length } catch (e) { r2 = 0 }
  m = Math.pow(10, Math.max(r1, r2));
  n = (r1 >= r2) ? r1 : r2;
  return ((arg1 * m - arg2 * m) / m).toFixed(n);
}
//浮點數相乘
function FloatMul(arg1, arg2)
{
  var m = 0, s1 = arg1.toString(), s2 = arg2.toString();
  try { m += s1.split(".")[1].length; } catch (e) { }
  try { m += s2.split(".")[1].length; } catch (e) { }
  return Number(s1.replace(".", "")) * Number(s2.replace(".", "")) / Math.pow(10, m);
}
//浮點數相除
function FloatDiv(arg1, arg2)
{
  var t1 = 0, t2 = 0, r1, r2;
  try { t1 = arg1.toString().split(".")[1].length } catch (e) { }
  try { t2 = arg2.toString().split(".")[1].length } catch (e) { }
  with (Math)
  {
    r1 = Number(arg1.toString().replace(".", ""))
    r2 = Number(arg2.toString().replace(".", ""))
    return (r1 / r2) * pow(10, t2 - t1);
  }
}
```
<=================================================================><br>
<a id="c25" href="#top">轉換溫度(零式與攝氏):</a>
```
<p><input id="c" onkeyup="convert('C')"> degrees Celsius</p>

<p><input id="f" onkeyup="convert('F')"> degrees Fahrenheit</p> 

<script>
function convert(degree) {
    var x;
    if (degree == "C") {
        x = document.getElementById("c").value * 9 / 5 + 32;
        document.getElementById("f").value = Math.round(x);
    } else {
        x = (document.getElementById("f").value -32) * 5 / 9;
        document.getElementById("c").value = Math.round(x);
    }
}
</script>
```
<===============================================================><br>
<a id="c26" href="#top">跳轉頁面:</a>
```
history.go() 方法可以用來明確指定瀏覽器要回去幾頁。

語法：

history.go(relativePosition);
參數 relativePosition 是一個數字，表示相對於當前頁面，要往上幾頁 (負數) 或往下幾頁 (正數)。

用法：

// 回上一頁，跟 history.back() 一樣意思
history.go(-1);

// 回下一頁，跟 history.forward() 一樣意思
history.go(1);

// 往回兩頁
history.go(-2);
```
<===================================================================><br>
<a id="c27" href="#top">window(self,top,parent)知識</a>
```
window.self

功能：是对当前窗口自身的引用。它和window属性是等价的。
语法：window.self
注：window、self、window.self是等价的。

window.top

功能：返回顶层窗口，即浏览器窗口。
语法：window.top
注：如果窗口本身就是顶层窗口，top属性返回的是对自身的引用。

window.parent

功能：返回父窗口。
语法：window.parent
注：如果窗口本身是顶层窗口，parent属性返回的是对自身的引用。
在框架网页中，一般父窗口就是顶层窗口，但如果框架中还有框架，父窗口和顶层窗口就不一定相同了。

判断当前窗口是否在一个框架中(或指:當前窗口是否寫在別的html檔裡面)：

<script type="text/javascript">
var b = window.top!=window.self;
document.write( "当前窗口是否在一个框架中："+b );
</script>
```
<===================================================================><br>
<a id="c28" href="#top">javascript:讀取文字檔檔案</a>
```
You need to check for status 0 
(as when loading files locally with XMLHttpRequest, you don't get a status returned because it's not from a Webserver)

function readTextFile(file)
{
    var rawFile = new XMLHttpRequest();
    rawFile.open("GET", file, false);
    rawFile.onreadystatechange = function ()
    {
        if(rawFile.readyState === 4)
        {
            if(rawFile.status === 200 || rawFile.status == 0)
            {
                var allText = rawFile.responseText;
                alert(allText);
            }
        }
    }
    rawFile.send(null);
}
And specify file:// in your filename:

readTextFile("file:///C:/your/path/to/file.txt");
```
<===================================================================><br>
<a id="c29" href="#top">javascript:製作基本頁籤</a>
```
<!DOCTYPE html PUBLIC "-//W3C//DTD XHTML 1.0 Transitional//EN" "http://www.w3.org/TR/xhtml1/DTD/xhtml1-transitional.dtd">
<html xmlns="http://www.w3.org/1999/xhtml">
<head runat="server">
    <title>JavascriptTab</title>
    <style type="text/css">
    .tab
    {
        border-right: black thin solid;
        border-top: black thin solid;
        border-left: black thin solid;
        border-bottom: black thin solid;
        width:200px;
        height:200px;
    }
    </style>
</head>
<body>
    <form id="form1" runat="server">
        <div id="Group1">
            <a href='#' onclick='ClickTab("0")'>tab1</a>
            <a href='#' onclick='ClickTab("1")'>tab2</a>
            <a href='#' onclick='ClickTab("2")'>tab3</a> (利用Click換頁)
	    <div id='G1Div0' style="display: block" class="tab">
                puma</div>
            <div id='G1Div1' style="display: none" class="tab">
                F6 Team</div>
            <div id='G1Div2' style="display: none" class="tab">
                Dotblogs</div>
        </div>
        <div id="Group2">
            <a href='#' onmouseover='MouseOverTab("0")'>tab1</a>
            <a href='#' onmouseover='MouseOverTab("1")'>tab2</a>
            <a href='#' onmouseover='MouseOverTab("2")'>tab3</a> (利用MouseOver換頁)<div id='G2Div0' style="display: block" class="tab">
                puma</div>
            <div id='G2Div1' style="display: none" class="tab">
                F6 Team</div>
            <div id='G2Div2' style="display: none" class="tab">
                Dotblogs</div>
        </div>
    </form>
</body>
</html>
<script type="text/javascript">
//onclick做法
function ClickTab(Index)
{    
    var child = document.getElementById("Group1").getElementsByTagName("div");
    for (var i=0;i<child.length;i++)
    {
        //將所有div不顯示
        child[i].style.display="none";
    }    
    document.getElementById("G1Div"+Index).style.display="block";//顯示指定的區塊
}
//mouseover做法
function MouseOverTab(Index)
{    
    var child = document.getElementById("Group2").getElementsByTagName("div");
    for (var i=0;i<child.length;i++)
    {
        child[i].style.display="none";
    }    
    document.getElementById("G2Div"+Index).style.display="block";
}
</script>
```
<===================================================================><br>
<a id="c30" href="#top">fullcalendar使用範例</a>
```
<!DOCTYPE html>
<html>
<head>
	<meta charset="utf-8">
	<meta name="viewport" content="width=device-width">
	<title>JS Bin</title>
	<!-- jQuery v1.9.1 -->
	<script type="text/javascript" src="https://code.jquery.com/jquery-1.9.1.min.js"></script>
	<!-- Moment.js v2.20.0 -->
	<script type="text/javascript" src="https://cdnjs.cloudflare.com/ajax/libs/moment.js/2.20.0/moment.min.js"></script>
	<!-- FullCalendar v3.8.1 -->
	<link href="https://cdnjs.cloudflare.com/ajax/libs/fullcalendar/3.8.1/fullcalendar.min.css" rel="stylesheet"  />
	<link href="https://cdnjs.cloudflare.com/ajax/libs/fullcalendar/3.8.1/fullcalendar.print.css" rel="stylesheet" media="print"></script>
	<script type="text/javascript" src="https://cdnjs.cloudflare.com/ajax/libs/fullcalendar/3.8.1/fullcalendar.min.js"></script>
</head>
<body>
	<div id="example"></div>
	<script>
		$( "#example" ).fullCalendar({
			// 參數設定[註1]
			header: { // 頂部排版
				left: "prev,next today", // 左邊放置上一頁、下一頁和今天
				center: "title", // 中間放置標題
				right: "month,basicWeek,basicDay" // 右邊放置月、周、天
			},
			defaultDate: "2018-02-12", // 起始日期
			weekends: true, // 顯示星期六跟星期日
			editable: true,  // 啟動拖曳調整日期
			events: [ 
				{ // 事件(包含開始時間)
					title: "中餐",
					start: "2018-02-12T12:00:00"
				},
				{ // 事件(包含跨日開始時間、結束時間)
					title: "音樂節",
					start: "2018-02-07",
					end: "2018-02-10"
				},
				{ // 事件(包含開始時間、結束時間)
					title: "會議",
					start: "2018-02-12T10:30:00",
					end: "2018-02-12T12:30:00"
				},
				{ // 事件(設定連結)
					title: "Click for Google",
					url: "http://google.com/",
					start: "2018-02-28"
				}
			]
		});
	</script>
</body>
</html>
```
