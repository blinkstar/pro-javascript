### 在XHTML中的用法

可扩展超文本标记语言，即`XHTML(Extensible HyperText Markup Language)`，是将`HTML`作为`XML`的应用而重新定义的一个标准。  

编写`XHTML`代码的规则要比编写`HTML`严格得多，而且直接影响能否在嵌入JavaScript代码时使用\<script /\>标签。  
以下面的代码为例，虽然它们在`HTML`中是有效的，但在`XHTML`中则是无效的。  

	<script type="text/javascript">
		function compare(a, b){
			if(a < b){
				alert("A is less than B");
			}else if(a > b){
				alert("A is greater than B");
			}else {
				alert("A is equal to B");
			}
		}
	</script>
     
在`HTML`中，有特殊的规则用以确定\<script\>元素中的哪些内容可以被解析，但这些特殊的规则在`XHTML`中不适用。  

这里比较语句`a < b`中的小于号`(<)`在`XHMTL`中将被当作**开始一个新标签来解析**。但是作为标签来讲，小于号后面不能跟空格，因此就会导致语法错误。  
     
避免在XHTML中出现类似语法错误的方法有两个。  

一是用相应的`HTML`实体`(&lt;)`替换代码中所有的小于号`(<)`，替换后的代码类似如下所示：
    
    <script type="text/javascript">
		function compare(a, b){
			if(a &lt; b){
				alert("A is less than B");
			}else if(a > b){
				alert("A is greater than B");
			}else {
				alert("A is equal to B");
			}
		}
	</script>
	 
虽然这样可以让代码在`XHTML`中正常运行，但却导致代码不好理解了。为此，我们可以考虑采用另一个方法。  

保证让相同代码在`XHTML`中正常运行的第二个方法，就是用一个 `CData` 片段来包含 JavaScript 代码。  
在`XHTML(XML)`中，`CData` 片段是文档中的一个特殊区域，这个区域中可以包含不需要解析的任意格式的文本内容。  
因此，在`CData`片段中就可以使用任意字符--小于号当然也没有问题，而且不会导致语法错误。  
引入`CData`片段后的JavaScript代码块如下所示：
     
     <script type="text/javascript"><![CDATA[
		function compare(a, b){
			if(a < b){
				alert("A is less than B");
			}else if(a > b){
				alert("A is greater than B");
			}else {
				alert("A is equal to B");
			}
		}
	]]></script>
	
在兼容`XHTML`的浏览器中，这个方法可以解决问题。但实际上，还有不少浏览器不兼容`XHTML`，因此不支持 `CData` 片段。怎么办呢？  
再使用JavaScript注释将 CData 标记注释掉就可以了：
     
     <script type="text/javascript">
     //<![CDATA[
		function compare(a, b){
			if(a < b){
				alert("A is less than B");
			}else if(a > b){
				alert("A is greater than B");
			}else {
				alert("A is equal to B");
			}
		}
	//]]>
	</script>
     
这种格式在所有现代浏览器中都可以正常使用。虽然有几分 `hack` 的味道，但它能通过 `XHTML` 验证，而且对 `XHTML` 之前的浏览器也会平稳退化。  

在将页面的 `MIME` 类型指定为 `"application/xhtml+xml"` 的情况下会触发 `XHTML` 模式。并不是所有浏览器都支持以这种方式提供`XHMTL`文档。   


