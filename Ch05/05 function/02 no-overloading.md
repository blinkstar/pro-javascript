### 没有重载 (深入理解)

将函数名想象为指针，也有助于理解为什么ECMAScript中没有函数重载的概念。  

	function addSomeNumber(num){
    	return num + 100;
    }
    function addSomeNumber(num){
    	return num + 200;
    }
    var result = addSomeNumber(100);    // 300
     
显然，这个例子中声明了两个同名函数，而结果则是后面的函数覆盖了前面的函数。  
以上代码实际上与下面的代码没有什么区别。  

	var addSomeNumber = function(num){
    	return num + 100;
    };
    addSomeNumber = function(num){
    	return num + 200;
    };
    var result = addSomeNumber(100);   // 300

通过观察重写之后的代码，很容易看清楚到底是什么回事儿 -- 在创建第二个函数时，  
实际上覆盖了引用第一个函数的变量 addSomeNumber 

