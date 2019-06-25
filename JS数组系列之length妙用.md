# JS数组系列之length妙用
时间： 2019年6月25日  
作者：Alan    

-----
## 黑科技
### length的妙用
数组的length不是只读的。所以我们可以通过length完成  
【1】从数组末尾移除项  
【2】在数组末尾添加新项  
【3】清空数组  

		/***
		 * 从数组末尾移除项
		 * **/
		var colors = ["red", "blue", "green"]; // 创建一个包含3个字符串的数组
		colors.length = 2;
		alert(colors[2]); // undefined  

		/***
		 * 在数组末尾添加新项
		 * **/
		var colors = ["red", "blue", "green"]; // 创建一个包含3个字符串的数组
		colors[colors.length] = "black"; // (在位置3)添加一种颜色
		colors[colors.length] = "brown"; // (在位置4)再添加一种颜色  

		/***
		 * 清空数组
		 * **/
		var colors = ["red", "blue", "green"]; // 创建一个包含3个字符串的数组
		colors.length = 0;
		console.log(colors); // []

### 参考文献
【1】《JavaScript高级程序设计》（第3版）

---

版权声明：自由转载-非商用-非衍生-保持署名
