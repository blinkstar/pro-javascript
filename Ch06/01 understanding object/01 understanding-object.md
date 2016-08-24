## 理解对象

面向对象 (Object-Oriented, OO)的语言有一个标志，那就是它们都有类的概念，  
而通过类可以创建任意多个具有相同属性和方法的对象。  
前面提到过，ECMAScript 中没有类的概念，因此它的对象也与基于类的语言中的对象有所不同。  
     
ECMA-262 把对象定义为："无序属性的集合，其属性可以包含基本值、对象或者函数。"  
严格来讲，这就相当于说对象是一组没有特定顺序的值。  
对象的每个属性或方法都有一个名字，而每个名字都映射到一个值。  
正因为这样 (以及其他将要讨论的原因)，我们可以把 ECMAScript 的对象想象成散列表：  
无非就是一组名值对，其中值可以是数据或函数。  

**每个对象都是基于一个引用类型创建的，这个引用类型可以是原生类型，也可以是开发人员定义的类型。**     

### 理解对象

之前曾经介绍过，创建自定义对象的最简单方式就是创建一个 Object 的实例，然后再为它添加属性和方法，如下所示。   

	var person = new Object();
    person.name = "Nicholas";
    person.age = 29;
    person.job = "Software Engineer";

    person.sayName = function(){
    	console.log(this.name);
    };

上面的例子创建了一个名为 person 的对象，并为它添加了三个属性 (name、age 和 job) 和一个方法 ( sayName() ) 。  
其中，sayName() 方法用于显示 this.name (将被解析为 person.name ) 的值。  
早期的 JavaScript 开发人员经常使用这个模式创建新对象。  
几年后，对象字面量成为创建这种对象的首选模式。前面的例子用对象字面量语法可以写成这样：  
     
	var person = {
    	name: "Nicholas",
        age: 29,
        job: "Software Engineer",

        sayName: function(){
        	console.log(this.name);
        }
	};   

这个例子中的 person 对象与前面例子中的 person 对象是一样的，都有相同的属性和方法。  
这些属性在创建时都带有一些特征值 (characteristic) ，JavaScript 通过这些特征值来定义它们的行为。    


