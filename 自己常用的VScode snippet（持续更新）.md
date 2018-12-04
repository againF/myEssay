# 自己常用的VScode snippet（持续更新）
作者：吴业飞
时间：2018年12月4日  


---
在VScode里编辑自己的代码段（snippet），Ctrl + Shift + p,输入snippet,首选项：配置用户代码片段。
## html.json
	{
		// Place your snippets for html here. Each snippet is defined under a snippet name and has a prefix, body and 
		// description. The prefix is what is used to trigger the snippet and the body will be expanded and inserted. Possible variables are:
		// $1, $2 for tab stops, $0 for the final cursor position, and ${1:label}, ${2:another} for placeholders. Placeholders with the 
		// same ids are connected.
		// Example:
		// "Print to console": {
		// 	"prefix": "log",
		// 	"body": [
		// 		"console.log('$1');",
		// 		"$2"
		// 	],
		// 	"description": "Log output to console"
		// }
		"dump": {
			"prefix": "dump",
			"body": [
				"<?php dump($1);?>",
				"$2"
			],
			"description": "Log output to console"
		},
		"foreach": {
			"prefix": "foreach",
			"body": [
				"{foreach name='$1' item='vo' key='k'}$3{/foreach}"
			],
			"description": "thinkPHP5 foreach"
		},
		"swiperHTML": {
			"prefix": "swiperHTML",
			"body": [
			"<div class='swiper-container'>",
				"    <div class='swiper-wrapper'>",
					"        <div class='swiper-slide'>Slide 1</div>",
					"        <div class='swiper-slide'>Slide 2</div>",
					"        <div class='swiper-slide'>Slide 3</div>",
				"    </div>",
				"    <div class='swiper-pagination'></div>",
				"    <div class='swiper-button-prev'></div>",
				"    <div class='swiper-button-next'></div>",
				"    <div class='swiper-scrollbar'></div>",
			"</div>"
			],
			"description": "swiper init html"
		},
		"swiperJS": {
			"prefix": "swiperJS",
			"body": [
				"<script>        ",
				"var mySwiper = new Swiper ('.swiper-container', {",
				  "    direction: 'vertical', // 垂直切换选项",
				  "    loop: true, // 循环模式选项",
				  
				  "    // 如果需要分页器",
				  "    pagination: {",
					"    el: '.swiper-pagination',",
				  "    },",
				  
				  "    // 如果需要前进后退按钮",
				  "    navigation: {",
					"    nextEl: '.swiper-button-next',",
					"    prevEl: '.swiper-button-prev',",
				  "    },",
				  
				  "    // 如果需要滚动条",
				  "    scrollbar: {",
					"    el: '.swiper-scrollbar',",
				  "    },",
				"})        ",
				"</script>",
			],
			"description": "swiper init JS"
		}
	}

---

版权声明：自由转载-非商用-非衍生-保持署名
