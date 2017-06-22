# webpack@1.12.14

初始环境：已安装 Node.js 和 npm

## 安装

```
npm init 
npm install webpack@1.12.14 --save-dev
```
## 栗子的文件
```
index.html
index.js
hello.js
```
```html [index.html]
<!DOCTYPE html>
<html lang="en">
<head>
	<meta charset="UTF-8">
	<title>rawraw</title>
</head>
<body>
	<script src="./bundle.js"></script>
</body>
</html>
```
```js [index.js]
var text = require('./hello');
console.log(text);
```
```js [hello.js]
module.exports = 'Hello Rawraw';
```
## 构建
```
webpack ./index.js bundle.js
```
结果：控制台输出Hello Rawraw
## webpack.config.js
```js
```
## loader
通过jsx-loader将REACT的JSX代码转换为JS代码
### 常用loader
`cnpm install file-loader css-loader style-loader sass-loader ejs-loader html-loader jsx-loader image-webpack-loader --save-dev`
### style-loader
作用：将CSS代码以`<style>`标签形式插入到页面上从而生效
### css-loader
作用：检查CSS代码中的import语句找到依赖并合并
### 安装loader
`npm install style-loader css-loader --save-dev`
### 栗子
#### 新建index.css文件
```css [index.css]
div{
	width: 100px;
	height: 100px;
	background-color: darkseagreen;
}
```
#### 新建index2.js
```js [index2.js]
//style-loader!css-loader!!:指定stylehe-loader和css-loader对index.css进行处理
require('style-loader!css-loader!./index.css');
document.body.appendChild(document.createElement('div'));
```
#### 构建
```
webpack ./index2.js bundle.js
```
![“运行结果”](/code1.png)
## Plugin
### html-webpack-plugin
自动创建html页面
#### 安装
```cmd
npm install html-webpack-plugin --save-dev
```
```js [webpack.config.js]
var HtmlWebpackPlugin = require('html-webpack-plugin');
//...
Plugins:[
 new HtmlWebpackPlugin({
    title:'test'
 })
]
//...
```
### extract-text-webpack-plugin:加载优化
css和js同时加载，可以通过extract-text-webpack-plugin插件，在把宝石将样式内容抽取并输出到额外的CSS文件中，然后再页面中直接引入结果CSS
#### 安装
```cmd
npm install extract-text-webpack-plugin --save-dev
```
## 实时构建
### webpack-dev-server
#### 安装
```
npm instal webpack-dev-server -g
```
#### 启动
默认监听8080，http://localhost:8080
```
webpack-dev-server
```
## 常用命令
```
$ webpack --config webpack.min.js //另一份配置文件
$ webpack --display-error-details //显示异常信息
$ webpack --watch   //监听变动并自动打包
$ webpack -p    //压缩混淆脚本
$ webpack -d    //生成map文件，被最终打包到哪里
```