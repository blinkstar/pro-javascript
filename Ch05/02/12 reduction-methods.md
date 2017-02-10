### 缩小方法

`ECMAScript 5` 还新增了两个缩小数组的方法： reduce() 和 reduceRight()。  
这两个方法都会迭代数组的所有项，然后构建一个最终返回的值。  

其中，reduce() 方法从数组的第一项开始，逐个遍历到最后。  
而 reduceRight() 则从数组的最后一项开始，向前遍历到第一项。

这两个方法都接收两个参数：  
 - 一个在每一项上调用的函数  
 - 和(可选的)作为缩小基础的初始值。  
 
传给 reduce() 和reduceRight() 的函数接收4个参数：  
 - 前一个值、
 - 当前值、
 - 项的索引  
 - 和数组对象。
 
这个函数返回的任何值都会作为第一个参数自动传给下一项。  
第一次迭代发生在数组的第二项上，因此第一个参数是数组的第一项，第二个参数就是数组的第二项。

使用 reduce() 方法可以执行求数组中所有值之和的操作，比如：  

	var values = [1, 2, 3, 4, 5];
    var sum = values.reduce(function(prev, cur, index, array){
    	return prev + cur;
    });
    alert(sum);   // 15
     
第一次执行回调函数，prev 是 1，cur 是2。  
第二次，prev是 3 (1加2的结果)，cur是3(数组的第三项)。  
这个过程会持续到把数组中的每一项都访问一遍，最后返回结果。

reduceRight() 的作用类似，只不过方向相反而已。来看下面这个例子。

    var values = [1, 2, 3, 4, 5];
    var sum = values.reduceRight(function(prev, cur, index, array){
    	return prev + cur;
    });

在这个例子中，第一次执行回调函数，prev 是5 ，cur 是4 .  
当然，最终结果相同，因为执行的都是简单相加的操作。

使用 reduce() 还是 reduceRight()，主要取决于要从那头开始遍历数组。除此之外，它们完全相同。  

支持这两个缩小函数的浏览器有 IE9+ 、Firefox 3 +、Safari 4 +、Opera 10.5 和 Chrome。
     
