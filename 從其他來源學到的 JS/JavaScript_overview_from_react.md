# JavaScript

* Number （數字）
* String （字串）
* Boolean （布林）
* Object （物件）
    * Function （函式）
    * Array （陣列）
    * Date （日期）
    * RegExp
* Null （空）
* Undefined （未定義）

## Number
數字算是「雙精確度 64 位元格式 IEEE 754 值」，因此沒有整數
```JS
0.1 + 0.2 = 0.30000000000000004
```

```JS
> parseInt("123", 10)
123
> parseInt("010", 10)
10
> parseInt("11", 2)
3
> parseInt("hello", 10)
NaN
```

NaN =  Not a Number

```JS
> NaN + 5
NaN
> isNaN(NaN)
true
> 1 / 0
Infinity
> -1 / 0
-Infinity

```

## String
```JS
> "hello".length
5
```

```JS
> "hello".charAt(0) //位置 0 的字元
h
> "hello, world".replace("hello", "goodbye") //把 hello 換成 goodbye
goodbye, world
> "hello".toUpperCase() //轉成大寫
HELLO

```

布林 (boolean) 
1. false、0、空字串 ("")、NaN、null、以及 undefined 都會成為 false
2. 所有其他的值都會成為 true
```JS
> Boolean("")
false
> Boolean(234)
true
```

運算子
```JS
> "hello" + " world"
hello world
```
如果你把一字串加到一個數字（或其他數值），會先把所有的東西轉成字串。這會讓你意想不到
```JS
> "3" + 4 + 5
345
> 3 + 4 + "5"
75
```
把一個空字串加到一個東西是個將其轉成字串的好方法之一。


雙等號運算子（等於）會進行型態強制轉換
```JS
> "dog" == "dog"
true
> 1 == true
true
```

要避免型態強制轉換，要用三等號運算子（絕對等於）：
```JS
> 1 === true
false
> true === true
true
```

判斷句
```JS
var name = "貓咪";
if (name == "狗狗") {
    name += "!";
} 
else if (name == "貓咪") {
    name += "!!";
} 
else {
    name = "!" + name;
}
name == "貓咪!!";
```


do...while：使用了do...while迴圈來持續讀取輸入，直到輸入符合指定的條件為止
```JS
while (true) {
  // 無限迴圈！
}

do {
  var input = get_input();
} while (inputIsNotValid(input));
```
在輸入有效之前，會一直重複 do 迴圈
inputIsNotValid 輸入無效，所以一但輸入有效， inputIsNotValid 就會回傳 false，然後取消迴圈


for 迴圈
```JS
for (var i=0; i<5; i++){
  // 會執行 5 次
}
```

三元運算子 (if 判斷式的縮寫)
```JS
a ? b : c
> a 如果是 ture 就執行 b，否則執行 c
```

switch 判斷式
```JS
switch (action){
  case "畫":
    draw();
    break;
  case "吃":
    eat();
    break;
  default:
    DoNoThing();
}
```

如果不加中斷
```JS
switch (a) {
  case 1:
  case 2:
    eatit(); //開始吃
    break; //中斷
  default: //預設
    donothing(); //不做任何事
}
```
如果 a 等於 1 或 2 的時候會執行 eatit 函式


## Object
建立空物件
```JS
var obj = Object();
```
or
```JS
var obj = {};
```

存取物件
```JS
obj.name = "小明";
var name = obj.name;
```

or 
```JS
obj["name"] = "小明"
var name = obj["name"]
```

```JS
obj.for = "Simon"; //語法錯誤
obj["for"] = "Simon"; //沒問題
```

`for` 是關鍵字，所以不能這樣用，而透過 `[]` 就可以允許所有字串的屬性名稱


```JS
var obj = {
  name: "胡蘿蔔", //名稱
  for: "小華", //給誰
  details: {
    //詳細資訊
    color: "橘", //顏色
    size: 12, //大小
  },
};
```
存取時也可以連在一起
```JS
obj.details.color
> 橘
obj["details"]["size"]
> 12
```


## Array
```JS
> var a = new Array();
> a[0] = "狗";
> a[1] = "貓";
> a[2] = "雞";
> a.length
3
```
array.length 就是最高索引數加一

```JS
> var a = ["狗", "貓", "雞"];
> a[100] = "狐";
> a.length
101
```

