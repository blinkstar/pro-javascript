### 字符方法

两个用于访问字符串中特定字符的方法是 ： `charAt()` 和 `charCodeAt()` 。  

这两个方法都接收一个参数，即基于 0 的字符位置。

其中，`charAt()` 方法以单字符字符串的形式返回给定位置的那个字符 (ECMAScript 中没有字符类型)。例如：  

	var stringValue = "hello world";
    alert(stringValue.charAt(1));  // "e"

字符串 `"hello world"` 位置 1 处的字符是 `"e"` ，因此调用 `charAt(1)` 就返回了 `"e"` 。  

如果你想得到的不是字符而是字符编码，那么就要像下面这样使用 `charCodeAt()` 了 。  

	var stringValue = "hello world";
    alert(stringValue.charCodeAt(1));    // 输出 "101"

这个例子输出的是 `"101"` ，也就是小写字母 `"e"` 的字符编码。

ECMAScript 5 还定义了另一个访问个别字符的方法。  
在支持的浏览器中，可以使用**方括号加数字索引来访问字符串中的特定字符**，如下面的例子所示。   

	var stringValue = "hello world";
    alert(stringValue[1]);  // "e"

使用方括号表示法访问个别字符的语法得到了 IE8 及 Firefox 、Safari 、Chrome 和 Opera 所有版本的支持。  
如果是在 IE 7 及更早版本中使用这种语法，会返回 undefined 值 (尽管根本不是特殊的 undefined 值)。  

 
