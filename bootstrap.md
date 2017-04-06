#### 模板
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
