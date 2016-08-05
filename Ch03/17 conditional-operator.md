#### 条件操作符

条件操作符应该算是ECMAScript中最灵活的一种操作符了，  
而且它遵循与Java中的条件操作符相同的语法形式，如下面的例子所示：  

	variable = boolean_expression ? true_value : false_value;

本质上，这行代码的含义就是基于对 boolean_expression 求值的结果，  
决定给变量 variable 赋什么值。  
如果求值的结果为 true，则给变量 variable 赋 true_value 值；  
如果求值结果为 false，则给变量 variable 赋 false_value 值。  

再看一个例子：

	var max = (num1 > num2) ? num1 : num2;

在这个例子中，max中将会保存一个最大的值。  
这个表达式的意思是： 如果num1大于num2(关系表达式返回true)，则将num1的值赋给max;  
如果num1小于num2(关系表达式返回false)，则将 num2的值赋给 max 。


