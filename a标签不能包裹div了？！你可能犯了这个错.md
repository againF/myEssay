# a标签不能包裹div了？！你可能犯了这个错
作者：吴业飞  
时间：2019年1月8日   
 
---
# 背景
本文记录了一次发现bug解决bug的过程。
# 需求
要求在整个全屏banner都能点击跳转页面，而不是点击banner上的按钮才跳转
# 问题
一拿到这个需求不以为然，因为太常规了，但是后面发生的事让我百思不得其解。我的代码结构原来大概是这样的  

	<div class="banner">
        <!-- some code here -->
        <a href="#">go to some where</a>
    </div>
现在要整个banner都能点击嘛，那外层包个a标签不就行了，于是我这样写  

	<a href="#">
	    <div class="section">
	        <!-- some code here -->
	        <a href="#">go to some where</a>
	    </div>
	</a>
很正常对不对，然而页面上渲染成了这样  

	<a href="#"></a>
	<div class="banner">
		<a href="#">
	    	<!-- some code here -->
	    </a>
		<a href="#">go to some where</a>
	</div>
这是什么鬼，我明明只写了一个a准备包裹banner,为什么自动生成了两个，还没包裹成功。然后我发现这个banner是`position: absolute;`的，我觉得我可能找到问题所在了，a标签不能包裹定位元素！于是我做了个实验  

	<a href="#">
	    <div style="position: absolute;">test</div>
	</a>  
结果渲染结果符合预期  

	<a href="#">
	    <div style="position: absolute;">test</div>
	</a>  
这下怎么办，到底是什么原因导致的渲染异常。此时我的心情就像看到1 + 1 不等于2一样，看起来多么简单多么正常的一个问题结果却不符合你的预期。我站起身，仰望45度的天空，思考片刻，想起了我的C语言启蒙老师的一句话“不要质疑编译器，它报错一定是你的错”，我静下心来默默打开了W3C的官网，我去直接查规范！看着W3C那几乎纯文字的排版，密密麻麻，强忍着找到了a标签的相关说明，有这么一句话  

>The a element may be wrapped around entire paragraphs, lists, tables, and so forth, even entire sections, so long as there is no interactive content within (e.g., buttons or other links).   

翻译过来就是
>只要在其中没有交互式内容（例如，按钮或其他链接），a元素可以围绕整个段落，列表，表格等，甚至整个部分。  
  
这个说的不就是我么！我的结构是  

	<a href="#">
	    <div class="banner">
			some code here
	        <a href="#">go to some where</a>
	    </div>
	</a>  
banner里有个链接！规范里说了，链接里不能套链接！
接着把内部链接删掉后，一切正常了。
# 后记
这个知识点应该在最早学习的时候学到过，但是平时工作中真的很少碰到这个链接里套链接的问题，所以也就遗忘了，在问题出现的时候没有一眼看出问题所在，老话说的好，温故而知新，谨记！
#  参考文献  
【1】《HTML 5.2
W3C Recommendation, 14 December 2017》，[https://www.w3.org/TR/html52/textlevel-semantics.html#the-a-element](https://www.w3.org/TR/html52/textlevel-semantics.html#the-a-element)

---

版权声明：自由转载-非商用-非衍生-保持署名
