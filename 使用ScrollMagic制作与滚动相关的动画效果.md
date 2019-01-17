# 使用ScrollMagic制作与滚动相关的动画效果
作者：吴业飞  
时间：2019年1月17日   
 
---
# 背景
经常看到一些国外动效做的特别炫的网站使用的是ScrollMagic这个js库，于是我决定写个demo试用一下。
# 需求
产品详情页的侧边分类导航要实现滚动到页面顶部转为固定效果。
# 例子  
	<!DOCTYPE html>
	<html lang="en">
	<head>
	    <meta charset="UTF-8">
	    <meta name="viewport" content="width=device-width, initial-scale=1.0">
	    <meta http-equiv="X-UA-Compatible" content="ie=edge">
	    <title>ScrollMagicDemo</title>
	    <style>
	        html,body {
	            margin: 0;
	            padding: 0;
	        }
	        .banner {
	            background: #ccc;
	            height: 500px;
	        }
	        .section {
	            padding: 100px 15px;
	            background: rgba(0, 0, 255, 0.521);
	            height: 2000px;
	        }
	        .side-bar {
	            position: absolute;
	            width: 200px;
	            height: 300px;
	            background: rgb(245, 96, 96);
	        }
	        .content {
	            height: 2000px;
	            background: gray;
	            padding-left: 200px;
	        }
	    </style>
	</head>
	<body>
	    <div class="banner">
	        <span class="start-point">1</span>
	        Banner
	    </div>
	    <div class="section">
	        <div class="side-bar">side-bar</div>
	        <div class="content">content</div>
	    </div>
	    <script src="./../node_modules/scrollmagic/scrollmagic/minified/ScrollMagic.min.js"></script>
	    <script>
	        var controller = new ScrollMagic.Controller();
	        var scene = new ScrollMagic.Scene({
	            triggerElement: '.section',//触发元素
	            triggerHook: "onLeave",//触发元素开始离开视口时触发
	            offset: 100,//从开始点滚动多少px触发（施法前摇）
	            duration: 0//效果持续的距离（法术持续时间/距离）
	
	        }).setPin(".side-bar");//固定需要固定的元素
	
	        controller.addScene(scene);
	    </script>
	</body>
	</html>
# 后记
本文只是抛砖引玉，后续还有ScrollMagic + GSAP的组合制作炫酷动画需要去尝试。
#  文档速查 
【1】[ScrollMagic的官方Api文档](http://scrollmagic.io/docs/index.html)

---

版权声明：自由转载-非商用-非衍生-保持署名
