### with 语句

with 语句的作用是**将代码的作用域设置到一个特定的对象中**。  

with语句的语法如下：

	with (expression) statement;

定义 with 语句的目的主要是为了**简化多次编写同一个对象**的工作，如下面的例子所示：

	var qs = location.search.substring(1);
    var hostName = location.hostname;
    var url = location.href;

上面几行代码都包含 `location` 对象。  
如果使用`with`语句，可以把上面的代码改写成如下所示：

	with(location){
    	var qs = search.substring(1);
        var hostname = hostname;
        var url = href;
    }

在这个重写后的例子中，使用with语句关联了location对象。  
这意味着在with语句的代码块内部，  
每个变量**首先被认为是一个局部变量**  
而如果在局部环境中找**不到该变量的定义**，就会查询 location 对象中是否有同名的属性。  
如果发现了同名属性，则以 location 对象属性的值作为变量的值。  

**严格模式下不允许使用 with 语句**，否则将视为语法错误。

由于大量使用 with 语句会导致性能下降，同时也会给调试代码造成困难，因此在开发大型应用程序时，不建议使用 with 语句。


