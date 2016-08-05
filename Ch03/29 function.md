### 函数

函数对任何语言来说都是一个核心的概念。  

通过函数可以封装任意多条语句，而且可以在任何地方、任何时候调用执行。  
ECMAScript中的函数使用function关键字来声明，后跟一组参数以及函数体。  
函数的基本语法如下所示：

	function functionName(arg0, arg1, ..., argN){
    	statements
    }

以下是一个函数示例：

	function sayHi(name, message){
    	alert("Hello " + name + "," + message);
    }

这个函数可以通过其函数名来调用，后面还要加上一对圆括号和参数  
(圆括号中的参数如果有多个，可以用逗号隔开)。  

调用 sayHi() 函数的代码如下所示：

	sayHi("Nicholas", "how are you today?");
     
这个函数的输出结果是 `"Hello Nicholas, how are you today?"` 。  
函数中定义的命名参数 `name` 和 `message` 被用作了字符串拼接的两个操作数，  
而结果最终通过警告框显示了出来。  

ECMAScript 中的函数在定义时不必指定是否返回值。  
实际上，任何函数在任何时候都可以通过 return 语句后跟要返回的值来实现返回值。请看下面的例子：

	function sum(num1, num2){
    	return num1 + num2;
    }

这个 `sum()` 函数的作用是把两个值加起来返回一个结果。  
我们注意到，除了 `return` 语句之外，没有任何声明表示该函数会返回一个值。  
调用这个函数的示例代码如下：

	var result = sum(5, 10);
     
这个函数会在执行完 `return` 语句之后停止并立即退出。  
因此，位于 return 语句之后的任何代码都永远不会执行。例如：

	function sum(num1, num2){
    	return num1 + num2;
        alert("Hello world");    // 永远都不会执行
    }
     
在这个例子中，由于调用`alert()`函数的语句位于 `return` 语句之后，因此永远不会显示警告框。  

当然，一个函数中也可以包含多个 `return` 语句，如下面这个例子中所示：  

	function diff(num1, num2){
		if(num1 < num2){
    		return num2 - num1;
    	}else {
    		return num1 - num2;
    	}
    }

这个例子中定义的 `diff()` 函数用于计算两个数值的差。  
如果第一个数比第二个小，则用第二个数减第一个数；  
否则，用第一个数减第二个数。  
代码中的两个分支都具有自己的 `return` 语句，分别用于执行正确的计算。  

另外，`return` 语句也可以不带有任何返回值。  
在这种情况下，函数在停止执行后将返回 `undefined` 值。  
这种用法一般用在需要提前停止函数执行而又不需要返回值的情况下。  
比如在下面这个例子中，就不会显示警告框：

	function sayHi(name, message){
    	return;
        alert("Hello " + name + "," + message);    // 永远不会调用
    }
     
严格模式对函数有一些限制：

 - 不能把函数命名为 eval 或 arguments;
 - 不能把参数命名为 eval 或 arguments;
 - 不能出现两个命名参数同名的情况。

如果发生以上情况，就会导致语法错误，代码无法执行。  

#### 理解参数

ECMAScript 函数的参数与大多数其他语音中函数的参数有所不同。   
ECMAScript 函数不介意传递进来多少个参数，也不在乎传进来参数是什么数据类型。  
也就是说，即便你定义的函数只接收两个参数，在调用这个函数时也未必一定要传递两个参数。 
可以传递一个、三个甚至不传递参数，而解析器永远不会有什么怨言。  

之所以会这样，原因是 ECMAScript 中的参数在内部是用一个数组来表示的。  
函数接收到的始终都是这个数组，而不关心数组中包含哪些参数(如果有参数的话)。  
如果这个数组中不包含任何元素，无所谓；  
如果包含多个元素，也没有问题。  

实际上，在函数体内可以通过 `arguments` 对象来访问这个参数数组，从而获得传递给函数的每一个参数。

其实，`arguments` 对象只是与数组类似，(它并不是 Array 的实例)，   
因为**可以使用方括号语法访问它的每一个元素**   
(即第一个元素是 arguments[0] ，第二个元素是 arguments[1] ，以此类推)，  
**使用 length 属性来确定传递进来多少个参数**。  

在前面的例子中，sayHi() 函数的第一个参数的名字叫 name，  
而该参数的值也可以通过访问 arguments[0] 来获取。  
因此，那个函数也可以像下面这样重写，即不显示地使用命名参数：

	function sayHi(){
    	alert("Hello " + arguments[0] + "," + arguments[1]);
    } 

这个重写后的函数中不包含命名的参数。  
虽然没有使用 name 和 message 标识符，但函数的功能依旧。  
这个事实说明了 ECMAScript 函数的一个重要特点：  
命名的参数只提供便利，但不是必需的。  

