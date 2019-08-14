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
