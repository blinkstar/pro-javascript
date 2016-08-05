### 使用\<script\>元素的方式有两种：直接在页面中嵌入JavaScript代码和包含外部JavaScript文件。

#### 在使用 \<script\> 元素嵌入 JavaScript 代码时，只须为 \<script\> 指定 `type` 属性。
	然后，像下面这样把 JavaScript 代码直接放在元素内部即可：
	
	<script type="text/javascript">
		function sayHi(){
			alert('Hi!');
		}
	</script>

包含在 \<script\> 元素内部的 JavaScript 代码将从上至下依次解释。就拿前面这个例子来说，解释器会解释到一个函数定义，然后将该定义保存在自己的环境当中。  

在解释器对 \<script\> 元素内部的所有代码求值完毕以前，页面中的其余内容**都不会被浏览器加载或显示**。

在使用 \<script\> 嵌入 JavaScript 代码时，记住不要在代码中的任何地方出现 `"</script>"` 字符串。

例如，浏览器在加载下面所示的代码时就会产生一个**错误**：  

	<script type="text/javascript">
		function sayScript(){
			alert("</script>");
		}
	</script>
	
因为按照解析嵌入式代码的规则，当浏览器遇到字符串`"</script>"`时，就会认为那是结束的`</script>`标签。  

而通过把这个字符串分隔为两部分可以解决这个问题，例如：	

	<script type="text/javascript">
		function sayScript(){
			alert("<\/script>")
		}
	</script>	
	
像这样分成两部分来写就不会造成浏览器的误解，因而也就不会导致错误了。	

#### 如果要通过\<script\>元素来包含外部JavaScript文件，那么src属性就是必需的。

这个属性的值是一个指向外部JavaScript文件的链接，例如：

	<script type="text/javascript" src="example.js"></script>
	
在这个例子中，外部文件`example.js`将被加载到当前页面中。
外部文件只须包含通常要放在开始的\<script\>和结束的\</script\>之间的那些JavaScript代码即可。

与解析嵌入式JavaScript代码一样，在解析外部JavaScript(**包括下载该文件**)时，**页面的处理也会暂时停止**。

如果是在`XHTML`文档中，也可以省略前面示例代码中结束的\</script\>标签，例如：

	<script type="text/javascript" src="example.js" />

但是，不能在`HTML`文档使用这种语法。原因是这种语法不符合HTML规范，而且也得不到某些浏览器(尤其是IE)的正确解析。

按照惯例，外部 JavaScript 文件带有 `.js` 扩展名。但这个扩展名不是必需的，因为**浏览器不会检查**包含 JavaScript 的文件的扩展名。  
这样一来，使用 `JSP` 、`PHP` 或其他服务器端语言动态生成 JavaScript 代码也就成为了可能。  
但是，**服务器**通常还是需要看扩展名决定为响应应用哪种MIME类型。  
如果不使用 `.js` 扩展名，请确保服务器能返回正确的 MIME 类型。
	
	
需要注意的是，带有`src`属性的\<script\>元素不应该在其\<script\>和\</script\>标签之间再包含额外的JavaScript代码。  
如果包含了嵌入的代码，则**只会下载并执行外部脚本文件，嵌入的代码会被忽略**。  	

另外，通过\<script\>元素的`src`属性还可以包含来自外部域的JavaScript文件。  
这一点既使\<script\>元素倍显强大，又让它备受争议。在这一点上，\<script\>与\<img\>元素非常相似，  
即它的`src`属性可以是指向当前HTML页面所在域之外的某个域中的URL，例如：  

	<script type="text/javascript" src="http://www.somewhere.com/afile.js"></script>

这样，位于外部域中的代码也会被加载和解析，就像这些代码位于加载它们的页面中一样。利用这一点就可以在必要时通过不同的域来提供JavaScript文件。  

无论如何包含代码，只要不存在`defer`和`async`属性，浏览器都会按照\<script\>元素**在页面中出现的先后顺序**对它们**依次**进行解析。  
换句话说，在第一个\<script\>元素包含的代码解析完成后，第二个\<script\>包含的代码才会被解析，然后才是第三个、第四个.....

