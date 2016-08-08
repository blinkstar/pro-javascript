### fromCharCode() 方法

另外，String 构造函数本身还有一个静态方法： fromCharCode() 。  
这个方法的任务是接收一或多个字符编码，然后将它们转换成一个字符串。  

从本质上来看，这个方法与实例方法 charCodeAt() 执行的是相反的操作。来看一个例子：
     
	console.log(String.fromCharCode(104, 101, 108, 108, 111));  // "hello"

在这里，我们给 fromCharCode() 传递的是字符串 "hello" 中每个字母的字符编码。 

