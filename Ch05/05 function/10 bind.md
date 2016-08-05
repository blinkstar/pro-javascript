#### bind

ECMAScript 5 还定义了一个方法： bind() 。  

这个方法会**创建一个函数的实例**，其 this 值会被绑定到传给 bind() 函数的值。例如：  

	window.color = "red";
    var o = {color: "blue"};
    function sayColor(){
    	alert(this.color);
    }
    
    var objectSayColor = sayColor.bind(o);  // this 指向 o
    
    // 这里使用 sayColor.call(o) 会直接报错，call 是运行，返回 undefiend 
    // 因为 objectSayColor 的值等于 sayColor.call(o) 运行后的返回值
    
    objectSayColor(); // blue
     
在这里，sayColor()调用 bind() 并传入对象 o ，创建了 objectSayColor() 函数。  
objectSayColor() 函数的 this 值等于 o，因此即使是在全局作用域中调用这个函数，也会看到 "blue" 。  

支持 bind() 方法的浏览器有 IE 9+ 、Firefox 4+ 、Safari 5.1 + 、Opera 12+ 和 Chrome 。  

每个函数继承的 toLocaleString() 和 toString() 方法始终都**返回函数的代码**。  
返回代码的格式则因浏览器而异 -- 有的返回的代码与源代码中的函数的代码一样，  
而有的则返回函数代码的内部表示，即由解析器删除了注释并对某些代码做了改动后的代码。  
由于存在这些差异，我们无法根据这两个方法返回的结果来实现任何重要功能；  
不过，这些信息在调试代码时倒是很有用。   

另外一个继承的 valueOf() 方法同样也**只返回函数代码**。  

