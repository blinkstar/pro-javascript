#### test

正则表达式的第二个方法是 `test()`，它接受一个字符串参数。  

在模式与该参数匹配的情况下返回 `true`；否则 ，返回 `false` 。  

在只想知道目标字符串与某个模式是否匹配，但不需要知道其文本内容的情况下，使用这个方法非常方便。  
因此，`test()` 方法经常被用在 `if` 语句中，如下面的例子所示。  

	var text = "000-00-0000";
    var pattern = /\d{3}-\d{2}-\d{4}/;

    if(pattern.test(text)){
    	alert("The pattern was matched.");
    }

在这个例子中，我们使用正则表达式来测试一个数字序列。  
如果输入的文本与模式匹配，则显示一条消息。  
这种用法经常出现在验证用户输入的情况下，  
因为我们只想知道输入是不是有效，至于它为什么无效就无关紧要了。

RegExp 实例继承的 toLocaleString() 和 toString() 方法都会返回正则表达式的字面量，  
与创建正则表达式的方式无关。例如：

	var pattern = new RegExp("\\[bc\\]at", "gi");
    alert(pattern.toString());    //       /\[bc\]at/gi
    alert(pattern.toLocaleString());    //        /\[bc\]at/gi

即使上例中的模式是通过调用 RegExp 构造函数创建的，  
但 toLocaleString() 和 toString() 方法仍然会像它是以字面量形式创建的一样显示其字符串表示。

正则表达式的 valueOf() 方法返回正则表达式本身。(对象)  