如果你查詢一個不存在的陣列索引，得到的就是 undefined：
```JS
> typeof(a[90])
undefined
```

陣列上做迴圈
```JS
for (var i = 0; i < a.length; i++) {
  //處理 a[i]
}
```
但這樣不是很有效率，因為每迴圈一次就會查詢一次 length 屬性。比較好的做法是：
```JS
for (var i = 0, len = a.length; i < len; i++) {
  //處理 a[i]
}
```


```JS
a[a.length] = item;  //同 a.push(item);
```
由於 a.length 一定是最高索引數加一，你可以很確定你指定到的是陣列結尾的空間。


## Method function
* toString
* toLocaleString
* concat 結合，會傳回加入了新項目的新陣列
* join
* pop 會移除最後一個項目並將其傳回
* push 會在結尾加入一或多個項目（就像前面提的 ar.length 方法）
* reverse
* shift
* slice 傳回副陣列
* sort 進行排序，可選擇性的接受「比較性函數」(comparison function)
* splice 讓你透過刪除一個區塊並以更多項目代替來修改陣列
* unshift 會在開頭加入一或多個項目

### toString
```JS
const array1 = [1, 2, 'a', '1a'];
console.log(array1.toString());
// Expected output: "1,2,a,1a"
```
陣列便字串的例子較為特別，會將每個元素用逗號連接起來

### toLocaleString
將陣列中元素本地化 (locate) 然後轉換成字串
```JS
// 日幣
let prices = ['300', 500, 8236, 42];
prices.toLocaleString('ja-JP',{style:'currency',currency: 'JPY'}); 
// "300,￥500,￥8,236,￥42"

// 新台幣
let prices = [300, 500, 8236, 42];
prices.toLocaleString('zh-TW',{style:'currency',currency: 'TWD'});
// "$300.00,$500.00,$8,236.00,$42.00"

// 法國歐元
let prices = ['300', 500, 8236, 42];
prices.toLocaleString('fr-FR',{style:'currency',currency: 'EUR'});
"300, 500,00 €, 8 236,00 €, 42,00 €" // 因為'300'是字串，所以會忽略。
```

### concat
```JS
const array1 = ['a', 'b', 'c'];
const array2 = ['d', 'e', 'f'];
const array3 = array1.concat(array2);

console.log(array3);
// Expected output: Array ["a", "b", "c", "d", "e", "f"]
```

### join
```JS
const elements = ['Fire', 'Air', 'Water'];

console.log(elements.join());
// Expected output: "Fire,Air,Water"

console.log(elements.join(''));
// Expected output: "FireAirWater"

console.log(elements.join('-'));
// Expected output: "Fire-Air-Water"
```


### pop
移除陣列中最後一個元素
```JS
const plants = ['broccoli', 'cauliflower', 'cabbage', 'kale', 'tomato'];

console.log(plants.pop());
// Expected output: "tomato"

console.log(plants);
// Expected output: Array ["broccoli", "cauliflower", "cabbage", "kale"]
```

### push
從陣列中最後加入
```JS
const animals = ['pigs', 'goats', 'sheep'];

const count = animals.push('cows');
console.log(count);
// Expected output: 4
console.log(animals);
// Expected output: Array ["pigs", "goats", "sheep", "cows"]
```

### reverse
反轉陣列
```JS
var a = ["one", "two", "three"];
var reversed = a.reverse();

console.log(a); // ['three', 'two', 'one']
console.log(reversed); // ['three', 'two', 'one']
```

在 JS 中，沒辦法直接反轉字串，但可以透過下面的方式操作
```JS
function reverseString(str) {
    // Step 1: 將字串轉換為陣列
    let strArray = str.split("");
    
    // Step 2: 反轉陣列
    let reversedArray = strArray.reverse();
    
    // Step 3: 將反轉後的陣列轉換回字串
    let reversedString = reversedArray.join("");
    
    return reversedString;
}

// 測試
let originalString = "hello";
let reversedString = reverseString(originalString);
console.log(reversedString); // "olleh"
```

第一步結果
```JS
let originalString = "hello";
let strArray = originalString.split("");
console.log(strArray);
> ["h", "e", "l", "l", "o"]
```

### shift
從頭去掉一個元素
```JS
const array1 = [1, 2, 3];

const firstElement = array1.shift();

console.log(array1);
// Expected output: Array [2, 3]

console.log(firstElement);
// Expected output: 1
```


