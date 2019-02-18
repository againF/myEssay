# 使用Babel将ES6+转换成ES5
作者：吴业飞  
时间：2019年2月18日   
 
---
## 环境，版本信息
node: v8.11.1  
npm: v6.5.0  
babel: v7.3.0  
## 安装
npm install --save-dev @babel/core @babel/cli @babel/preset-env  

npm install --save @babel/polyfill  
  
这里特别说明一下，这两条安装命令是babel官网上的，我在实际安装过程中使用VScode里的终端，会报错，原因是不识别`@`，只要加上`""`就可以了，像这样  

npm install --save-dev '@babel/core' '@babel/cli' '@babel/preset-env'  

npm install --save '@babel/polyfill'  

## 配置
在项目根目录创建`.babelrc`文件  

	{
	    "presets": [
	      [
	        "@babel/preset-env",
	        {
	          "useBuiltIns": "entry"
	        }
	      ]
	    ]
	  }

## 运行
假设目录结构是  

	dist
		js
	src
		js
			promise.js
	node_modules
	.babelrc
	package-lock.json
	package.json
我们在命令行输入./node_modules/.bin/babel ./src/js --out-dir ./dist/js即可将`./src/js`目录下的所有js文件通过Babel转化后输出到`./dist/js`目录下
## 写在最后
本文只介绍了最简单的Babel使用方法，如果要结合构建工具使用，相关配置还需参照[babel官网](https://babeljs.io/docs/en/usage)
## 参考文献
【1】[babel官网](https://babeljs.io/docs/en/usage)
---

版权声明：自由转载-非商用-非衍生-保持署名
