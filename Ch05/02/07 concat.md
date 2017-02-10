### 操作方法

ECMAScript 为操作已经包含在数组中的项提供了很多方法。


#### concat

    
其中，concat() 方法可以基于当前数组中的所有项创建一个新数组。  

具体来说，这个方法会先  

 - 创建当前数组一个副本，  
 - 然后将接收到的参数添加到这个副本的末尾，  
 - 最后返回新构建的数组。  
 
在没有给 concat() 方法传递参数的情况下，它**只是复制**当前数组并**返回副本**。  

如果传递给 concat() 方法的是一或多个数组，则该方法会将这些数组中的每一项都添加到结果数组中。  

如果传递的值不是数组，这些值会被简单地添加到结果数组的末尾。下面来看一个例子。

	var colors = ["red", "green", "blue"];
    var colors2 = colors.concat("yellow", ["black", "brown"]);

    alert(colors);   // red,green,blue
    alert(colors2);  // red,green,blue,yellow,black,brown

以上代码开始定义了一个包含3个值的数组 colors。  
然后，基于 colors 调用了 concat() 方法，  
并传入字符串 "yellow" 和一个包含 "black" 和 "brown" 的数组。  

最终，结果数组 colors2 中包含了 "red"、"green"、"blue"、"yellow"、"black" 和 "brown"。  
**至于原来的数组 colors，其值仍然保持不变。**  



