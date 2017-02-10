### 位置方法

`ECMAScript 5` 为数组实例添加了两个位置方法: `indexOf()` 和 `lastIndexOf()` 。  

这两个方法都接收两个参数：**要查找的项**和(可选的)表示**查找起点**位置的索引。  

其中，indexOf()方法从数组的开头(位置0)开始向后查找，lastIndexOf()方法则从数组的末尾开始向前查找。

这两个方法都返回要查找的项在数组中的位置，或者在没找到的情况下返回 -1 。  

在比较第一个参数与数组中的每一项时，会使用**全等操作符**；  
也就是说，要求查找的项必须严格相等 (就像使用 === 一样)。以下是几个例子。   

	var numbers = [1, 2, 3, 4, 5, 4, 3, 2, 1];
    alert(numbers.indexOf(4));        // 3
    alert(numbers.lastIndexOf(4));    // 5
    alert(numbers.indexOf(4, 4));     // 5
    alert(numbers.lastIndexOf(4, 4)); // 3

    var person = {name: "Nicholas"};
    var people = [{name: "Nicholas"}];
     
    var morePeople = [person];
    alert(people.indexOf(person));   // -1
    alert(morePeople.indexOf(person));  //0

使用 indexOf() 和 lastIndexOf() 方法查找特定项在数组中的位置非常简单，  
支持它们的浏览器包括 IE9+、Safari 3+、Opera 9.5+ 和 Chrome
