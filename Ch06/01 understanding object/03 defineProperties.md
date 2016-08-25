#### 定义多个属性

由于为对象定义多个属性的可能性很大，ECMAScript 5 又定义了一个 Object.defineProperties() 方法。  

利用这个方法可以通过描述符一次定义多个属性。  

这个方法接收两个对象参数：  
 - 第一个对象是要添加和修改其属性的对象，  
 - 第二个对象的属性与第一个对象中要添加或修改的属性一一对应。  
 
例如：

	var book = {};

    Object.defineProperties(book, {
    	_year: {
        	value: 2004
        },
        edition: {
        	value: 1
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

以上代码在 book 对象上定义了**两个数据属性** (_year 和 edition) 和**一个访问器属性** (year) 。  

最终的对象与上一节中定义的对象相同。唯一的区别就是这里的属性都是在同一时间创建的。  

支持 Object.defineProperties() 方法的浏览器有   
IE9+ 、Firefox 4+ 、Safari 5+ 、Opera 12 + 和 Chrome 。

