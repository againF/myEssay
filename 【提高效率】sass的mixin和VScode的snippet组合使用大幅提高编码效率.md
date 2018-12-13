# 【提高效率】sass的mixin和VScode的snippet组合使用大幅提高编码效率
作者：吴业飞  
时间：2018年12月13日   
 
---
## 背景
在日常编写前端代码时，会发现一些经常出现的代码组合，本着DRY(Don't repeat yourself)原则，我发现了sass的mixin和VScode的snippet组合使用可以大幅提高编码效率。
## 应用场景
举一个简单的例子。比如现在我们需要加一个标题样式，我们可能会写如下CSS代码  

	.title {
	  font-size: 60px;
	  line-height: 1;
	  font-family: "Lato-Bold";
	  color: #fff;
	  margin-bottom: 15px;
	}
注意到我们用到了5个属性，很明显，一个网站里我们需要设置很多的文字类样式，也就是说我们每次都得重复写上面的5个属性，是不是感觉很枯燥很低效。有用过Sass之类工具的同学可能想到了写Mixin将上面的给文字设置样式的代码封装起来，我们可能会得到如下代码：  
  
	/*
	*文本基本设置
	*param {
		$fontSize: 
		$lineHeight: 
		$fontFamily: 
		$color: 
		$marginBottom: 
	}
	*/
	@mixin text($fontSize, $lineHeight, $fontFamily, $color, $marginBottom: 0px) {
		font-size: $fontSize;
		line-height: $lineHeight;
		font-family: $fontFamily;
		color: $color;
		margin-bottom: $marginBottom;
	}  
现在我们的sass文件里可能是这样为`.title`设置样式的  

	.title {
	    @include text(60px, 1, 'Lato-Bold', #fff, 15px);
	}
相比上面的写5个属性5行代码我们现在只要写一行代码就可以了！是不是很爽写起来！其实这没有什么新鲜的，用过Sass可能早就体验过了，我也是在用了一段时间这种写法后发现还是嫌麻烦，能不能再简单点！我想到了Snippet!自定义代码块，一键生成   
 
	.title {
	    @include text(px, px, '', #, px);
	}  
在VScode里编辑自己的代码段（snippet），Ctrl + Shift + p,输入snippet,首选项：配置用户代码片段。比如我们编辑`scss.json`文件  
 
	"title": {
		"prefix": "title",
		"body": [
			".title {",
				"    @include text(px, px, '', #, px);",
			"}"
		],
		"description": "set class title"
	}  
现在我们有了Snippet,意味着我们在sass里只要敲`title`按下`tab`键，我们就有了如下结构  

	.title {
	    @include text(px, px, '', #, px);
	}   
接下来我们要做的只是按照设计稿填参数就行了！
## 写在最后
本文只是抛砖引玉，这个技巧是我在最近一个项目中灵光一闪发现的，我的mixin和snippet文件也在持续更新中，在项目里发现可以提取出来的代码都会陆续封装起来，效率也在一直提升，也许还有更好的工作流程等待我去发现，没关系，在实践总学习吧，争取早日找到最佳实践！
	
---

版权声明：自由转载-非商用-非衍生-保持署名
