### 函数属性和方法

前面曾经提到过，ECMAScript 中的函数是对象，因此函数也有属性和方法。  
每个函数都包括两个属性：length 和 prototype。  

#### length  

其中，length 属性表示**函数希望接收的命名参数的个数**，如下面的例子所示。  

	function sayName(name){
    	alert(name);
    }
    function sum(num1, num2){
    	return num1 + num2;
    }
    function sayHi(){
    	alert("hi");
    }
    alert(sayName.length);  // 1
    alert(sum.length);    //2
    alert(sayHi.length);   // 0
     
以上代码定义了3个函数，但每个函数接收的命名参数个数不同。  
首先，sayName() 函数定义了一个参数，因此其length 属性的值为1 。  
类似地，sum()定义了两个参数，结果其 length 属性中保存的值为 2 。  
而 sayHi() 没有命名参数，所以其 length 值为 0 。

