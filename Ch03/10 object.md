#### Object 类型

ECMAScript 中的对象其实就是一组数据和功能的集合。
    
对象可以通过执行 `new` 操作符后跟要创建的对象类型的名称来创建。  

而创建 Object 类型的实例并为其添加属性和(或)方法，就可以创建自定义对象，如下所示：  

	var o = new Object();
     
这个语法与 Java 中创建对象的语法相似；  
但在 ECMAScript 中，如果不给构造函数传递参数，则可以省略后面的那一对圆括号。  
也就是说，在像前面这个示例一样不传递参数的情况下，完全可以省略那对圆括号(但这不是推荐的做法)：  

	var o = new Object; // 有效，但不推荐省略圆括号

仅仅创建 Object 的实例并没有什么用处，但关键是要理解一个重要的思想：  
即在 ECMAScript 中，(就像Java中的 java.lang.Object对象一样)   
Object 类型是所有它的实例的基础。  
换句话说，Object 类型所具有的任何属性和方法也同样存在于更具体的对象中。  

Object的每个实例都具有下列属性和方法。

 - Constructor: 保存着用于创建当前对象的函数。对于前面的例子而言，构造函数 (constructor) 就是 Object()。
 - hasOwnProperty(propertyName): 用于检测给定的属性在当前对象**实例**中 (而不是在实例的**原型**中)是否存在。
 	其中，作为参数的属性名(propertyName)必须以字符串形式指定(例如：o.hasOwnProperty("name") )。
 - isPrototypeOf(object): 用于检查传入的对象是否是另一个对象的原型。   
 - propertyIsEnumerable(propertyName): 用于检查给定的属性是否能够使用 for-in 语句来枚举。
 	与hasOwnProperty()方法一样，作为参数的属性名必须以字符串形式指定。
 - toLocaleString(): 返回对象的字符串表示，该字符串与执行环境的地区对应。
 - toString(): 返回对象的字符串表示。
 - valueOf(): 返回对象的字符串、数值或布尔值表示。通常与 toString() 方法的返回值相同。

由于在ECMAScript中Object是所有对象的基础，因此所有对象都具有这些基本的属性和方法。

    
     
