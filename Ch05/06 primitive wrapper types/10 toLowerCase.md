### 字符串大小写转换方法

接下来我们要介绍的是一组与大小写转换有关的方法。  

ECMAScript 中涉及字符串大小写转换的方法有 4 个：   

toLowerCase()、toLocaleLowerCase()、toUpperCase() 和 toLocaleUpperCase()。  

其中，toLowerCase() 和 toUpperCase() 是两个经典的方法，借鉴自 java.lang.String 中的同名方法。  

而 toLocaleLowerCase() 和 toLocaleUpperCase() 方法则是针对特定地区的实现。  

对有些地区来说，针对地区的方法与其通用方法得到的结果相同，  
但少数语言(如土耳其语) 会为 Unicode 大小写转换应用特殊的规则，  
这时候就必须使用针对地区的方法来保证实现正确的转换。以下是几个例子。

	var stringValue = "hello world";
    alert(stringValue.toLocaleUpperCase());   // "HELLO WORLD"
    alert(stringValue.toUpperCase());   // "HELLO WORLD"
    alert(stringValue.toLocaleLowerCase());   // "hello world"
    alert(stringValue.toLowerCase());   // "hello world"  

以上代码调用的 toLocaleUpperCase() 和 toUpperCase() 都返回了 "HELLO WORLD"，  
就像调用 toLocaleLowerCase() 和 toLowerCase() 都返回 "hello world" 一样。  

一般来说，在不知道自己的代码将在哪种语言环境中运行的情况下，还是使用针对地区的方法更稳妥一些。  

