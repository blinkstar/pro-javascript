### 字符串位置方法

有两个可以从字符串中查找子字符串的方法： indexOf() 和 lastIndexOf()。  
这两个方法都是从一个字符串中搜索给定的子字符串，然后返回子字符串的位置  
(如果没有找到该子字符串，则返回 -1)。  

这两个方法的区别在于：
 - indexOf()方法从字符串的开头向后搜索子字符串，  
 - 而lastIndexOf()方法是从字符串的末尾向前搜索子字符串。  
 
还是来看一个例子吧。

	var stringValue = "hello world";
    alert(stringValue.indexOf("o"));  // 4
    alert(stringValue.lastIndexOf("o")); // 7

子字符串"o"第一次出现的位置是4，即 "hello" 中的 "o"；  
最后一次出现的位置是7，即 "world"中的 "o"。  
如果"o"在这个字符串中仅出现了一次，那么 indexOf()和lastIndexOf()会返回相同的位置值。  

这两个方法都可以接收可选的第二个参数，**表示从字符串中的哪个位置开始搜索。**  
换句话说，indexOf()会从该参数指定的位置向后搜索，忽略该位置之前的所有字符；  
而lastIndexOf()则会从指定的位置向前搜索，忽略该位置之后的所有字符。看下面的例子。  
     
	var stringValue = "hello wolrd";
    alert(stringValue.indexOf("o", 6));   // 7
    alert(stringValue.lastIndexOf("o", 6));  // 4

在将第二个参数6传递给这两个方法之后，得到了与前面例子相反的结果。  
这一次，由于 indexOf()是从位置6(字母"w")开始向后搜索，结果在位置7找到了 "o"，因此它返回 7。  
而 lastIndexOf() 是从位置6开始向前搜索。结果找到了 "hello" 中的 "o"，因此它返回4 。  
在使用第二个参数的情况下，可以通过循环调用 indexOf() 或 lastIndexOf() 来找到所有匹配的子字符串，如下面的例子所示：
     
	var stringValue = "Lorem ipsum dolor sit amet, consectetur adipisicing elit";
    var position = new Array();
    var pos = stringValue.indexOf("e");

    while(pos > -1) {
    	position.push(pos);
        pos = stringValue.indexOf("e", pos+1)
    }
    alert(positoin);

这个例子通过不断增加 indexOf() 方法开始查找的位置，遍历了一个长字符串。  
在循环之外，首先找到了 "e" 在字符串中的初始位置；  
而进入循环后，则每次都给 indexOf() 传递上一次的位置加 1 。  
这样，就确保了每次新搜索都从上一次找到的子字符串的后面开始。  
每次搜索返回的位置依次被保存在数组 positions 中，以便将来使用。  


