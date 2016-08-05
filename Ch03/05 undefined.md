### Undefined 类型

`Undefined` 类型只有一个值，即特殊的 `undefined` 。  

在使用 `var` **声明变量**但未对其加以**初始化**时，这个变量的值就是 `undefined` ，例如：  
     
	var message;
    alert(message == undefined);   // true

这个例子只声明了变量 `message`，但未对其进行初始化。  
比较这个变量与`undefined`字面量，结果表明它们是相等的。  

这个例子与下面的例子是等价的：  

	var message = undefined;
    alert(message == undefined);  // true

这个例子使用 `undefined` 值显示初始化了变量 `message` 。  
但我们没有必要这么做，因为**未经初始化的值默认就会取得 undefined 值**。  

一般而言，不存在需要显示地把一个变量设置为 `undefined` 值的情况。  
字面值 `undefined` 的主要目的是**用于比较**，而ECMA-262第3版之前的版本中并没有规定这个值。  
第3版引入这个值是为了**正式区分空对象指针**与**未经初始化的变量**。  
     
不过，包含 `undefined` 值的变量与**尚未定义的变量**还是不一样的。看看下面这个例子：  

	var message; // 这个变量声明之后默认取得了 undefined 值
    // 下面这个变量没有声明 
    // var age

    alert(message); // "undefined"
    alert(age);     // 产生错误

运行以上代码，第一个警告框会显示变量 message 的值，即 "undefined"。  
而第二个警告框 -- 由于传递给 `alert()` 函数的是尚未声明的变量 `age` -- 则会导致一个错误。  

**对于尚未声明过的变量，只能执行一项操作，即使用 typeof 操作符检测其数据类型**    
(对未经声明的变量调用delete不会导致错误，但这样做没什么实际意义，而且在严格模式下确实会导致错误)。  

然而，令人困惑的是： 对**未初始化的变量**执行 typeof 操作符会返回 undefined 值，    
而对**未声明的变量**执行 typeof 操作符同样也会返回 undefined 值。来看下面的例子：  

	var message; // 这个变量声明之后默认取得了 undefined值
    // 下面这个变量并没有声明
    // var age
    alert(typeof message);           // "undefined"
    alert(typeof age);                   // "undefined"

结果表明，**对未初始化和未声明的变量执行typeof操作符都返回了undefined值**；  
这个结果有其逻辑上的合理性。  
因为虽然这两种变量从技术角度看有本质区别，但实际上无论对哪种变量也不可能执行真正的操作。  

即便未初始化的变量会自动被赋予 `undefined` 值，但显示地初始化变量依然是明智的选择。  
如果能够做到这一点，那么当`typeof`操作符返回 `"undefined"` 值时，  
我们就知道被检测的变量还没有被声明，而不是尚未初始化。  



