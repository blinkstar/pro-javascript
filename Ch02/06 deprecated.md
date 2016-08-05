### 不推荐使用的语法

在最早引入\<script\>元素的时候，该元素与传统`HTML`的解析规则是有冲突的。  
由于要对这个元素应用特殊的解析规则，因此在那些不支持JavaScript的浏览器(最典型的是Mosaic)中就会导致问题。  
具体来说，不支持JavaScript的浏览器会把\<script\>元素的内容直接输出到页面中，因而会破坏页面的布局和外观。  

Netscape与Mosaic协商并提出了一个解决方案，让不支持\<script\>元素的浏览器能够隐藏嵌入的JavaScript代码。  
这个方案就是把JavaScript代码包含在一个`HTML`注释中，像下面这样：

	<script><!--
		function sayHi(){
			alert('Hi!');
		}
	//--></script>    
	 
给脚本加入`HTML`注释后，Mosaic等浏览器就会忽略\<script\>标签中的内容；  
而那些支持JavaScript的浏览器在遇到这种情况时，则必须进一步确认其中是否包含需要解析的JavaScript代码。  
     
虽然这种注释JavaScript代码的格式得到了所有浏览器的认可，也能被正确解释，**但由于所有浏览器都已经支持JavaScript，因此也就没有必要再使用这种格式了**。  

在XHMTL模式下，因为脚本包含在XML注释中，所以脚本会被忽略。


