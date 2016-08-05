### Boolean 类型

`Boolean` 类型是`ECMAScript`中使用得最多的一种类型，该类型只有两个字面值: `true` 和 `false` 。  

这两个值与数字值不是一回事，因此 `true` 不一定等于 1 ，而 `false` 也不一定等于 0 。  

以下是为变量赋 `Boolean` 类型值的例子：   

	var found = true;
    var lost = false;

需要注意的是，`Boolean`类型的字面值 `true` 和 `false` 是**区分大小写的**。  
也就是说， **True 和 False (以及其他的混合大小写形式) 都不是 Boolean 值**，只是标识符。  

虽然 `Boolean` 类型的字面值只有两个，但 `ECMAScript` 中所有类型的值都有与这两个 `Boolean` 值等价的值。  
要将一个值转换为其对应的 `Boolean` 值，可以调用**转型函数 Boolean()**，如下例所示：  

	var message = "Hello world!";
    var messageAsBoolean = Boolean(message);

在这个例子中，字符串 `message` 被转换成了一个 `Boolean` 值，该值被保存在 `messageAsBoolean` 变量中。  

可以对任何数据类型的值调用 `Boolean()` 函数，而且总会返回一个  `Boolean` 值。  
至于返回的这个值是 `true` 还是 `false` ，取决于要转换值的数据类型及其实际值。  
下表给出了各种数据类型及其对应的转换规则。  

<table>
	<thead>
		<tr><th>数据类型</th><th>转换为true的值</th><th>转换为false的值</th></tr>
	</thead>
	<tbody>
		<tr><td>Boolean</td><td>true</td><td>false</td></tr>
		<tr><td>String</td><td>任何非空字符串</td><td>""(空字符串)</td></tr>
		<tr><td>Number</td><td>任何非零数字值(包括无穷大)</td><td>0和NaN</td></tr>
		<tr><td>Object</td><td>任何对象</td><td>null</td></tr>
		<tr><td>Undefined</td><td>n/a</td><td>undefined</td></tr>
	</tbody>
</table>

这些转换规则对理解流控制语句 (如 `if` 语句) 自动执行相应的 `Boolean` 转换非常重要，请看下面的代码:  

	var message = "Hello world!";
    if(message){
    	alert("Value is true");
    }

运行这个示例，就会显示一个警告框，因为字符串 `message` 被自动转换成了对应的 `Boolean` 值 `(true)` 。  
由于存在这种自动执行的 `Boolean` 转换，因此确切地知道在流控制语句中使用的是什么变量至关重要。  
错误地使用一个对象而不是一个 `Boolean`值，就有可能彻底改变应用程序的流程。  


