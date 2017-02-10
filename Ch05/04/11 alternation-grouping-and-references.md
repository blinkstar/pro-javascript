### 选择、分组和引用

正则表达式的语法还包括指定选择项、子表达式分组和引用前一子表达式的特殊字符。  

字符 `"|"` 用于分隔供选择的字符。  
例如， `/ab|cd|ef/` 可以匹配字符串 `"ab"`，  
也可以匹配字符串 `"cd"`，还可以匹配字符串 `"ef"` 。  

`/\d{3}|[a-z]{4}/` 匹配的是三位数字或者四个小写字母。  

注意，**选择项的尝试匹配次序是从左到右**，直到发现了匹配项。  
如果左边的选择项匹配，就**忽略**右边的匹配项，即使它产生更好的匹配。  
因此，当正则表达式 `/a|ab/` 匹配字符串 `"ab"` 时，它只能匹配第一个字符。

#### 正则表达式中的圆括号有多种作用。

一个作用是把单独的项组合成**子表达式**，以便可以像处理一个独立的单元那样  
用 `"|"` 、`"*"`、`"+"` 或者 `"?"` 等来对单元内的项进行处理。

例如， `/java(script)?/`  可以匹配字符串 `"java"`，其后可以有 `"script"` 也可以没有。  

`/(ab|cd)+|ef/` 可以匹配字符串 `"ef"`，  
也可以匹配字符串 `"ab"` 或 `"cd"` 的一次或多次重复。

在正则表达式中，圆括号的另一个作用是在完整的模式中定义**子模式**。  

当一个正则表达式成功地和目标字符串相匹配时，可以**从目标串中抽出和圆括号中的子模式相匹配的部分**。  

例如，假定我们正在检索的模式是一个或多个小写字母后面跟随了一位或多位数字，  
则可以使用模式  `/[a-z]+\d+/` 。  

但假定我们真正关心的是每个匹配尾部的数字，  
那么如果将模式的数字部分放在括号中 `(/[a-z]+(\d+)/)` ，  
就可以从检索到的匹配中抽取数字了。

带圆括号的表达式的另一个用途是允许在同一个正则表达式的后部引用前面的子表达式。  

这是通过在字符 `"\"` 后**加一位或多位数字**来实现的。  
这个数字指定了带圆括号的子表达式在正则表达式中的位置。  

例如，`\1`引用的是第一个带圆括号的子表达式，  
`\3`引用的是第三个带圆括号的子表达式。  

注意，因为子表达式可以嵌套另一个子表达式，所以它的位置是**参与计数的左括号的位置**。    

例如，在下面的正则表达式中，嵌套的子表达式 `([Ss]cript)` 可以用 `\2`来指代：  
     
	/([Jj]ava([Ss]cript)?)\sis\s(fun\w*)/

对正则表达式中前一个子表达式的引用，并不是指对子表达式模式的引用，而指的是**参与那个模式相匹配的文本**的引用。  
这样，引用可以用于实施一条**约束**，即一个字符串各个单独部分包含的是**完全相同**的字符。  

例如，下面的正则表达式匹配的就是位于单引号或双引号之内的0个或多个字符。  
但是，它并不要求左侧和右侧的引号匹配 (即，加入的两个引号都是单引号或都是双引号)：  

	/['"][^'"]*['"]/

如果要匹配左侧和右侧的引号，可以使用如下的引用：  

	/(['"])[^'"]*\1/

`\1` 匹配的是第一个带圆括号的子表达式所匹配的模式。  

在这个例子中，存在这样一条约束，那就是左侧的引号必须和右侧的引号相匹配。  
正则表达式不允许用双引号括起的内容中有单引号，反之亦然。  

**不能在在字符类中使用这种引用**，所以下面的写法是**非法**的：  

	/(['"])[^\1]*\1/

同样，在正则表达式中**不用创建带数字编码的引用**，也可以对子表达式进行分组。    
它不是以 `"("` 和 `")"` 进行分组，而是以 `"(?:"` 和 `")"` 来进行分组，    
比如，考虑下面这个模式：  

	/([Jj]ava(?:[Ss]cript)?)\sis\s(fun\w*)/

这里，子表达式 `(?:[Ss]cript)` **仅仅用于分组**，因此复制符号 `"?"` 可以应用到各个分组。  
这种改进的圆括号**并不生成引用**，所以在这个正则表达式中，`\2`引用了与 `(fun\w*)` 匹配的文本。  

表4 正则表达式的选择、分组和引用字符

<table>
	<thead>
		<tr><th>字符</th><th>含义</th></tr>
	</thead>
	<tbody>
		<tr><td>|</td><td>选择，匹配的是该符号左边的子表达式或右边的子表达式</td></tr>
		<tr><td>(...)</td><td>组合，将几个项组合为一个单元，这个单元可通过 "*"、"+"、"?"、 和 "|" 等符号加以修饰，而且可以记住和这个组合相匹配的字符串以供此后的引用使用</td></tr>
		<tr><td>(?:...)</td><td>只组合，把项目组合到一个单元，但不记忆与该组相匹配的字符</td></tr>
		<tr><td>\n</td><td>和第n个分组第一次匹配的字符相匹配，组是圆括号中的子表达式 (也有可能是嵌套的)，组索引是从左到右的左括号数，"(?:"形式的分组不编码</td></tr>
	</tbody>
</table>
      