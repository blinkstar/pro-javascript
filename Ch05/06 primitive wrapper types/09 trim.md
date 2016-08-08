### trim() 方法

ECMAScript 5 为所有字符串定义了 trim() 方法。  

这个方法会创建一个字符串的**副本**，删除前置及后缀的所有空格，然后返回结果。例如：

	var stringValue = "    hello world   ";
    var trimmedStringValue = stringValue.trim();
    alert(stringValue);      // "    hello world   "
    alert(trimmedStringValue);    // "hello world"

由于 trim() 返回的是字符串的副本，所以**原始字符串中的前置及后缀空格会保持不变**。  
支持这个方法的浏览器有 IE 9+、Firefox 3.5 + 、Safari 5 +、Opera 10.5+ 和 Chrome 。  
此外，Firefox 3.5+ 、Safari 5+ 和 Chrome 8 + 还支持非标准的 trimLeft() 和 trimRight() 方法，  
分别用于删除字符串开头和末尾的空格。

