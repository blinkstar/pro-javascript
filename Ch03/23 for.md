3### for 语句

for 语句也是一种前测试循环语句，但它具有在执行循环之前初始化变量和定义循环后要执行的代码的能力。  
以下是for语句的语法：

	for (initialization; expression; post-loop-expression) statement

下面是一个示例：  

	var count = 10;
    for(var i=0;i<count;i++){
    	alert(i);
    }

以上代码定义了变量i的初始值为0.   
只有当条件表达式 (i<count) 返回true的情况下才会进入 for 循环，因此也有可能不会执行循环体中的代码。  
如果执行了循环体中的代码，则一定会对循环后的表达式 (i++) 求值，即递增 i 的值。  

这个 for 循环语句与下面的 while 语句的功能相同：

	var count = 10;
    var i=0;
    while(i<count){
    	alert(i);
        i++;
    }

**使用 while循环做不到的，使用for循环同样也做不到**。   

也就是说，for循环只是把与循环有关的代码集中在了一个位置。  

有必要指出的是，**在for循环的变量初始化表达式中，也可以不使用 var 关键字**。  
该变量的初始化可以在**外部**执行，例如：  

	var count = 10;
	var i;
    for(i = 0; i < count; i++){
    	alert(i);
    }

以上代码与在循环初始化表达式中声明变量的效果是一样的。  
由于 ECMAScript 中**不存在块级作用域**，因此**在循环内部定义的变量也可以在外部访问到**。例如：  

	var count = 10;
    for(var i = 0; i< count; i++){
    	alert(i);
    }
    alert(i);

在这个例子中，会有一个警告框显示循环完成后变量 i 的值，这个值是 10.  
这是因为，**即使 i 是在循环内部定义的一个变量，但在循环外部仍然可以访问到它**。  
     
此外，for语句中的初始化表达式、控制表达式和循环后表达式都是可选的。  
将这两个表达式全部省略，就会创建一个无限循环，例如：  

	for(;;){  // 无限循环
    	doSomething();
    }

而只给出控制表达式实际上就是把 for 循环转换成了 while 循环，例如：  

	var count = 10;
    var i = 0;
    for(; i<count;){
    	alert(i);
        i++;
    }

由于for语句存在极大的灵活性，因此它也是ECMAScript中最常用的一个语句。  


