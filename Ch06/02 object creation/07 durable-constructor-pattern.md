### 稳妥构造函数模式

道格拉斯.克罗克福德 (Douglas Crockford) 发明了 JavaScript 中的稳妥对象 (durable objects) 这个概念。  
所谓稳妥对象，指的是没有公共属性，而且其方法也不引用 this 的对象。  
稳妥对象最适合在一些安全的环境中 (这些环境中会禁止使用 this 和 new) ，  
或者在防止数据被其他应用程序 (如 Mashup 程序)改动时使用。  

稳妥构造函数遵循与寄生构造函数类似的模式，但有两点不同：  
 - 一是新创建对象的实例方法不引用 this；  
 - 二是不使用 new 操作符调用构造函数。  
 
按照稳妥构造函数的要求，可以将前面的 Person 构造函数重写如下。

	function Person(name, age, job){
    	// 创建要返回的对象
        var o = new Object();
        // 可以在这里定义私有变量和函数
		// 添加方法 
        o.sayName = function(){
        	console.log(name); 
        };

        // 返回对象
        return o;
    }

注意，在以这种模式创建的对象中，除了使用 sayName() 方法之外，没有其他办法访问 name 的值。  
可以像下面使用稳妥的 Person 构造函数。

	var friend = Person("Nicholas", 29, "Software Engineer");
    friend.sayName();   // "Nicholas"

这样，变量 person 中保存的是一个稳妥对象，而除了调用 sayName() 方法之外，没有别的方式可以访问其数据成员。  
即使有其他代码会给这个对象添加方法或数据成员，但也不可能有别的办法访问传入到构造函数中的原始数据。  

稳妥构造函数模式提供的这种安全性，使得它非常适合在某些安全执行环境 -- 例如，ADsfae 和 Caja 提供的环境下使用。  

与寄生构造函数模式类似，使用稳妥构造函数模式创建的对象与构造函数之间也没有什么关系，  
因此 instanceof 操作符对这种对象也没有意义。  

 