### 文档模式

IE5.5引入了文档模式的概念，而这个概念是通过使用文档类型`(doctype)`切换实现的。  

最初的两种文档模式是：混杂模式`(quirks mode)`和标准模式`(standards mode)`。  

混杂模式会让IE的行为与(包含非标准特性的)IE5相同，而标准模式则让IE的行为更接近标准行为。  

虽然这两种模式主要影响CSS内容的呈现，但在某些情况下也会影响到JavaScript的解释执行。  

在IE引入文档模式的概念后，其他浏览器也纷纷效仿。  

在此之后，IE又提出一种所谓的准标准模式`(almost standards mode)`。这种模式下的浏览器特性有很多都是符合标准的，但也不尽然。
不标准的地方主要体现在处理图片间隙的时候(在表格中使用图片时问题最明显)。  

如果在文档开始处没有发现文档类型声明，则所有浏览器都会默认开启混杂模式。
但采用混杂模式不是什么值得推荐的做法，因为不同浏览器在这种模式下的行为差异非常大，如果不使用某些`hack`技术，跨浏览器的行为根本就没有一致性可言。

对于标准模式，可以通过使用下面任何一种文档类型来开启：  

	<!-- HTML 4.01 Strict -->
	<!DOCTYPE HTML PUBLIC “-//W3C//DTD HTML 4.01//EN” “http://www.w3.org/TR/html4/strict.dtd”>
	
	<!-- XHTML 1.0 Strict -->
	<!DOCTYPE html PUBLIC “-//W3C//DTD XHTML 1.0 Strict//EN” “http://www.w3.org/TR/xhtml1/DTD/xhtml1-strict.dtd”>

	<!-- HTML5 -->
	<!DOCTYPE html>
     
而对于准标准模式，则可以通过使用过渡型`(transitional)`或框架集型`(framset)`文档类型来触发，如下所示：  

	<!-- HTML 4.01 Transitional -->
	<!DOCTYPE HTML PUBLIC “-//W3C//DTD HTML 4.01 Transitional//EN” “http://www.w3.org/TR/html4/loose.dtd”>
	
	<!-- HTML 4.01 Frameset -->
	<!DOCTYPE HTML PUBLIC “-//W3C//DTD HTML 4.01 Frameset//EN” “http://www.w3.org/TR/html4/frameset.dtd”>
	
	<!-- XHTML 1.0 Transitional -->
	<!DOCTYPE html PUBLIC “-//W3C//DTD XHTML 1.0 Transitional//EN” “http://www.w3.org/TR/xhtml1/DTD/xhtml1-transitional.dtd”>

	<!-- XHTML 1.0 Frameset -->
	<!DOCTYPE html PUBLIC “-//W3C//DTD XHTML 1.0 Frameset//EN” “http://www.w3.org/TR/xhtml1/DTD/xhtml1-frameset.dtd”>
     
准标准模式与标准模式非常接近，它们的差异几乎可以忽略不计。因此，当有人提到"标准模式"时，有可能是指这两种模式中的任何一种。
而且，**检测文档模式时也不会发现什么不同**。


