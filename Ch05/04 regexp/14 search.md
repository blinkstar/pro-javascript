### 用于模式匹配的 String 方法

到目前为止，尽管已经讨论过创建正则表达式的语法，但还没有尝试过如何在 JavaScript 代码中使用这些正则表达式。  
本节将讨论 `String` 对象的一些用以执行正则表达式模式匹配和检索替换操作的方法，  
后续几节还会继续讨论如何使用 `JavaScript` 正则表达式的模式匹配，  
不过将侧重于 `RegExp` 对象和它的方法及属性。  
注意，下面的讨论只是与正则表达式相关的方法和属性的概述。

String 支持4种使用正则表达式的方法。

<table>
	<thead>
		<tr><th>方法</th><th>是否自动将字符串转为正则</th><th>是否支持g</th></tr>
	</thead>
	<tbody>
		<tr><td>search</td><td>转</td><td>不支持</td></tr>
		<tr><td>replace</td><td>不转</td><td>支持</td></tr>
		<tr><td>match</td><td>转</td><td>支持</td></tr>
		<tr><td>split</td><td>不转</td><td>不支持</td></tr>
	</tbody>
</table>

	var s = "This is a \\s match test.";
	
	console.log(s);
	
	console.log(s.search(/\s/));
	console.log(s.search("\\s"));
	
	console.log(s.replace(/\s/, "*"));
	console.log(s.replace("\\s","*"));
	
	console.log(s.match(/\s/));
	console.log(s.match("\\s"));
	
	console.log(s.split(/\s/));
	console.log(s.match("\\s"));
	

#### search

最简单的是 `search()`。  

它的**参数是一个正则表达式**，返回第一个与之匹配的子串的**起始位置**，如果找不到匹配的子串，它将返回 -1 。  
比如，下面的调用返回值为 4：

	"JavaScript".search(/script/i);

如果 `search()` 的参数**不是正则表达式**，则首先**会通过 RegExp 构造函数将它转换成正则表达式**，  

`search()` 方法**不支持全局检索**，因为它**忽略**正则表达式参数中的修饰符 `g` 。 


