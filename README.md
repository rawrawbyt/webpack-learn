# webpack-learn
webpack学习
## 安装
`mkdir webpack-learn && cd webpack-learn`
`npm i npm -g`
`npm init -y`
`npm install webpack --save-dev`
`npm install webpack@<version> --save-dev`
## 创建demo
新建app 子目录下创建一个 index.js 文件。
```js [index.js]
function component () {
	var element = document.createElement('div');

	/* 需要引入 lodash，下一行才能正常工作 */
	element.innerHTML = _.join(['Hello','webpack'], ' ');

	return element;
}

document.body.appendChild(component());
```
```html [index.html]
<!DOCTYPE html>
<html lang="en">
<head>
	<meta charset="UTF-8">
	<title>test</title>
</head>
<body>
	<script src="app/index.js"></script>
</body>
</html>
```
## 安装 lodash 依赖
`npm install --save lodash`
## 执行
### 手动
`webpack app/index.js dist/bundle.js`
### 自动，新建webpack.config.js
```js
var path = require('path');

module.exports = {
	entry: './app/index.js',
	output: {
		filename: 'bundle.js',
		path: path.resolve(__dirname, 'dist')
	}
};
```
`webpack --config webpack.config.js`
## npm快捷方式
```js
{
  ...
  "scripts": {
    "build": "webpack"
  },
  ...
}
```
`npm run build`
