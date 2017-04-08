### 模板
```
<!DOCTYPE html>
<html>
<head>
   <title></title>
   <meta charset="utf-8">
   <meta name="viewport" content="width=device-width,initial-scale=1.0,                                       
    maximum-scale=1.0,user-scalable=no">
   <link rel="stylesheet" type="text/css" href="bower_components/bootstrap/dist/css/bootstrap.min.css">
   <script src="bower_components/jquery/dist/jquery.min.js"></script>
   <script src="bower_components/bootstrap/dist/css/bootstrap.min.js"></script>
</head>
<body>

</body>
</html>
```
### 核心
> 栅格化系统+响应式布局，bootstrap 依赖与jquery，用bower安装bootstrap会自动jquery
### 建议使用bower安装，需要node环境安装bower
```
cnpm install bower -g
//然后就可以使用bower安装了,切换到项目根目录,使用git
bower install bootstrap
```
### 使用
> 有两种方式

- main.js中全局引用，这样项目任何地方都可以直接调用，但是这样引入有个弊端，大家都知道，main.js引入的东西是会被webpack全部打包到built.js文件中，这样的话，项目文件就会很大，推荐使用下面这种方式引用
```
import bootstrap from 'bootstrap'
Vue.use(bootstrap)
```
- 一般像jquery bootstrap这种建议在index.html中引入即可只需要引入这个bootstrap.min.css即可
`<link rel="stylesheet" type="text/css" href="bower_components/bootstrap/dist/css/bootstrap.min.css">`

### 栅格化系统
```
 <div class="container">
      <div class="row">
           <div class="col-md-6"></div>
           <div class="col-md-6"></div>
      </div>
  </div>    
 用jade的语法就是这样
 .container
   .row
     .col-md-n
eg:

    <div class="container">
      <div class="row">
        <div class="col-md-4" style="background: red">
            apple
        </div>
        <div class="col-md-4">
            pear
        </div>
        <div class="col-md-4">
            orange
        </div>

      </div>

    </div>
```
```
.cantainer
 .row
  .col-md/xs-n n(max)=12
```
### 面板
<hr>
使用语境状态类 panel-primary、panel-success、panel-info、panel-warning、panel-danger，来设置带语境色彩的面板，实例如下：
```
   .panel-success
     .panel-heading
     .panel-title
     .panel-body
     .panel-footer
     .table
```    
### table
<hr>

```
        <table class="table">
		<th>name</th>
		<th>mark</th>
		<tr>
		  <td>产品 A</td>
		  <td>200</td>
		</tr>
		  <tr><td>产品 A</td>
		  <td>200</td>
		 </tr>
	</table>
```
实际效果如下<br>

<table class="table">
		<th>name</th>
		<th>mark</th>
		<tr>
		  <td>产品 A</td>
		  <td>200</td>
		</tr>
		  <tr><td>产品 A</td>
		  <td>200</td>
		 </tr>
	</table>
###　ul
列表组件用于以列表形式呈现复杂的和自定义的内容。创建一个基本的列表组的步骤如下：
向元素 <ul> 添加 class .list-group。
向 <li> 添加 class .list-group-item。
<hr>
```
  <ul class="list-group">
      <li class="list-group-item">免费域名注册</li>
      <li class="list-group-item">免费 Window 空间托管</li>
      <li class="list-group-item">图像的数量</li>
      <li class="list-group-item">24*7 支持</li>
      <li class="list-group-item">每年更新成本</li>
 </ul>
``` 

### well
<hr>
Well 是一种会引起内容凹陷显示或插图效果的容器 <div>。为了创建 Well，只需要简单地把内容放在带有 class .well 的 <div> 中即可。
```
  .well well-lg
  .well well-sm
```
### badge
我们可以向任意的列表项添加徽章组件，它会自动定位到右边。只需要在 <li> 元素中添加` <span class="badge">` 即可

<hr>
`<span class="badge">新</span>`
