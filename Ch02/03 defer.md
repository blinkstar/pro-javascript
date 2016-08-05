### 延迟脚本

HTML4.01为\<script\>标签定义了`defer`属性。这个属性的用途是表明脚本在执行时不会影响页面的构造。  
也就是说，**脚本会被延迟到整个页面都解析完毕后再运行**。  

因此，在\<script\>元素中设置`defer`属性，相当于告诉浏览器**立即下载，但延迟执行**。  

	<!doctype html>
	<html>
		<head>
			<title>Example HTML Page</title>
			<script type="text/javascript" defer="defer" src="example1.js"></script>
			<script type="text/javascript" defer="defer" src="example2.js"></script>
		</head>
		<body>
			<!-- 这里放内容 -->
		</body>
	</html>	
	
在这个例子中，虽然我们把\<script\>元素放在了文档的\<head\>元素中，但其中包含的脚本将延迟到浏览器遇到\</html\>标签后再执行。  

HTML5规范要求脚本按照它们出现的先后顺序执行，因此第一个延迟脚本会先于第二个延迟脚本执行，而这两个脚本会先于DOMContentLoaded事件执行。  
在现实当中，**延迟脚本并不一定会按照顺序执行，也不一定会在DOMContentLoaded事件触发前执行**，因此最好只包含一个延迟脚本。  


前面提到过，`defer`属性只适用于外部脚本文件。这一点在HTML5中已经明确规定，因此支持HTML5的实现会忽略给嵌入脚本设置的`defer`属性。  
IE4-IE7还支持对嵌入脚本的`defer`属性，但IE8及之后版本则完全支持HTML5规定的行为。  

IE4、Firefox3.5、Safari 5 和 Chrome 是最早支持`defer`属性的浏览器。其他浏览器会忽略这个属性，像平常一样处理脚本。    
为此，把延迟脚本放在页面底部仍然是最佳选择。  

在XHTML文档中，要把`defer`属性设置为 `defer="defer"`。  


