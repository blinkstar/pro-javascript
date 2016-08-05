## 数据类型

`ECMAScript`中有5种简单数据类型(也称为基本数据类型)：`Undefined`、`Null`、`Boolean`、`Number`和`String`。  
还有1种复杂数据类型--`Object`，`Object`本质上是由一组无序的名值对组成的。  
`ECMAScript`不支持任何创建自定义类型的机制，而所有值最终都将是上述6种数据类型之一。  

乍一看，好像只有6种数据类型不足以表示所有数据；  
但是，由于`ECMAScript`数据类型具有动态性，因此的确没有再定义其他数据类型的必要了。  

### typeof 操作符

鉴于`ECMAScript`是松散类型的，因此需要有一种手段来检测给定变量的数据类型 -- `typeof` 就是负责提供这方面信息的操作符。  

对一个值使用 `typeof` 操作符可能返回下列某个**字符串**：

 - "undefined"  -- 如果这个值未定义；
 - "boolean" -- 如果这个值是布尔值；
 - "string" -- 如果这个值是字符串；
 - "number" -- 如果这个值是数值；
 - "object" -- 如果这个值是对象或 **null**;
 - "function" -- 如果这个值是函数。  

下面是几个使用 `typeof` 操作符的例子：  

	var message = "some string";
    alert(typeof message);   // "string"
    alert(typeof (message)); // "string"
	alert(typeof 95);    // "number"

这几个例子说明，`typeof`操作符的操作数可以是变量 `(message)` ，也可以是数值字面量。  

注意，`typeof` **是一个操作符而不是函数**，因此例子中的圆括号尽管可以使用，但不是必需的。  

有些时候，`typeof` 操作符会返回一些令人迷惑但技术上却正确的值。  
比如，调用 `typeof null` 会返回 `"object"` ，因为特殊值 `null` 被认为是一个**空的对象引用**。    

Safari 5 及之前版本、Chrome 7及之前版本在对正则表达式调用 `typeof` 操作符时会返回 `"function"` ，  
而其他浏览器在这种情况下会返回 `"object"` 。  

从技术角度讲，函数在ECMAScript中是对象，不是一种数据类型。  
然而，函数也确实有一些特殊的属性，因此通过`typeof`操作符来**区分函数和其他对象**是有必要的。  