### slice
不會改變原本陣列，會回傳一個新陣列，屬於淺拷貝
```JS
const animals = ['ant', 'bison', 'camel', 'duck', 'elephant'];

console.log(animals.slice(2));
// Expected output: Array ["camel", "duck", "elephant"]
//                            2       3         4

console.log(animals.slice(2, 4));
// Expected output: Array ["camel", "duck"]
//                            2        3

console.log(animals.slice(1, 5));
// Expected output: Array ["bison", "camel", "duck", "elephant"]
//                            1        2        3          4

console.log(animals.slice(-2));
// Expected output: Array ["duck", "elephant"]
//                           -2         -1

console.log(animals.slice(2, -1));
// Expected output: Array ["camel", "duck"]
//                            2        -2
```

### sort
```JS
const months = ['March', 'Jan', 'Feb', 'Dec'];
months.sort();
console.log(months);
// Expected output: Array ["Dec", "Feb", "Jan", "March"]

const array1 = [1, 30, 4, 21, 100000];
array1.sort();
console.log(array1);
// Expected output: Array [1, 100000, 21, 30, 4]
```


### splice
array.splice(start, deleteCount, item1, item2, ...)
* start: 指定要修改的起始位置的索引。
* deleteCount: 要刪除的元素數量。如果設置為 0，則不會刪除任何元素，但可以插入新元素。
* item1, item2, ...: 要插入到陣列中的新元素（可選）。
```JS
let array = [1, 2, 3, 4, 5];

// 從索引 2 開始刪除一個元素
array.splice(2, 1);
// 結果：array 為 [1, 2, 4, 5]

// 從索引 1 開始刪除兩個元素並插入新元素
array.splice(1, 2, 'a', 'b');
// 結果：array 為 [1, 'a', 'b', 4, 5]

// 從索引 2 開始刪除 0 個元素並插入新元素
array.splice(2, 0, 'x', 'y');
// 結果：array 為 [1, 'a', 'x', 'y', 'b', 4, 5]

// 刪除所有元素
array.splice(0);
// 結果：array 為 []
```


### unshift
可以加入一個或多個元素在陣列的開頭，然後會回傳陣列的長度
```JS
let array = [1, 2, 3, 4, 5];

// 使用 shift() 移除第一個元素
let shiftedElement = array.shift();
// 結果：shiftedElement 為 1，array 為 [2, 3, 4, 5]

// 使用 unshift() 在開頭添加一個元素
let newLength = array.unshift(0);
// 結果：newLength 為 5，array 為 [0, 2, 3, 4, 5]

// 使用 unshift() 在開頭添加多個元素
newLength = array.unshift(-2, -1);
// 結果：newLength 為 7，array 為 [-2, -1, 0, 2, 3, 4, 5]
```

## Function
```JS
function add(x, y) {
  var total = x + y;
  return total;
}
```

沒有傳入參數會回傳 NaN
```JS
> add()
NaN // undefined 不能進行加法
```

傳入過多參數，會忽略過多的參數
```JS
> add(2, 3, 4)
5 // 加了前兩數，不理 4
```

在函式中可以使用一個叫做 argument 的變數，用於表示所有傳入函式的變數
```JS
function add() {
    var sum = 0;
    for (var i = 0, j = arguments.length; i < j; i++) {
        sum += arguments[i];
    }
    return sum;
}

> add(2, 3, 4, 5)
14
```

如果是關於陣列的函式，使用 arr.length 來動態抓取長度
```JS
function avgArray(arr) {
    var sum = 0;
    for (var i = 0, j = arr.length; i < j; i++) {
        sum += arr[i];
    }
    return sum / arr.length;
}

> avgArray([2, 3, 4, 5])
3.5
```

### apply
這個函式可以將陣列動態傳入函式
舉例來說
```JS
function avg() {
    var sum = 0;
    for (var i = 0, j = arguments.length; i < j; i++) {
        sum += arguments[i];
    }
    return sum / arguments.length;
}
> avg(2, 3, 4, 5)
3.5
```
這個 avg 只能接受由逗號分隔的參數
那如果我們使用的是陣列
```JS
array = [2, 3, 4, 5]
> avg.apply(null, [2, 3, 4, 5])
> avg.apply(null, array)
3.5
```
我們就可以利用這種方式，將陣列動態變成函式可以接受的形式

