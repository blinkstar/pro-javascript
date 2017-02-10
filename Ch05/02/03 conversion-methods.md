### 转换方法

如前所述，所有对象都具有 toLocaleString()、toString() 和 valueOf() 方法。  

其中，调用数组的 toString() 方法会返回由数组中每个值的字符串形式拼接而成的一个以逗号分隔的字符串。  
而调用 valueOf() 返回的还是数组。  

实际上，为了创建这个字符串**会调用数组**每一项的 toString()方法。来看下面这个例子。
     
	var colors = ["red", "blue", "green"];   // 创建一个包含3个字符串的数组
    alert(colors.toString());  // red,blue,green
    alert(colors.valueOf());  // red,blue,green
    alert(colors);

在这里，我们首先显式地调用了 toString()和valueOf()方法，  
以便返回数组的字符串表示，每个值的字符串表示拼接成了一个字符串，中间以逗号分隔。  
最后一行代码直接将数组传递给了alert()。  

由于 **alert() 要接收字符串参数**，所以它会在**后台调用 toString()方法**，  
由此会得到与直接调用toString()方法相同的结果。
     
另外，toLocaleString()方法经常也会返回与toString()和valueOf()方法相同的值，但也不总是如此。  
当调用数组的 toLocaleString()方法时，它也会创建一个数组值的以逗号分隔的字符串。  
而与前两个方法唯一的不同之处在于，这一次为了取得每一项的值，  
调用的是每一项的toLocaleString()方法，而不是toString()方法。请看下面这个例子。

	var person1 = {
    	toLocaleString: function(){
        	return "Nikolaos"; 
        },
        toString: function(){
        	return "Nicholas";
        }
    };
     
     
    var person2 = {
    	toLocaleString: function(){
        	return "Grigorios"; 
        },
        toString: function(){
        	return "Greg";
        }
    };
     
    var people = [person1, person2];
    alert(people); //  Nicholas,Greg
    alert(people.toString());  // Nicholas,Greg
    alert(people.toLocaleString());  // Nikolaos,Grigorios

我们在这里定义了两个对象：person1 和 person2 。  
而且还分别为每个对象定义了一个 toString()方法和一个 toLocaleString()方法，这两个方法返回不同的值。  
然后，创建一个包含前面定义的两个对象的数组。  
在数组传递给alert()时，输出结果是 "Nicholas,Greg"，因为调用了数组每一项的toString()方法   
(同样，这与下一行显示调用 toString()方法得到的结果相同)。  
而当调用数组的 toLocaleString()方法时，输出结果是 "Nikolaos,Grigorios"，  
原因是调用了数组的每一项的 toLocaleString() 方法。

数组继承的 toLocaleString()、toString() 和 valueOf() 方法，  
在默认情况下都会以逗号分隔的字符串的形式返回数组项。  

**而如果使用 join()方法**，则可以使用不同的分隔符来构建这个字符串。  
join()方法只接收一个参数，即用作分隔符的字符串，  
然后返回包含所有数组项的字符串。请看下面的例子：

	var colors = ["red", "green", "blue"];  
    alert(colors.join(","));          // red,green,blue
    alert(colors.join("||"));    // red||green||blue

在这里，我们使用 join()方法重现了 toString() 方法的输出。  
在传递逗号的情况下，得到了以逗号分隔的数组值。  
而在最后一行代码中，我们传递了双竖线符号，结果就得到了字符串 "red||green||blue"。  

**如果不给 join() 方法传入任何值，或者给它传入 undefined，则使用逗号作为分隔符。**  
IE7及更早版本会错误的使用字符串"undefined"作为分隔符。

如果数组中的某一项的值是 null 或者 undefined,  
那么该值在 join()、toLocaleString()、toString() 和 valueOf()方法  
返回的**结果中以空字符串表示**。


