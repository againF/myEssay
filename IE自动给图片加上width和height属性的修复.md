# IE自动给图片加上width和height属性的修复
作者：吴业飞  
时间：2018.07.25

## 情景再现
在项目中写了一个图片列表，再普通不过的一行3张图，用的是栅格布局，`html`代码大概如下

		<div class="row">
		  <div class="col-md-4"><img src="" alt=""></div>
		  <div class="col-md-4"><img src="" alt=""></div>
		  <div class="col-md-4"><img src="" alt=""></div>
		</div>
在全局CSS我是申明了

		img {
		    max-width: 100%;
		}
按照预期不管图片尺寸怎样应该是自动填充满容器达到自适应效果的，在Chrome下确实也是一切正常，可是在IE下（测试版本IE10），发现IE自作聪明地把图片原始尺寸加到了`img`标签上，像这样`<img width="750px" height="750px">`,这样一来虽然还是一行3张图没毛病但是图片以原始尺寸显示被挤压地很丑，没有等比缩放。不管这是特性还是bug，都得修复！
## 解决方案
在靠近`</body>`的地方加上

	<script>
	    window.onload = function () {
	    // fix bug for IE auto add width/height at img
	    var img = document.getElementsByTagName("img");
	    var len = img.length;
	    for(var i = 0;i < len;i++) {
	      img[i].removeAttribute("width");
	      img[i].removeAttribute("height");
	    }
  	</script>
原理就是在图片渲染完后清除图片上的width和height属性。










---

版权声明：自由转载-非商用-非衍生-保持署名
