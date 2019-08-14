# JSDOMnotes
```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <meta http-equiv="X-UA-Compatible" content="ie=edge">
    <title>Document</title>
    <style>
        img{
            position: absolute;
            top:1px;
        }
    </style>
</head>
<body>
    <img src="picture/Arli.jpg" alt="" width="80px">
    <script>
        var pic=document.querySelector('img');
        document.addEventListener('mousemove',function(e){
            // console.log(1)
            var x=e.pageX;
            var y=e.pageY;
            // console.log('x坐标是'+x,'y坐标是'+y)
            pic.style.top=y-40+'px';
            pic.style.left=x-40+'px';
        })
      
    </script>
</body>
</html>
```
| 鼠标事件对象 | 说明 |
| ------ | ------ |
| e.clientX | 返回鼠标相对于浏览器窗口可视区的X坐标 |
| e.clientY | 返回鼠标相对于浏览器窗口可视区的Y坐标 |
| e.pageX | 返回鼠标相对于文档页面的X坐标 IE9+支持 |
| e.pageY | 返回鼠标相对于文档页面的Y坐标 IE9+支持 |
| e.screenX | 返回鼠标相对于电脑屏幕的Ⅹ坐标 |
| e.screenY | 返回鼠标相对于电脑屏幕的Y坐标 |

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <meta http-equiv="X-UA-Compatible" content="ie=edge">
    <title>Document</title>
</head>
<body>
    <input type="text" name="" id="">
    <script>
        var search=document.querySelector('input');
        document.addEventListener('keyup',function(e){
            if(e.keyCode===83){
                search.focus()
            }
        })
    </script>
</body>
</html>
```
```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <meta http-equiv="X-UA-Compatible" content="ie=edge">
    <title>Document</title>
    <style>
        *{
            margin: 0;
            padding: 0;
        }
        .search{
            position: relative;
            width: 178px;
            margin: 100px;
        }
        .con{
            display: none;
            position: absolute;
            top: -40px;
            width: 171px;
            border: 1px solid rgba(0,0, 0, .2);
            box-shadow: 0 2px 4px rgba(0,0, 0, .2);
            padding: 5px 0;
            font-size: 18px;
            line-height: 20px;
            color: #333;
        }
        .con::before{
            content: "";
            width: 0;
            height: 0;
            position: absolute;
            top: 28px;
            left: 18px;
            border: 8px solid #000;
            border-style: solid dashed dashed;
            border-color: #fff transparent transparent;
        }

    </style>
</head>
<body>
    <div class="search">
        <div class="con">123</div>
        <input type="text" placeholder="请输入您的快递单号" class="jd">
    </div>
    <script>
        var con=document.querySelector('.con')
        var jd_input=document.querySelector('.jd')
        jd_input.addEventListener('keyup',function(){
            // console.log('输入')
            if (this.value==''){
                con.style.display='none';
            }else{
                con.style.display='block';
                con.innerText=this.value;
            }
        })
        jd_input.addEventListener('blur',function(){
            con.style.display='none'
        })
        jd_input.addEventListener('focus',function(){
            if(this.value!==''){
                con.style.display='block'
            }
        })
    </script>
</body>
</html>
```
