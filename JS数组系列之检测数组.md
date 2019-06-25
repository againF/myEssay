# JS数组系列之检测数组
时间： 2019年6月25日  
作者：Alan    

-----


## 检测数组
要检测某个对象是不是数组，我们可以用 
 
	/***
	 * 检测数组
	 * **/
	function isArray(value) {
	    if(value instanceof Array) {
	        return true;
	    }
	}
#### 适用条件：  
对于一个网页，或者一个全局作用域可以放心使用。

#### 存在的问题：  
`instanceof`操作符假定单一的全局执行环境。如果一个页面包含多个frame,也就意味着存在多个不同的全局执行环境，即存在多个不同版本的`Array`构造函数。也就是说，如果你从一个框架往另一个框架传入一个数组，那么传入的数组与第二个框架中原生创建的数组分别具有各自不同的构造函数。`value instanceof Array`要返回`true`, `value`必须是数组，而且还必须与`Array`构造函数在同一个全局作用域内。（Array是window的属性！）如果`value`是在另一个`frame`中定义的数组，那么以上代码会返回`false`。
### 替代方案
为了解决`instanceof`存在的问题，ECMAScript5新增了`Array.isArray()`方法。这个方法的目的是最终确定某个值到底是不是数组，而不管它是在哪个全局执行环境中创建的。  

	/***
	 * 检测数组
	 * **/
    if(Array.isArray(value)) {
        // do something
    }
#### 兼容性：  
IE9+, Firefox 4+, Safari 5+, Opera 10.5+, Chrome  
又是IE拖了后腿，为了解决兼容性问题和作用域问题，我们可以用以下的终极方法  
### 终极方案
	/***
	 * 检测数组
	 * **/
	function isArray(value) {
	    return Object.prototype.toString.call(value) === "[object Array]";
	}
#### 原理分析
在任何值上调用Object原生的`toString()`方法，都会返回一个`[object NativeConstructorName]`格式的字符串。每个类在内部都有一个`[[Class]]`属性，这个属性中就指定了上述字符串中的构造函数名。由于原生数组的构造函数名与全局作用域无关，所以用`toString()`方法就能保证返回一致的值。
##### tips
`Object.prototype.toString()`可能会被修改，这里讨论的技巧假设`Object.prototype.toString()`是未被修改过的原生版本。  

### 参考文献
【1】《JavaScript高级程序设计》（第3版）

---

版权声明：自由转载-非商用-非衍生-保持署名
