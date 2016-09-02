### 寄生式继承

寄生式 (parasitic) 继承是与原型式继承紧密相关的一种思路，并且同样也是有克罗克福德推而广之的。  

寄生式继承的思路与寄生式构造函数和工厂模式类似，即创建一个仅用于封装继承过程的函数，  
该函数在内部以某种方式来增强对象，最后再像真地是它做了所有工作一样返回对象。  

以下代码示范了寄生式继承模式。  

	function createAnother(original){
    	var clone = object(original);  // 通过调用函数创建一个新对象
        clone.sayHi = function(){    // 以某种方式来增强这个对象
        	console.log("hi");
        };
        return clone;    // 返回这个对象
    }

在这个例子中，createAnother() 函数接受了一个参数，也就是将要作为新对象基础的对象。  
然后，把这个对象 ( original ) 传递给 object() 函数，将返回的结果赋值给 clone 。  
再为 clone 对象添加一个新方法 sayHi() ，最后返回 clone 对象。  
可以像下面这样来使用 createAnother() 函数：  

	var person = {
    	name: "Nicholas",
        friends: ["Shelby", "Court", "Van"]
    };

    var anotherPerson = createAnother(person);
    anotherPerson.sayHi();   // "hi"

这个例子中的代码基于 person 返回了一个新对象 -- anotherPerson 。  
新对象不仅具有 person 的所有属性和方法，而且还有自己的 sayHi() 方法。  

在主要考虑对象而不是自定义类型和构造函数的情况下，寄生式继承也是一种有用的模式。  

前面示范继承模式时使用的 object() 函数不是必需的；任何能够返回新对象的函数都适用于此模式。  

**使用寄生式继承来为对象添加函数，会由于不能做到函数复用而降低效率；这一点与构造函数模式类似。**   ( sayHi() )


