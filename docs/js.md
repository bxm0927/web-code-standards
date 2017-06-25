
# JS 规范

## 语法

使用四个空格的缩进，这是保证代码在各种环境下显示一致的唯一方式。

声明之后一律以分号结束， 不可以省略

完全避免 == != 的使用， 用严格比较条件 === !==

eval 非特殊情况， 禁用！！！

with 非特殊情况， 禁用！！！

单行长度，理论上不要超过80列，不过如果编辑器开启"自动换行"的话可以不考虑单行长度

接上一条，如果需要换行，存在操作符的情况，一定在操作符后换行，然后换的行缩进4个空格

这里要注意，如果是多次换行的话就没有必要继续缩进了，比如说下面这种就是最佳格式。

```
if (typeof qqfind === "undefined" ||
    typeof qqfind.cdnrejected === "undefined" ||
    qqfind.cdnrejected !== true) {
    url = "http://pub.idqqimg.com/qqfind/js/location4.js";
} else {
    url = "http://find.qq.com/js/location4.js";
}
```

## 空行

方法之间加

单行或多行注释前加

逻辑块之间加空行增加可读性

## 变量命名

标准变量采用驼峰标识

使用的ID的地方一定全大写

使用的URL的地方一定全大写, 比如说 reportURL

涉及Android的，一律大写第一个字母

涉及iOS的，一律小写第一个，大写后两个字母

常量采用大写字母，下划线连接的方式

构造函数，大写第一个字母

```
var thisIsMyName;

var goodID;

var AndroidVersion;

var iOSVersion;

var MAX_COUNT = 10;

function Person(name) {
    this.name = name
}
```

## 字符常量

一般情况下统一使用单引号

## null的使用场景

初始化可能以后分配对象值的变量

与一个可能或可能没有对象值的初始化变量进行比较

传入一个预期对象的函数

从预期对象的函数返回

## 不适合null的使用场景

不要使用null来测试是否提供参数

不要测试值为null的未初始化变量

## undefined使用场景

永远不要直接使用undefined进行变量判断

使用字符串 "undefined" 对变量进行判断

```
// Bad
var person;
console.log(person === undefined);    //true

// Good
console.log(typeof person);    // "undefined"
```

## 对象字面量

```
// Bad
var team = new Team();
team.title = "AlloyTeam";
team.count = 25;

// Good
var team = {
    title: "AlloyTeam",
    count: 25
};
```

## 数组声明

```
// Bad
var colors = new Array("red", "green", "blue");
var numbers = new Array(1, 2, 3, 4);


// Good
var colors = [ "red", "green", "blue" ];
var numbers = [ 1, 2, 3, 4 ];
```

## 单行注释

双斜线后，必须跟注释内容保留一个空格

与下一行代码缩进保持一致

可位于一个代码行的末尾，双斜线距离分号四个空格

```
// Good
if (condition) {
    // if you made it here, then all security checks passed
    allowed();
}

var zhangsan = "zhangsan";    // 双斜线距离分号四个空格，双斜线后始终保留一个空格
```

## 多行注释格式

最少三行

前边留空一行

```
/**
 * 注释内容与星标前保留一个空格
 */
```

## 何时使用多行注释格式

难于理解的代码段

可能存在错误的代码段

浏览器特殊的HACK代码

业务逻辑强相关的代码

想吐槽的产品逻辑, 合作同事

## 文档注释

各类标签 @param @method 等 参考 http://usejsdoc.org/

用于：方法、构造函数、对象

```
/**
 * here boy, look here , here is girl
 * @method lookGril
 * @param {Object} balabalabala
 * @return {Object} balabalabala
 */
```

## 括号对齐

标准示例 括号前后有空格，花括号起始不另换行，结尾新起一行

花括号必须要，即使内容只有一行

涉及 if for while do...while try...catch...finally 的地方都必须使用花括号，即使内容只有一行

## if else 前后留有空格

```
if (condition) {
    doSomething();
} else {
    doSomethingElse();
}
```

## switch

switch和括号之间有空格，case需要缩进，break之后跟下一个case中间留一个空白行

花括号必须要， 即使内容只有一行。

switch 的 falling through 一定要有注释特别说明，no default 的情况也需要注释特别说明况

```
switch (condition) {
    case "first":
        // code
        break;

    case "second":
        // code
        break;

    default:
    // code
}
```

## for

普通for循环, 分号后留有一个空格， 判断条件等内的操作符两边不留空格

前置条件如果有多个，逗号后留一个空格

for-in 一定要有 hasOwnProperty 的判断， 否则 JSLint 或者 JSHint 都会有一个 warn

```
for (i=0, len=values.length; i<len; i++) {
    process(values[i]);
}


var prop;

for (prop in object) {
    // 注意这里一定要有 hasOwnProperty 的判断， 否则 JSLint 或者 JSHint 都会有一个 warn ！
    if (object.hasOwnProperty(prop)) {
        console.log("Property name is " + prop);
        console.log("Property value is " + object[prop]);
    }
}
```

## 变量声明

所有函数内变量声明放在函数内头部，只使用一个 var(多了JSLint报错)， 一个变量一行， 在行末跟注释， 注释啊，注释啊，亲

## 函数声明

一定先声明再使用， 不要利用 JavaScript engine的变量提升特性, 违反了这个规则 JSLint 和 JSHint都会报 warn

function declaration 和 function expression 的不同，function expression 的（）前后必须有空格，而function declaration 在有函数名的时候不需要空格，没有函数名的时候需要空格。

函数调用括号前后不需要空格

立即执行函数的写法, 最外层必须包一层括号

"use strict" 决不允许全局使用， 必须放在函数的第一行， 可以用自执行函数包含大的代码段, 如果 "use strict" 在函数外使用， JSLint 和 JSHint 均会报错

```
function doSomething(item) {
    // do something
}

var doSomething = function (item) {
    // do something
}


// Good
doSomething(item);

// Bad: Looks like a block statement
doSomething (item);

// Good
(function() {
    "use strict";

    function doSomething() {
        // code
    }
})();
```
