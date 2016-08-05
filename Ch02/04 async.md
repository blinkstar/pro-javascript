### 异步脚本

HTML5为\<script\>元素定义了`async`属性。这个属性与`defer`属性类似，都用于改变处理脚本的行为。  

同样与`defer`类似，`async`只适用于外部脚本文件，并告诉浏览器立即下载文件。  

但与`defer`不同的是，标记为`async`的脚本**并不保证按照指定它们的先后顺序执行**。例如：  

	<!doctype html>
	<html>
		<head>
			<title>Example HTML Page</title>
			<script type="text/javascript" async src="example1.js"></script>
			<script type="text/javascript" async src="example2.js"></script>
		</head>
		<body>
			<!-- 这里放内容 -->
		</body>
	</html>	 
     
在以上代码中，第二个脚本文件可能会在第一个脚本文件之前执行。  

因此，确保**两者之间互不依赖**非常重要。  

指定`async`属性的目的是  --  **不让页面等待两个脚本下载和执行，从而异步加载页面其他内容**。 为此，建议异步脚本不要在加载期间修改DOM。  
    

异步脚本一定会在页面的**load事件前执行**，但可能会在**DOMContentLoaded事件触发之前或之后执行**。    
(DOMContentLoaded -- async -- load)  

支持异步脚本的浏览器有Firefox3.6、Safari 5和Chrome。  

在XHTML文档中，要把`async`属性设置为 `async="async"`。  


