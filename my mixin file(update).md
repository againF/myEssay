# 自己常用的mixin（持续更新）
作者：吴业飞
时间：2018年12月4日  


---

	/*
	*列表展示的项目
	*param {
		$width: 百分比，一行展示4个用25%，以此类推，
		$marginRight：项目水平间距，单位px
	}
	*/
	@mixin width-box($width, $marginRight: 0px) {
		width: calc(#{$width} - #{$marginRight});
		display: inline-block;
		vertical-align: top;
		margin-right: $marginRight;
	}
	/*
	*背景图片
	*param {
		$url: string
	}
	*/
	@mixin background-image($url) {
		background-image: url($url);
		background-position: center;
		background-size: cover;
		background-repeat: no-repeat;
	}
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
	/*
	*a标签模拟按钮
	*param {
		display: inline-block;
		$fontSize: 
		$lineHeight: 
		$fontFamily: 
		$color: 
		$padding: 
	}
	*/
	@mixin button($fontSize, $lineHeight, $fontFamily, $color, $padding) {
		display: inline-block;
		font-size: $fontSize;
		line-height: $lineHeight;
		font-family: $fontFamily;
		color: $color;
		padding: $padding;
	}

---

版权声明：自由转载-非商用-非衍生-保持署名
