### RegExp 构造函数属性

RegExp 构造函数包含一些属性(这些属性在其他语言中被看成是静态属性)。  
这些属性适用于作用域中的所有正则表达式，并且基于所执行的最近一次正则表达式操作而变化。  
关于这些属性的另一个独特之处，就是可以通过两种方式访问它们。  
换句话说，这些属性分别有一个长属性名和一个短属性名(Opera是例外，它不支持短属性名)。  
下表列出了 RegExp 构造函数的属性。

<table>
	<thead>
		<tr><th>长属性名</th><th>短属性名</th><th>说明</th></tr>
	</thead>
	<tbody>
		<tr><td>input</td><td>$_</td><td>最近一次要匹配的字符串。Opera 未实现此属性</td></tr>
		<tr><td>lastMatch</td><td>$&</td><td>最近一次的匹配项。Opera 未实现此属性</td></tr>
		<tr><td>lastParen</td><td>$+</td><td>最近一次匹配的捕获组。Opera 未实现此属性</td></tr>
		<tr><td>leftContext</td><td>$`</td><td>input 字符串中 lastMatch 之前的文本</td></tr>
		<tr><td>multiline</td><td>$*</td><td>布尔值，表示是否所有表达式都使用多行模式。IE 和 Opera 未实现此属性</td></tr>
		<tr><td>rightContext</td><td>$'</td><td>input 字符串中 lastMatch 之后的文本</td></tr>
	</tbody>
</table>

使用这些属性可以从 `exec()` 或 `test()` 执行的操作中提取出更具体的信息。  
请看下面的例子。

	var text = "this has been a short summer";
    var pattern = /(.)hort/g;
    // 注意：Opera 不支持 input、lastMatch、lastParen 和 multiline 属性。
    // Internet Explorer 不支持 multiline 属性
    if(pattern.test(text)){         // true
    	alert(RegExp.input);        // this has been a short summer
        alert(RegExp.leftContent);  // this has been a
        alert(RegExp.rightContent); // summer
        alert(RegExp.lastMatch);    // short
        alert(RegExp.lastParen);    // s
        alert(RegExp.multiline);    // false
     }

以上代码创建了一个模式，匹配任何一个字符后跟 hort ，而且把第一个字符放在了一个捕获组中。  
RegExp 构造函数的各个属性返回了下列值：
 - input  属性返回了原始字符串；
 - leftContext 属性返回了单词 short 之前的字符串，而rightContext 属性则返回了 short 之后的字符串；
 - lastMatch 属性返回最近一次与整个正则表达式匹配的字符串，即 short
 - lastParen 属性返回最近一次匹配的捕获组，即例子中的 s

如前所述，例子使用的长属性名都可以用相应的短属性名来代替。  
只不过，由于这些短属性名**大都不是有效的ECMAScript标识符**，  
因此必须通过方括号语法来访问它们，如下所示。

	var text = "this has been a short summer";
    var pattern = /(.)hort/g; 
    // 注意：Opera 不支持 input、lastMatch、lastParen 和 multiline 属性。
    // Internet Explorer 不支持 multiline 属性
    if(pattern.test(text)){
    	alert(RegExp.$_);     // this has been a short summer
        alert(RegExp["$`"]);  // this has been a
        alert(RegExp["$'"]);  // summer
        alert(RegExp["$&"]);  // short
        alert(RegExp["$+"]);  // s
        alert(RegExp["$*"]);  // false
    }

除了上面介绍的几个属性之外，还有多达9个用于存储捕获组的构造函数属性。  
访问这些属性的语法是 RegExp.$1、RegExp.$2 ..... RegExp.$9，  
分别用于存储第一、第二.....第九个匹配的捕获组。  
在调用 `exec()` 或 `test()` 方法时，这些属性会被自动填充。  
然后，我们就可以像下面这样来使用它们。

	var text = "this has been a short summer";
    var pattern = /(..)or(.)/g;
    if(pattern.test(text)){  
    	alert(RegExp.$1);    // sh
        alert(RegExp.$2);    // t
    }

这里创建了一个包含两个捕获组的模式，并用该模式测试了一个字符串。  
即使 `test()` 方法只返回一个布尔值，但`RegExp`构造函数的属性   
$1 和 $2 也会被匹配相应捕获组的字符串自动填充。

