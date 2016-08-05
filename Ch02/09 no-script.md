### \<noscript\>元素

早期浏览器都面临一个特殊的问题，即当浏览器不支持JavaScript时如何让页面平稳地退化。  
对这个问题的最终解决方案就是创造一个\<noscript\>元素，用以在不支持JavaScript的浏览器中显示替代的内容。  

这个元素可以包含能够出现在文档\<body\>中的任何`HTML`元素--\<script\>元素除外。  

包含在\<noscript\>元素中的内容只有在下列情况下才会显示出来：

 - 浏览器不支持脚本；
 - 浏览器支持脚本，但脚本被禁用。

符合上述任何一个条件，浏览器都会显示\<noscript\>中的内容。而在除此之外的其他情况下，浏览器不会呈现\<noscript\>中的内容。  
     
请看下面这个简单的例子：

	<!DOCTYPE html>
	<html>
		<head>
			<title>Example HTML Page</title>
			<script type=”text/javascript” defer=”defer” src=”example1.js”></script>
			<script type=”text/javascript” defer=”defer” src=”example2.js”></script>
		</head>
		<body>
			<noscript>
				<p>This page requires a JavaScript-enabled browser.</p>
			</noscript>
		</body>
	</html>  
	   
这个页面会在脚本无效的情况下向用户显示一条消息。而在启用了脚本的浏览器中，用户永远也不会看到它--尽管它是页面的一部分。



