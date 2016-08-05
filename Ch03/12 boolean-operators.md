### 布尔操作符

在一门编程语言中，布尔操作符的重要性堪比相等操作符。  
如果没有测试两个值关系的能力，那么诸如 if.....else 和循环之类的语句就不会有用武之地了。  

布尔操作符一共有3个：非(NOT)、与(AND)和或(OR) 。

#### 逻辑非

逻辑非操作符由一个叹号(!)表示，可以应用于ECMAScript中的任何值。  
无论这个值是什么数据类型，这个操作符都会返回一个布尔值。  
逻辑非操作符首先将它的操作数转换为一个布尔值，然后再对其求反。  
也就是说，逻辑非操作符遵循下列规则：

 - 如果操作数是一个对象，返回 false；
 - 如果操作数是一个空字符串，返回true；
 - 如果操作数是一个非空字符串，返回 false；
 - 如果操作数是数值 0，返回 true；
 - 如果操作数是任意非 0 数值(包括Infinity)，返回 false ；
 - 如果操作数是 null，返回 true;
 - 如果操作数是 NaN ，返回 true;
 - 如果操作数是 undefined，返回 true 。

下面几个例子展示了应用上述规则的结果：

	alert(!false);   // true
    alert(!"blue");  // false
    alert(!0);       // true
    alert(!NaN);     // true
    alert(!"");      // true
    alert(!12345);   // false

逻辑非操作符也可以用于将一个值转换为其对应的布尔值。  
**而同时使用两个逻辑非操作符，实际上就会模拟 Boolean() 转型函数的行为**。  

其中，第一个逻辑非操作会基于无论什么操作数返回一个布尔值，而第二个逻辑非操作则对该布尔值求反，  
于是就得到了这个值真正对应的布尔值。  

当然**最终结果与对这个值使用 Boolean()函数相同**，如下面的例子所示：  
	
	alert(!!"blue");  // true
    alert(!!0);   // false
    alert(!!NaN); // false
    alert(!!"");   // false
    alert(!!12345);  // true

#### 逻辑与

逻辑与操作符由两个和号 (&&) 表示，有两个操作数，如下面的例子所示：  

	var result = true && false;

逻辑与的真值表如下：

<table>
	<thead>
		<tr><th>第一个操作数</th><th>第二个操作数</th><th>结果</th></tr>
	</thead>
	<tbody>
		<tr><td>true</td><td>true</td><td>true</td></tr>
		<tr><td>true</td><td>false</td><td>false</td></tr>
		<tr><td>false</td><td>true</td><td>false</td></tr>
		<tr><td>false</td><td>false</td><td>false</td></tr>
	</tbody>
</table>
     
逻辑与操纵可以应用于任何类型的操作数，而不仅仅是布尔值。  

**在有一个操作数不是布尔值的情况下，逻辑与操作数就不一定返回布尔值**；  
此时，它遵循下列规则：

 - 如果第一个操作数是对象，则返回第二个操作数；
 - 如果第二个操作数是对象，则只有在第一个操作数的求值结果为true的情况下才会返回该对象；    
 - 如果两个操作数都是对象，则返回第二个操作数；
 - 如果有一个操作数是null，则返回null；
 - 如果有一个操作数是NaN，则返回NaN；
 - 如果有一个操作数是undefined，则返回undefined 。

逻辑与操作属于短路操作，即如果第一个操作数能够决定结果，那么就不会再对第二个操作数求值。  
对于逻辑与操作而言，如果第一个操作数是false，则无论第二个操作数是什么值，结果都不再可能是 true 了 。  
来看下面的例子：

	var found = true;
    var result = (found && someUndefinedVariable) ;   // 这里会发生错误
    alert(result); // 这一行不会执行

在上面的代码中，当执行逻辑与操作时会发生错误，因为变量 someUndefinedVarible 没有声明。  
由于变量 found的值是true，所以逻辑与操作符会继续对变量someUndefinedVariable 求值。  
但 someUndefinedVarible 尚未定义，因此就会导致错误。  
这说明不能在逻辑与操作中使用未定义的值。  

**如果像下面这个例子中，将 found 的值设置为 false，就不会发生错误了**：

	var found = false;
    var result = (found && someUndefinedVariable); // 不会发生错误
    alert(result);   // 会执行 ("false")

在这个例子中，警告框会显示出来。  
无论变量 someUndefinedVariable 有没有定义，也永远不会对它求值，因为第一个操作数的值是 false 。  
而这也就意味着逻辑与操作的结果必定是 false ，根本用不着再对 && 右侧的操作数求值了。   
在使用逻辑与操作符时要始终铭记它是一个短路操作符。

#### 逻辑或

逻辑或操作符由两个竖线符号 (||) 表示，有两个操作数，如下面的例子所示：  

	var result = true || false;

逻辑或的真值表如下：

<table>
	<thead>
		<tr><th>第一个操作数</th><th>第二个操作数</th><th>结果</th></tr>
	</thead>
	<tbody>
		<tr><td>true</td><td>true</td><td>true</td></tr>
		<tr><td>true</td><td>false</td><td>true</td></tr>
		<tr><td>false</td><td>true</td><td>true</td></tr>
		<tr><td>false</td><td>false</td><td>false</td></tr>
	</tbody>
</table>
     
与逻辑与操作相似，如果有一个操作数不是布尔值，逻辑或也不一定返回布尔值；  
此时，它遵循下列规则：

 - 如果第一个操作数是对象，则返回第一个操作数；
 - 如果第一个操作数的求值结果为 false，则返回第二个操作数；
 - 如果两个操作数都是对象，则返回第一个操作数；
 - 如果两个操作数都是null，则返回null;
 - 如果两个操作数都是NaN，则返回NaN
 - 如果两个操作数都是 undefined，则返回 undefined。


与逻辑与操作数相似，逻辑或操作符**也是短路操作符**。
  
也就是说，**如果第一个操作数的求值结果为true，就不会对第二个操作数求值了**。下面看一个例子：  

	var found = true;
    var result = (found || someUndefinedVariable); // 不会发生错误
    alert(result);   // 会执行 ("true") 

这个例子跟前面的例子一样，变量 someUndefinedVariable 也没有定义。  
但是，由于变量 found 的值是 true，而变量 someUndefinedVariable 永远不会被求值，因此结果就会输出 "true" 。  
如果像下面这个例子一样，把found的值改为 false，就会导致错误：

	var found = false;
    var result = (found || someUndefinedVariable); // 这里会发生错误
    alert(result);   // 这一行不会执行

**我们可以利用逻辑或的这一行为来避免为变量赋 null 或 undefined 值**。例如：

	var myObject = preferredObject || backupObject;

在这个例子中，变量 myObject 将被赋予等号后面两个值中的一个。  

变量 preferredObject 中包含优先赋值给变量 myObject 的值，变量backupObject负责在preferredObject中不包含有效值的情况下提供后备值。  
如果 preferredObject 的值不是 null，那么它的值将被赋给 myObject；如果是null，则将backupObject的值赋给myObject。  

**ECMAScript程序的赋值语句经常会使用这种模式**。


