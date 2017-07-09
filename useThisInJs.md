# js中this的用法
我在工作中尝试用内联的方法把事件写进控件中，像这样
`<button type="button" onclick="changeColor()">buy</button>`

然后js中:  
  
	function changeColor() {  
		$(this).toggle("blue");  
	}  


我发现点击按钮并不能实现变色，查出来的结果是$(this)其实在这里并不是我想指向的button而是Window对象，于是我去研究了this的用法

this是面向对象语言中的一个重要概念，在JAVA,C#等大型语言中，this固定指向运行时的当前对象。但是在javascript中，由于 javascript的动态性（解释执行，当然也有简单的预编译过程），this的指向在运行时才确定。这个特性在给我们带来迷惑的同时也带来了编程上的 自由和灵活，结合apply(call)方法，可以使JS变得异常强大。
## 变化的this 
在JavaScript中，this通常指向的是我们正在执行的函数本身，或者是指向该函数所属的对象（运行时）。当我们在页面中定义了函数 doSomething()的时候，它的owner是页面，或者是JavaScript中的window对象（或 global对象）。对于一个onclick属性，它为它所属的HTML元素所拥有，this应该指向该HTML元素。 
### 在几种常见场景中this的变化   
函数示例   

	function doSomething () {           
		alert(this.navigator); //appCodeName    
		this.value = "I am from the Object constructor";    
		this.style.backgroundColor = "# 000000";    
	}  
1. (A)作为普通函数直接调用时，this指向window对象
2. (B)作为控件事件触发时:  
	1) inline event registration 内联事件注册 .将事件直接写在HTML代码中(<element onclick=”doSomething()”>), 此时this指向 window对象 。
	2)Traditional event registration 传统事件注册 （DHTML方式）. 形如 element.onclick = doSomething; 此时this指向 element对象 
	3） <element onclick=”doSomething(this)”>作为参数传递可以指向element 
3. (C)作为对象使用时this指向当前对象。形如：new doSomething(); 
4. (D)使用apply 或者call方法时，this指向所传递的对象。 
形如：var obj={}; doSomething.apply(obj,new Array(”nothing”); //thisàobj   
### 如何在事件处理中来使用this  
#### 在函数doSomething()中this所指的是什么？  
js代码  
  
	function doSomething() {   
		this.style.color = '#cc0000';   
	}   
	function doSomething() {   
		this.style.color = '#cc0000';   
	} 
 在JavaScript中，this通常指向的是我们正在执行的函数本身（译者注：用owner代表this所指向的内容），或者是，指向该函数所属的对象。当我们在页面中定义了函数doSomething()的时候，它的owner是页面，或者是JavaScript中的window对象（或 global对象）。对于一个onclick属性，它为它所属的HTML元素所拥有，this应该指向该HTML元素。 
这种“所有权”就是JavaScript中面向对象的一种方式。在Objects as associative arrays中可以查看一些更多的信息。 如果我们在没有任何更多准备情况下执行doSomething()，this关键字会指向window，并且该函数试图改变window的 style.color。因为window并没有style对象，这个函数将非常不幸的运行失败，并产生JavaScript错误。   
##### Copying  
因此如果我们想充分利用this，我们不得不注意使用this的函数应该被正确的HTML元素所拥有。换句话说，我们应该复制这个函数到我们的onclick属性。Traditional event registration会关心它。   
Javascript代码  

	element.onclick = doSomething; 
	element.onclick = doSomething;   
这个函数被完整复制到onclick属性（现在成为了函数）。因此如果这个event handler被执行，this将指向HTML元素，并且该元素的颜色得以改变。这种方法使得我们能够复制这个函数到多个event handler。每次this都将指向正确的HTML元素。这样你就可以最大限度使用this。每当执行该函数，this所指向的HTML元素都正确响应事件，这些HTML元素拥有doSomething()的一个拷贝。  
##### Referring  
然而，如果你使用inline event registration(内联事件注册)   
Javascript代码  
 
	<element onclick="doSomething()"> 
	<element onclick="doSomething()">   
你将不能拷贝该函数！反而这种差异是非常关键的。onclick属性并不包含实际的函数，仅仅是一个函数调用。     
Javascript代码   

	doSomething(); 
	doSomething(); 
因此，它将声明“转到doSomething()并且执行它”。当我们到达doSomething()，this关键字又重新指向了全局的window对象，函数返回错误信息。  
##### The differnce  
如果你想使用this来指向HTML元素响应的事件，你必须确保this关键字被写在onclick属性里。只有在这种情况下它才指向event handler所注册的HTML元素。   
Javascript代码  
 
	element.onclick = doSomething; 
	alert(element.onclick) 
	element.onclick = doSomething; 
	alert(element.onclick) 
你将得到   
Javascript代码  
   
	function doSomething() { 
		this.style.color = '#cc0000'; 
	} 
	function doSomething() { 
		this.style.color = '#cc0000'; 
	}   

正如你所见，this关键字被展现在onclick函数中，因此它指向HTML元素。   
但是如果执行   
Javascript代码  
 
	<element onclick="doSomething()"> 
	alert(element.onclick) 
	<element onclick="doSomething()"> 
	alert(element.onclick)  
 
你将得到   
Javascript代码  
 
	function onclick() { 
		doSomething() 
	} 
	function onclick() { 
		doSomething() 
	}  
 
这仅仅是到doSomething()函数的一个引用。this关键字并没有出现在onclick函数中，因此它不指向HTML元素。   
例子--拷贝   
下面的例子中，this被写入onclick函数里：   
Javascript代码   

	element.onclick = doSomething 
	element.addEventListener('click', doSomething, false) 
	element.onclick = function() {this.style.color = '#cc0000';} 
	<element onclick="this.sytle.color = '#cc0000';"> 
	element.onclick = doSomething 
	element.addEventListener('click', doSomething, false) 
	element.onclick = function() {this.style.color = '#cc0000';} 
	<element onclick="this.sytle.color = '#cc0000';">  
 
例子--引用   
下述情况中，this指向window：   
Javascript代码   

	element.onclick = function() {doSomething()} 
	element.attachEvent('onclick', doSomething) 
	<element onclick="doSomething()"> 
	element.onclick = function() {doSomething()} 
	element.attachEvent('onclick', doSomething) 
	<element onclick="doSomething()">  
 
注意attachEvent()的出现。Microsoft event registration model最主要的弊端是attachEvent()创建了一个指向函数的引用，而不是复制它。因此有时不可能知道哪个HTML正在处理该事件。   
组合使用   
当使用内联事件注册时，你可以将this发送到函数以至于可以正常使用：   
Javascript代码  
 
	<element onclick="doSomething(this)"> 
	function doSomething(obj) { 
	//this出现在event handler中并被发送到函数 
	//obj指向HTML元素，因此可以这样： 
		obj.style.color = '#cc0000'; 
	}
