## 创建对象     
     
虽然 Object 构造函数或对象字面量都可以用来创建单个对象，但这些方式有个明显的缺点：  
**使用同一个接口创建很多对象，会产生大量的重复代码。**  
     
	var person1 = new Object();
    person1.name = "Nicholas";
    person1.age = 29;
    person1.sayName = function(){
    	console.log(this.name);
    };      
    var person2 = new Object();
    person2.name = "Greg";
    person2.age = 27;
    person2.sayName = function(){
    	console.log(this.name);
    }; 

    var person1 = {
    	name: "Nicholas",
    	age: 29,
    	sayName: function(){
        	console.log(this.name);
        }
    };     
    var person2 = {
    	name: "Greg",
        age: 27,
        sayName: function(){
        	console.log(this.name);
        }
    };

为解决这个问题，人们开始使用工厂模式的一种变体。    

### 工厂模式

工厂模式是软件工程领域的一种广为人知的设计模式，这种模式抽象了创建具体对象的过程。  
考虑到在 ECMAScript 中无法创建类，开发人员就发明了一种函数，  
用函数来封装以特定接口创建对象的细节，如下面的例子所示。  

	function createPerson(name, age, job){
    	var o = new Object();
        o.name = name;
        o.age = age;
        o.job = job;
        o.sayName = function(){
        	console.log(this.name);
        };
        return o;
    }

    var person1 = createPerson("Nicholas", 29, "Software Engineer");
    var person2 = createPerson("Greg", 27, "Doctor");

函数 createPerson() 能够根据接收的参数来构建一个包含所有必要信息的 person 对象。  
可以无数次地调用这个函数，而每次它都会返回一个包含三个属性一个方法的对象。  

**工厂模式虽然解决了创建多个相似对象的问题，但却没有解决对象识别的问题 (即怎样知道一个对象的类型)。**    

随着 JavaScript 的发展，又一个新模式出现了。
