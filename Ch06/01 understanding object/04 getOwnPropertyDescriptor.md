#### 读取属性的特性

使用 ECMAScript 5 的 Object.getOwnPropertyDescriptor() 方法，可以取得给定属性的描述符。  

这个方法接收两个参数：  
 - 属性所在的对象   
 - 和要读取其描述符的属性名称。  
 
返回值是一个对象，  
 - 如果是访问器属性，这个对象的属性有 configurable、enumerable、get 和 set ；  
 - 如果是数据属性，这个对象的属性有 configurable、enumerable、writable 和 value 。  
 
例如：
     
	var book = {};
     
    Object.defineProperties(book, {
    	_year: {
        	value: 2004
        },
        edition: {
        	varlue: 1
        },
        year: {
        	get: function(){
            	return this._year;
            },
            set: function(newValue){
            	if(newValue > 2004){
                	this._year = newValue;
                    this.edition += newValue - 2004;
                }
            }
        }
});

var descriptor = Object.getOwnPropertyDescriptor(book, "_year");
console.log(descriptor.value);  // 2004
console.log(descriptor.configurable);  // false
console.log(typeof descriptor.get);   // "undefined"
     
var descriptor = Object.getOwnPropertyDescriptor(book, "year");
console.log(descriptor.value);  // undefined
console.log(descriptor.configurable);  // false
console.log(typeof descriptor.get);   // "function"
     
对于数据属性 _year，value 等于最初的值，configurable 是 false，而 get 等于 undefined 。  
对于访问器属性 year ，value 等于 undefined，enumerable 是 false，  
而get 是一个执行 getter 函数的指针。  

在 JavaScript 中，可以针对任何对象 -- 包括 DOM  和 BOM 对象，使用 Object.getOwnPropertyDescriptor() 方法。  
支持这个方法的浏览器有 IE9+、Firefox 4+ 、 Safari 5 + 、Opera 12 + 和 Chrome 。  

