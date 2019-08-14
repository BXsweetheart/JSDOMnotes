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
