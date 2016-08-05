### for-in 语句

for-in 语句是一种精准的迭代语句，可以用来枚举对象的属性。  
以下是 for-in 语句的语法：

	for(property in expression) statement

下面是一个示例：
	
	for(var propName in window){
         document.write(propName);
    }

在这个例子中，我们使用 for-in 循环来显示了BOM中window对象的所有属性。  
每次执行循环时，都会将window对象中存在的一个属性名赋值给变量propName。  
这个过程会一直持续到对象中的所有属性都被枚举一遍为止。  

与for语句类似，这里控制语句中的var操作符也不是必需的。
但是，为了保证使用局部变量，我们推荐上面例子中的这种做法。

ECMAScript**对象的属性没有顺序**。    
因此，**通过for-in循环输出的属性名的顺序是不可预测的**。  
具体来讲，所有属性都会被返回一次，但返回的次序可能会因浏览器而异。  

但是，如果表示要迭代的对象的变量值为 null 或 undefined, for-in 语句会抛出错误。  
ECMAScript 5 更正了这一行为；对这种情况不再抛出错误，而只是不执行循环体。  
为了保证最大限度的兼容性，建议在使用 for-in 循环之前，  
先检测确认该对象的值不是 null 或 undefined。

Safari 3 以前版本的 for-in 语句中存在一个 bug，该 bug 会导致某些属性被返回两次。
