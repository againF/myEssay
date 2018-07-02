# Media Query Break Point
作者：吴业飞
时间：2018.07.02

自己总结的做移动端适配时的媒体查询断点写法  

	
	/*media query break point
	*Author: Alan
	*Date: 2018.07.02
	*/
	
	// mobile:442px*870px
	
	/*Phone            Resolution
	*Galaxy S5         360*640
	*Pixel2            411*731
	*Pixel2 XL         411*823
	*iPhone 5/SE       320*568
	*iPhone 6/7/8      375*667
	*iPhone 6/7/8 Plus 417*736
	*iPhone X          375*812
	*iPad              768*1024
	*iPad Pro          1024*1366
	*/
	
	/*Break Point
	*417
	*411
	*375
	*360
	*320
	*/
	
	/*
	*This template use like this:
	*首先将iPhone 5/SE 320*568作为基础参照，把样式写在@media (min-width: 0px) and (max-width: 443px)中，
	*即将最小分辨率下的样式作为基础样式
	*做完iPhone 5/SE 320*568适配接下来其他的手机将个别要改动的样式写在对应断点中
	*Note: 这个文件中没做pad的适配，因为在我的实践中将pad的适配单独提取出来了
	*/
	//global
	@media (min-width: 0px) and (max-width: 443px) {}
	// iPhone 6/7/8 Plus 417*736
	@media (min-width: 413px) and (max-width: 418px) {}
	// Pixel2            411*731
	// Pixel2 XL         411*823
	@media (min-width: 377px) and (max-width: 412px) {}
	// iPhone 6/7/8      375*667
	@media (min-width: 362px) and (max-width: 376px) {}
	// Galaxy S5         360*640
	@media (min-width: 322px) and (max-width: 361px) {}
	// iPhone 5/SE       320*568
	@media (min-width: 0px) and (max-width: 321px) {}
	
	
	



---

版权声明：自由转载-非商用-非衍生-保持署名
