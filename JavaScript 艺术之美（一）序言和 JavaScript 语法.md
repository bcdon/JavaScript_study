## 一、JavaScript 简史
百度百科很全，移步：[JavaScript 百度百科](https://baike.baidu.com/item/javascript/321142?fr=aladdin "JavaScript 百度百科")

## 二、在 HTML 中插入 JavaScript

    // 法1.直接使用
    <script>...</script>
    // 法2.使用外部文件
    <script src="myScript.js"></script>
    // 法3.老传统
    <script type="text/javascript">...</script>
- 现代浏览器以及 HTML5 中的默认脚本语言是 JavaScript，所以没必要设置 type="text/javascript"。
- script 标签可位于 HTML 的 body 或 head 部分，最好的做法是放在html文档最后，`</body>` 之前。

## 三、注释
    // 法1.单行注释
	/* 法2.多行注释第一行
		第二行 */
	<!-- 法3.html风格，单行注释，一般不推荐

## 四、变量
- 人们把那些会发生变化的东西称为变量，把值存入变量的操作称为赋值，使用 var 关键词来声明变量。
- JavaScript允许直接对变量赋值而无需事先声明，如果对某个变量赋值之前未声明，赋值操作将自动声明该变量。

```
// 变量声明
	var name1;
	var name2;
// 用一条语句一次声明多个变量
	var name1, name2;
// 先声明后赋值
	var name1, name2;
	name1 = "value1";
	name2 = "value2";
// 一石二鸟，声明同时赋值
	var name1 = "value1";
	var name2 = "value2";
// 也可以这样，最佳做法
	var name1 = "value1", name2 = "value2";
	

```
- 在JavaScript 里变量和其他语法元素的名字都是区分字母大小写的
- JavaScript 语法不允许变量名中包含空格或除美元符号"$"外的标点符号。
- JavaScript 变量名允许包含字母、数字、下划线和美元符号“$”，第一个字符不允许是数字，能以 $ 和 _ 符号开头（不过我们不推荐这么做）

### 驼峰式和下划线规范：
声明变量用下划线链接多个单词，函数名、方法名和对象属性名命名首选驼峰格式

## 五、数据类型
在声明变量的同时声明变量的数据类型，这种做法称为 类型声明，必须明确类型声明的语言称为强类型语言，JavaScript不需要进行类型声明，因此它是一种弱类型语言。
### 1.字符串
字符串由零个或多个字符构成，必须包在单引号或双引号内：
```
var mood = "happy";
var mood = 'happy';
```
有的情况下需要在字符串里对字符进行转义，在JavaScript里用反斜线对字符串进行转义：
```
var mood = 'don\'t ask';
```
### 2.数值
JavaScript 只有一种数字类型。数字可以带小数点(浮点数)，也可以不带(整数)：
```
var x1 = 34.00;        //使用小数点来写
var x2 = 34;              //不使用小数点来写
```
在有关数值的前面加上一个减号“-”表示他是一个负数：
```
var x1 = -34.00;          //负浮点数
var x2 = -34;             //负整数
```
极大或极小的数字可以通过科学（指数）计数法来书写：
```
var y = 123e5;             // 12300000
var z = 123e-5;           // 0.00123
```
### 3.布尔值
布尔（逻辑）只有两个可选值：true 或 false。
```
var x = true;
var y = false;
```
## 六、数组
数组是指用一个变量表示一个值的集合，集合中的每个值都是这个数组的一个元素。
数组可以用关键字 Array 声明，同时还可以指定数组初始元素个数（数组的长度）：
```
var my_array = Array(4);      //指定长度，不必须
var my_array1 = Array();      //不指定长度
```
向数组中添加元素操作称为填充：
```
var cars = new Array();
cars[0] = "Audi";    //数组的下标是从0开始计数的
cars[1] = "BMW";
cars[2] = "Volvo";
```
声明数组的同时对他进行填充，用逗号把各个元素隔开：
```
var cars = new Array("Audi","BMW","Volvo");
```
甚至用不着明确表明是在创建数组，需用一对方括号把各个元素的初始值括起来：
```
var cars = ["Audi","BMW","Volvo"];
```
数组元素不必非得是字符串：
```
var cars = ["Audi", 1998, false];   // 3种数据类型，依次为 字符串、数值、布尔值
// 还可以是变量
var name1 = "John";
cars[0] = name1;  // 把cars数组的第一个元素赋值为字符串"John"
// 数组元素的值还可以是另一个数组的元素
var name1 = ["Audi","BMW","Volvo"];
cars[1] = name1[2];      // 把name1数组的第3个元素值"Volvo"赋给cars的第二个元素

```
数组还可以包含其他数组，数组中的任何一个元素都可以把一个数组作为它的值：
```
var cars = ["Audi", 1998, false];
var name1 = [];
name1[0] = cars; // name1数组的第一个元素值是cars数组

```
通过name1数组获得cars数组里的某个元素：name1[0][0] 的值是字符串"Audi"，name1[0][1] 的值是数值 1998，name1[0][2] 的值是布尔值 false。
### 关联数组：
可以通过在填充数组时为每个新元素明确地给出下标来改变这种默认行为，在新元素给出下标时不必局限于使用整数数字，可以用字符串：
```
var cars = new Array();
cars["name"] = "Audi";
cars["year"] = 1998;
cars["living"] = false;
```
在JavaScript中，所有的变量实际上都是某种类型的对象。
## 七、对象
JavaScript 中的所有事物都是对象：字符串、数字、数组、日期，等等。对象是拥有属性和方法的数据，对象也是使用一个名字表示一组值，每个值都是对象的一个属性：
```
person=new Object();   // 创建对象使用Object关键字
person.firstname="Bill";  // 使用点号获取属性
person.lastname="Gates";
person.age=56;
person.eyecolor="blue";
```
花括号语法创建对象：
```
var person={firstname="Bill",lastname="Gates",age=56};
```
属性是与对象相关的值，方法是能够在对象上执行的动作。
下面用person对象填充cars数组,使用 cars[0].firstname得到值"Bill"：
```
var cars = new Array();
var person={firstname="Bill",lastname="Gates",age=56};
cars[0] = person;
```
下面将cars数组也声明为对象:
```
var cars = {};
var person={firstname="Bill",lastname="Gates",age=56};
cars.firstCars = person;

```
使用 cars.firstCars.firstname得到值"Bill",依次类推。