另外，在命名参数方面，其他语言可能需要事先创建一个函数签名，而将来的调用必须与该签名一致。  
但在ECMAScript中，没有这些条条框框，解析器不会验证命名参数。
     
通过访问 arguments 对象的 length 属性可以获知有多少个参数传递给了函数。  
下面这个函数会在每次被调用时，输出传入其中的参数个数：

	function howManyArgs(){
    	alert(arguments.length);
    }

    howManyArgs("string", 45); // 2
    howManyArgs(); // 0
    howManyArgs(12); // 1

执行以上代码会依次出现3个警告框，分别显示 2、0和1 。  
由此可见，开发人员可以利用这一点让函数能够接收任意个参数并分别实现适当的功能。  
请看下面的例子：

	function doAdd(){
    	if(arguments.length == 1){
        	alert(arguments[0] + 10);
        }else if(arguments.length == 2){
        	alert(arguments[0] + arguments[1]);
        }
    }

    doAdd(10);  // 20
    doAdd(30, 20); // 50

函数 doAdd() 会在只有一个参数的情况下给该参数加上 10；  
如果是两个参数，则将那个参数简单相加并返回结果。  
因此，doAdd(10)会返回20，而doAdd(30, 20) 则返回 50。  
虽然这个特性算不上完美的重载，但也足够弥补 ECMAScript 的这一缺憾了。

另一个与参数相关的重要方面，就是 arguments 对象可以与命名参数一起使用，  
如下面的例子所示：

	function doAdd(num1, num2){
    	if(arguments.length == 1){
        	alert(num1 + 10);
        }else if(arguments.length == 2){
        	alert(arguments[0] + num2);
        }
    }

在重写后的这个 doAdd() 函数中，两个命名参数都与 arguments 对象一起使用。  
由于 num1 的值与 arguments[0] 的值相同，因此它们可以互换使用  
(当然，num2 和 arguments[1] 也是如此)。

关于 arguments 的行为，还有一点比较有意思。  
**那就是它的值永远与对应命名参数的值保持同步**。例如：  

	function doAdd(num1, num2){
    	arguments[1] = 10;
        alert(arguments[0] + num2);
    }

每次执行这个 `doAdd()` 函数都会重写第二个参数，将第二个参数的值修改为 10 。  
因为 arguments 对象中的值会自动反映到对应的命名参数，  
所以修改 arguments[1]，也就修改了 num2 ，结果它们的值都会变成 10 。

不过，**这并不是说读取这两个值会访问相同的内存空间；它们的内存空间是独立的，但它们的值会同步**。

另外还要记住，**如果只传入了一个参数，那么 arguments[1] 设置的值不会反映到命名参数中**。  
这是因为 **arguments 对象的长度是由传入的参数个数决定的，不是由定义函数时的命名参数的个数决定的**。

关于参数还要记住最后一点：没有传递值的命名参数将自动被赋予 undefined 值。  
这就跟定义了变量但又没有初始化一样。  
例如，如果只给 doAdd() 函数传递了一个参数，则 num2 中就会保存 undefined 值。

严格模式对如何使用 arguments 对象做出了一些限制。  
首先，像前面例子中那样的赋值会变得无效。  
也就是说，即使把 arguments[1] 设置为10，  
num2 的值仍然还是 undefined 。  
其次，重写 arguments 的值会导致语法错误 (代码将不会执行) 。

ECMAScript 中的所有参数传递的**都是值**，不可能通过**引用**传递参数。

#### 没有重载

ECMAScript 函数不能像传统意义上那样实现重载。  
而在其他语言(如 Java) 中，可以为一个函数编写两个定义，  
只要这两个定义的签名(接受的参数的类型和数量)不同即可。  

如前所述，ECMAScript函数没有签名，因为其参数是由包含零或多个值的数组来表示的。  
而**没有函数签名，真正的重载是不可能做到的**。  

如果在ECMAScript 中定义了两个名字相同的函数，则**该名字只属于后定义的函数**。  
请看下面的例子：

	function addSomeNumber(num){
    	return num + 100;
    }
    function addSomeNumber(){
    	return num + 200;
    }
    var result = addSomeNumber(100);       // 300

在此，函数 addSomeNumber() 被定义了两次。  
第一个版本给参数加 100，而第二个版本给参数加 200.  
由于后定义的函数覆盖了先定义的函数，  
因此当在最后一行代码中调用这个函数时，返回的结果就是 300.  

如前所述，通过检查传入函数中参数的类型和数量并作出不同的反映，可以模仿方法的重载。


