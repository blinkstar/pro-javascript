## RegExp 类型

ECMAScript 通过 RegExp 类型来支持正则表达式。  

使用下面类似 Perl 的语法，就可以创建一个正则表达式。

	var expression = /pattern/ flags;

其中的模式 (pattern) 部分可以是任何简单或复杂的正则表达式，  
可以包含字符类、限定符、分组、向前查找以及反向引用。  

每个正则表达式都可带有一或多个标志 (flags)，用以标明正则表达式的行为。  
正则表达式的匹配模式支持下列3个标志。
 - g: 表示全局 (global) 模式，即模式将被应用于所有字符串，而非在发现第一个匹配项时立即停止；
 - i: 表示不区分大小写 (case-insensitive) 模式，即在确定匹配项时忽略模式与字符串的大小写；
 - m: 表示多行 (multiline) 模式，即在到达一行文本末尾时还会继续查找下一行中是否存在与模式匹配的项。

因此，一个正则表达式就是一个模式与上述3个标志的组合体。  
不同组合产生不同结果，如下面的例子所示。 

	// 匹配字符串中所有 "at" 的实例
    var pattern1 = /at/g;

    // 匹配第一个 "bat" 或 "cat"，不区分大小写
    var pattern2 = /[bc]at/i;

    // 匹配所有以 "at" 结尾的3个字符的组合，不区分大小写
    var pattern3 = /.at/gi;

与其他语言中的正则表达式类似，模式中使用的所有元字符都必须转义。  
正则表达式中的元字符包括：

	( [ { \ ^ $ | ) ? * + . ] }

这些元字符在正则表达式中都有一或多种特殊用途，因此如果想要匹配字符串中包含的这些字符，  
就必须对它们进行转义。下面给出几个例子。  
    
	// 匹配第一个 "bat" 或 "cat"，不区分大小写
    var pattern1 = /[bc]at/i;

    // 匹配第一个 "[bc]at" 不区分大小写
    var pattern2 = /\[bc\]at/i;

    // 匹配所有以 "at" 结尾的3个字符的组合，不区分大小写
    var pattern3 = /.at/gi;

    // 匹配所有 ".at"，不区分大小写
    var pattern4 = /\.at/gi;

在上面的例子中，pattern1 匹配第一个 "bat" 或 "cat"，不区分大小写。  
而要想直接匹配 "[bc]at" 的话，就需要像定义 pattern2 一样，对其中的两个方括号进行转义。  
对于 pattern3 来说，句点表示位于 "at" 之前的任意一个可以构成匹配项的字符。  
但如果想匹配 ".at" ，则必须对句点本身进行转义，如pattern4 所示。  

前面举的这些例子都是以字面量形式来定义的正则表达式。  

另一种创建正则表达式的方式是使用 `RegExp` 构造函数，它接收两个参数：  
一个是要匹配的字符串模式，另一个是可选的标志字符串。  

可以使用字面量定义的任何表达式，都可以使用构造函数来定义，如下面的例子所示。  

	// 匹配第一个 "bat" 或 "cat" ，不区分大小写
    var pattern1 = /[bc]at/i;
    // 与 pattern1 相同，只不过是使用构造函数创建的
    var pattern2 = new RegExp("[bc]at", "i");
     
在此，pattern1 和 pattern2 是两个完全等价的正则表达式。  

要注意的是，传递给 RegExp 构造函数的两个**参数都是字符串**  
(不能把正则表达式字面量传递给 RegExp 构造函数)。    
    
由于 RegExp 构造函数的模式参数是字符串，所以在某些情况下要对字符进行**双重转义**。
  
所有元字符都必须双重转义，那些已经转义过的字符也是如此，例如 `\n`  
(字符 `\` 在字符串中通常被转义为 `\\` ，而在正则表达式字符串中就会变成 `\\\\`)

	console.log("\");  --- 报错
    console.log("\\"); --- 输出 \

下面给出了一些模式，左边是这些模式的字面量形式，右边是使用 RegExp 构造函数定义相同模式时使用的字符串。

<table>
	<thead>
		<tr><th>字面量模式</th><th>等价的字符串</th></tr>
	</thead>
	<tbody>
		<tr><td>/\[bc\]at/</td><td>"\\[bc\\]at"</td></tr>
		<tr><td>/\.at/</td><td>"\\.at"</td></tr>
		<tr><td>/name\/age/</td><td>"name\\/age"</td></tr>
		<tr><td>/\d.\d{1,2}/</td><td>"\\d.\\d{1,2}"</td></tr>
		<tr><td>/\w\\hello\\123/</td><td>"\\w\\\\hello\\\\123"</td></tr>
	</tbody>
</table>

使用正则表达式字面量和使用 RegExp 构造函数创建的正则表达式不一样。  

在 ECMAScript 3 中，  
正则表达式**字面量**始终会**共享**同一个 RegExp 实例，  
而使用**构造函数**创建的每一个新的 RegExp 实例都是一个**新实例**。来看下面的例子。  

	var re = null,
    	i;
    for(i=0;i<10;i++){
    	re = /cat/g;
    	// Chrome 中 re.lastIndex  为 0
        console.log(re.test("catastrophe"));  // Chrome true
        // Chrome 中 re.lastIndex  为 3
    }
    for(i=0;i<10;i++){
    	re = new RegExp("cat", "g");
    	// Chrome 中 re.lastIndex  为 0
        console.log(re.test("catastrophe"));  // Chrome true
        // Chrome 中 re.lastIndex  为 3
    }
    
    re = /cat/g;
    for(i=0;i<10;i++){
    	// Chrome 中 re.lastIndex  为 0 3 交替 
        console.log(re.test("catastrophe"));  // Chrome true false 交替
    }
    re = new RegExp("cat", "g");
    for(i=0;i<10;i++){
    	// Chrome 中 re.lastIndex  为 0 3 交替 
    	console.log(re.test("catastrophe"));  // Chrome true false 交替
    }

在第一个循环中，即使是循环体中指定的，但实际上只为 /cat/创建了**一个** RegExp 实例。  
由于实例属性**不会重置**，所以在循环中调用 test() 方法会失败。  
这是因为第一次调用 test() 找到了 "cat"，  
但第二次调用是从**索引为3**的字符 (上一次匹配的末尾)开始的，所以就找不到它了。  
由于会测试到字符串末尾，所以下一次调用test()就又从开头开始了。

第二个循环使用 RegExp 构造函数在每次循环中创建正则表达式。  
因为每次迭代都会创建一个**新的 RegExp 实例**，所以每次调用 test() 都会返回 true。

ECMAScript 5 明确规定，  
**使用正则表达式字面量必须像直接调用 RegExp() 构造函数一样，每次都创建新的 RegExp 实例**。  
IE 9+、Firefox 4 + 和 Chrome 都据此做出了修改。
     
     