apply 函數有兩個參數，第一個參數就是指 this


### 匿名函式
[匿名函式](https://realnewbie.com/front-end/anonymous-function/#ftoc-heading-6)

只需要不寫名字就是
```JS
function(參數1, 參數2, ...) {
  // 函數內容
  return 結果; // 可選
}
```

也可以 assign 給變數
```JS
let myFunction = function(x, y) {
  return x + y;
};
```
用法就跟一般函式相同
```JS
let result = myFunction(5, 3);
console.log(result); // 輸出 8
```

### 立即執行函式
```JS
(function() {
    var b = 3;
    a += b;
})();
```

`(function() { ... })`
這是一個匿名函式的函式表達式，用圓括號括起來。這樣做是為了將函式視為一個表達式，而不是一個聲明。這個匿名函式定義了一個私有作用域，其中的變數不會污染全局作用域。

`();` 最後的一對括號 () 是用來立即執行這個匿名函式的。這個括號結構讓這個函式立即被呼叫並執行。因為這個函式是在定義之後立即執行的，所以稱為立即執行函式 (IIFE)。

### 遞迴函式
```JS
function countChars(elm) {
  if (elm.nodeType == 3) {
    // TEXT_NODE
    return elm.nodeValue.length;
  }
  var count = 0;
  for (var i = 0, child; (child = elm.childNodes[i]); i++) {
    count += countChars(child);
  }
  return count;
}
```

在這個函式中，如果想要用匿名函式來寫，該如何呼叫自己
可以使用 `arguments.callee` 的屬性，來呼叫
```JS
var charsInBody = (function (elm) {
  if (elm.nodeType == 3) {
    // TEXT_NODE
    return elm.nodeValue.length;
  }
  var count = 0;
  for (var i = 0, child; (child = elm.childNodes[i]); i++) {
    count += arguments.callee(child);
  }
  return count;
})(document.body);
```

而且它會儲存被呼叫的資料
```JS
function counter() {
    if (!arguments.callee.count) {
        arguments.callee.count = 0;
    }
    return arguments.callee.count++;
}

> counter()
0
> counter()
1
> counter()
2
```


## 自訂物件

```JS
function makePerson(first, last) {
    return {
        first: first,
        last: last
    }
}
function personFullName(person) {
    return person.first + ' ' + person.last;
}
function personFullNameReversed(person) {
    return person.last + ', ' + person.first
}
> s = makePerson("Simon", "Willison");
> personFullName(s)
Simon Willison
> personFullNameReversed(s)
Willison, Simon
```

雖然這樣行得通，可是這樣很醜，在全域命名空間 (global namespace) 裡灑了一堆函式。我們需要把函式「附著」(attach) 到物件上。

```JS
function makePerson(first, last) {
    return {
        first: first,
        last: last,
        fullName: function() {
            return this.first + ' ' + this.last;
        },
        fullNameReversed: function() {
            return this.last + ', ' + this.first;
        }
    }
}
> s = makePerson("Simon", "Willison")
> s.fullName()
Simon Willison
> s.fullNameReversed()
Willison, Simon
```

```JS
function personFullName() {
  return this.first + " " + this.last;
}
function personFullNameReversed() {
  return this.last + ", " + this.first;
}
function Person(first, last) {
  this.first = first;
  this.last = last;
  this.fullName = personFullName;
  this.fullNameReversed = personFullNameReversed;
}
```

這樣的寫法就可以讓所有人共享 personFullName、personFullNameReversed 這兩個 function

```JS
> s = new Person("Simon", "Willison");
> s.firstNameCaps();
TypeError on line 1: s.firstNameCaps is not a function
> Person.prototype.firstNameCaps = function() {
    return this.first.toUpperCase()
}
> s.firstNameCaps()
SIMON
```

如果我們想要將某個不在 Person 中的函數，我們可以自己新增
語法使用 Name.prototype.FunctionName = funciton()
`Person.prototype.firstNameCaps = function()`

再舉一個例子
```JS
> var s = "Simon";
> s.reversed()
TypeError on line 1: s.reversed is not a function
> String.prototype.reversed = function() {
    var r = "";
    for (var i = this.length - 1; i >= 0; i--) {
        r += this[i];
    }
    return r;
}
> s.reversed()
nomiS
```

定義函數
```JS
function car(make, model, year) {
  this.make = make;
  this.model = model;
  this.year = year;
}
```
使用 new 建立物件，也可以建立多個物件
```JS
mycar = new car("Eagle", "Talon TSi", 1993);
kenscar = new car("Nissan", "300ZX", 1992);
vpgscar = new car("Mazda", "Miata", 1990);
```


## class
ES6 新引進的語法
```JS
class Person {
  constructor(name, age) {
    this.name = name;
    this.age = age;
  }

  greet() {
    console.log(`Hello, my name is ${this.name} and I am ${this.age} years old.`);
  }
}

const john = new Person("John", 30);
john.greet(); // "Hello, my name is John and I am 30 years old."
```
重點：`class Person{}`、`constructor`、`${this.name}`、`new Person()`

`...args`：ES6 引入的語法，表示該函數可以接收任意數量的參數，並將這些參數收集到一個陣列 args 中
```JS
function exampleFunction(...args) {
  console.log(args);
}

exampleFunction(1, 2, 3, 4); // [1, 2, 3, 4]
```

`constructor` 用於模擬 new 關鍵字創建新物件的行為

## 閉包
```JS
function makeAdder(a) {
    return function(b) {
        return a + b;
    }
}

x = makeAdder(5);   // x 是一個函數，這個函數接受一個參數 b 並返回 5 + b
y = makeAdder(20);  // y 是一個函數，這個函數接受一個參數 b 並返回 20 + b

x(6);  // 呼叫 x 函數並傳入 6，返回 5 + 6
y(7);  // 呼叫 y 函數並傳入 7，返回 20 + 7

```
計算結果
* x = makeAdder(5); 創建了一個函數 x，這個函數接受一個參數 b 並返回 5 + b。
* y = makeAdder(20); 創建了一個函數 y，這個函數接受一個參數 b 並返回 20 + b。
呼叫 x(6) 時，會計算 5 + 6，結果是 11。
呼叫 y(7) 時，會計算 20 + 7，結果是 27。
```JS
x(6);  // 返回 11
y(7);  // 返回 27
```

閉包：當內部函數想要使用外部變數時，就會產生閉包
1. 呼叫 `makeAdder(5)`：當 makeAdder(5) 被呼叫時，參數 a 被設置為 5。然後，makeAdder 返回一個匿名函數，這個函數接受一個參數 b 並返回 a + b。
2. 創建閉包：返回的匿名函數「記住」了 a 的值。這樣，匿名函數就成了一個閉包，並保存了 a 的值為 5。

## 記憶體流失
1. 取得 DOM 元素：

```JS
var el = document.getElementById("el");
```
這行程式碼從 DOM 中取得一個元素，並將其存儲在變數 el 中。

2. 創建一個物件並將元素引用存儲在物件中：

```JS
var o = { el: el };
```
這行程式碼創建了一個物件 o，其中包含對 el 元素的引用。

3. 創建一個循環引用：

```JS
el.o = o;
```
這行程式碼將物件 o 的引用存儲在 el 元素的屬性 o 中。

循環引用
在這裡，產生了一個循環引用：

* 物件 o 包含對 DOM 元素 el 的引用。
* DOM 元素 el 包含對物件 o 的引用。

### 如何解決
1. 手動清除
```JS
function leakMemory() {
  var el = document.getElementById("el");
  var o = { el: el };
  el.o = o;

  // 需要時清除引用以避免記憶體流失
  // el.o = null;
  // o.el = null;
}
```

2. 設定 timeout 時間
```JS
function leakMemory() {
  var el = document.getElementById("el");
  var o = { el: el };
  el.o = o;

  // 當確定不再需要這些物件時，清除引用
  setTimeout(() => {
    el.o = null;
    o.el = null;
  }, 0);
}
```

`setTimeout` 的第二個參數是延遲時間（以毫秒為單位），而設置為 0 表示這段代碼將在所有同步代碼執行完畢後立即執行。
具體來說，它會在當前的事件循環（event loop）完成之後、下一個事件循環開始之前執行。因此，雖然看起來像是「立即」執行，但它實際上是排隊等待下一個可用的執行時間點。

```JS
console.log("Start");

setTimeout(() => {
  console.log("Inside setTimeout");
}, 0);

console.log("End");
```
輸出結果
```JS
Start
End
Inside setTimeout
```