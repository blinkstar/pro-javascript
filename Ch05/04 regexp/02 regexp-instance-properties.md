### RegExp 实例属性

RegExp 的每个实例都具有下列属性，通过这些属性可以取得有关模式的各种信息。  

 - global: 布尔值，表示是否设置了 g 标志。
 - ignoreCase: 布尔值，表示是否设置了 i 标志。
 - lastIndex：整数，表示开始搜索下一个匹配项的字符位置，从 0 算起。
 - multiline: 布尔值，表示是否设置了 m 标志。
 - source: 正则表达式的字符串表示，按照字面量形式而非传入构造函数中的字符串模式返回。

通过这些属性可以获知一个正则表达式的各方面信息，但却没有多大用处，  
因为这些信息全都包含在模式声明中。例如：

	var pattern1 = /\[bc\]at/i;
    console.log(pattern1.global);   // false
    console.log(pattern1.ignoreCase); // true
    console.log(pattern1.multiline);  // false
    console.log(pattern1.lastIndex);  // 0
    console.log(pattern1.source);  //    "\[bc\]at"

    var pattern2 = new RegExp("\\[bc\\]at", "i");
    console.log(pattern2.global);   // false
    console.log(pattern2.ignoreCase); // true
    console.log(pattern2.multiline);  // false
    console.log(pattern2.lastIndex);  // 0
    console.log(pattern2.source);  //    "\[bc\]at"

我们注意到，尽管第一个模式使用的是字面量，第二个模式使用了 RegExp 构造函数，  
但它们的 source 属性是相同的。  
可见，source 属性保存的是规范形式的字符串，即字面量形式所用的字符串。

