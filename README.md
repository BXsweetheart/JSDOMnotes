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
            margin:0;
            padding: 0;
        }
        div{
            margin: 100px 100px;
            display: flex;
            flex-direction: row;
        }
        span{
            display: block;
            width: 40px;
            height: 40px;
            font-size: 24px;
            text-align: center;
            line-height: 40px;
            margin: auto 5px;
            background-color: #333;
            color: #fff;
        }
    </style>
</head>
<body>
    <div>
        <span class="hour"></span>:
        <span class="minute"></span>:
        <span class="second"></span>
    </div>
    <script>
        var hour=document.querySelector('.hour');//小时
        var minute=document.querySelector('.minute');//分钟
        var second=document.querySelector('.second');//秒
        // var inputTime= +new Date('2019-8-15 24:00:00');//用户输入事件的总毫秒数
         var inputTime = new Date( new Date(new Date().toLocaleDateString()).getTime() +24 * 60 * 60 * 1000 )   //当天24：00
        countDown();
        setInterval(countDown,1000);
        function countDown( ){
            var nowTime=+new Date();//当前毫秒数
            var times=(inputTime-nowTime)/1000;
            var h=parseInt(times/60/60%24);//hour
            h=h<10?'0'+h:h;
            hour.innerHTML=h;
            var m=parseInt(times/60%60);//minute
            m=m<10?'0'+m:m;
            minute.innerHTML=m;
            var s=parseInt(times%60);//second
            s=s<10?'0'+s:s;
            second.innerHTML=s;
        }
        
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
</head>
<body>
    <input type="number"><button>Sent</button>
    <script>
        var btn=document.querySelector('button')
        var time=3
        btn.addEventListener('click',function(){
            btn.disabled=true;
           
          var timer=  setInterval(() => {
                if(time==0){
                    clearInterval(timer);
                    btn.disabled=false;
                    btn.innerHTML='发送';
                    time=3
                }   else{
                    btn.innerHTML='还剩下'+time+'秒';
                    time--;       
                }    
            }, 1000);
        })
    </script>
</body>
</html>
```
| 组成 | 说明 |
| ------ | ------ |
| protocol | 通信协议  常用的Shttpftp;maito等 |
| host | 主机(域名)  www.itheima.con |
| port | 端口号  可选,省略时使用方案的默认端口如http的默认端口为80 | 
| path | 路径  由零或多个'/'符号隔开的字符串,一般用来表示主机上的一个目录或文件地址|
| query| 参数  以键值对的形式通过&符号分隔开来 | 
| fragment| 片段  #后面内容 常见于链接锚点 |

| location对象属性| 返回值| 
| ------ | ------ |
| location. href| 获取或者设置整个URL| 
| location. host| 返回主机(域名)www.itheima.com| 
| location. port| 返回端口号如果未写返回空字符串| 
| location. pathname| 返回路径| 
| location, search| 返回参数| 
| location. hash| 返回片段#后面内容常见于链接锚点| 

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
    <button>点击</button>
    <div></div>
    <script>
        var btn=document.querySelector('button');
        var div=document.querySelector('div');
       btn.addEventListener('click',function(){
            // location.href='http://www.baidu.com'
            var timer=5
            setInterval(() => {
                if(timer==0){
                    location.href='http://www.baidu.com'
                }else{
                    div.innerHTML='你将在'+timer+'秒钟后跳转到首页';
                    timer--;
                }
                
            }, 1000);
        });
    </script>
</body>
</html>
```
| location对象方法| 返回值| 
| ------ | ------ |
| location. assign()| 跟href一样,可以跳转页面(也称为重定向页面)| 
| location. replace()| 替换当前页面,因为不记录历史,所以不能后退页面| 
| location. reload()| 重新加载页面,相当于刷新按钮或者f5如果参数为true强制刷新ctrl+f5| 

| history对象方法| 作用| 
| ------ | ------ |
| back()| 可以后退功能| 
| forward()| 前进功能| 
| go(参数| 前进后退功能参数如果是1前进1个页面如果是-1后退1个页面| 


| offset系列属性| 作用 | 
| ------ | ------ |
| element.offsetParent | 返回作为该元素带有定位的父级元素如果父级都没有定位则返回body | 
| element.offsetlop | 返回元素相对带有定位父元素上方的偏移 | 
| element.offsetLeft | 返回元素相对带有定位父元素左边框的偏移 | 
| element.offsetwidth | 返回自身包括 padding、边框、内容区的宽度,返回数值不带单位 | 
| element.offsetHeight | 返回自身包括 padding、边框、内容区的高度,返回数值不带单位 | 

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
        .box{
            width: 200px;
            height: 200px;
            margin: 200px 150px;
            background-color: aqua;
        }
    </style>
</head>
<body>
    <div class="box"></div>
    <script>
        var box=document.querySelector('.box')
        box.addEventListener('mousemove',function(e){
            var x=e.pageX-this.offsetLeft
            var y=e.pageY-this.offsetTop
            this.innerHTML='x坐标是'+x+'y坐标是'+y;
        })
    </script>
</body>
</html>
```

###放大镜
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
        
        .preview-img{
            position: relative;
            margin: 50px 50px;
            width: 600px;
            height: 400x;
            border: 1px solid #333;
        }  
        .img{
            margin: 50px 100px;
        }
        .mask{
            display: none;
            width: 150px;
            height: 150px;
            position: absolute;
            top: 0;
            left: 0;
            background-color: #FEDE4F;
            opacity: .5;
            cursor: move;
        }
        .big{
            margin: 0;
            padding: 0;
            display: none;
            position: absolute;
            width: 800px;
            height: 500px;
            /* background-color: aqua; */
            left: 610px;
            top:0;
            z-index: 999;
            border: 1px solid #ccc;
            overflow: hidden;
        }
        .big img{
            position: absolute;
            top:0px;
            left:0px;
        }
    </style>
</head>
<body>
    <div class="preview-img">
        <img class="img" src="picture/Riven.jpg" width="400px" alt="">
        <div class="mask"></div>
        <div class="big">
            <img src="picture/Riven.jpg" class="bigImg" alt="">
        </div>
    </div>
    <script>
        var preview_img=document.querySelector('.preview-img')
        var mask=document.querySelector('.mask');
        var big=document.querySelector('.big');

        preview_img.addEventListener('mouseover',function(){
            mask.style.display='block';
            big.style.display='block';
        });
        preview_img.addEventListener('mouseout',function(){
            mask.style.display='none';
            big.style.display='none';
        })
        //2.鼠标移动的时候让黄色的盒子跟着鼠标走
        preview_img.addEventListener('mousemove',function(e){
            //（1）先计算出鼠标在盒子内的坐标
           var x=e.pageX-this.offsetLeft
           var y=e.pageY-this.offsetTop
           
           //（2）减去mask自身宽度（offsetWidth）以及自身高度（offsetHeight）的一半就是鼠标在盒子中间的left和top值了。
            //（3）mask移动的距离
            var maskX=x-mask.offsetWidth/2;
            var maskY=y-mask.offsetHeight/2 ;
            //（4）如果mask的坐标小于0，就让他停在0的位置；
            var maskXMax=preview_img.offsetWidth-mask.offsetWidth;//遮挡层最大的横向移动距离
            var maskYMax=preview_img.offsetHeight-mask.offsetHeight;//遮挡层最大的竖向移动距离
            if(maskX <= 0){
                maskX = 0;
            }else if( maskX>=maskXMax){
                maskX = maskXMax;
            }
            if(maskY<=0) {
                maskY = 0;
            }else if( maskY>=maskYMax){
                maskY = maskYMax;
            }
           mask.style.left=maskX +'px';
           mask.style.top=maskY +'px';
           //大图片的移动距离=遮挡层移动距离*大图片最大移动距离/遮挡层的最大移动距离
           var bigImg= document.querySelector('.bigImg');
           var bigXMax=bigImg.offsetWidth-big.offsetWidth;
           var bigYMax=bigImg.offsetHeight-big.offsetHeight;
           var bigX=maskX*bigXMax/maskXMax;
           var bigY=maskY*bigYMax/maskYMax;
           bigImg.style.left=-bigX+'px'
           bigImg.style.top=-bigY+'px'
        })
    </script>
</body>
</html>
```
| client系列属性| 作用| 
| ------ | ------ |
| element. client Top| 返回元素上边框的大小| 
| element. clientLeft| 返回元素左边框的大小| 
| element. clientWidth| 返回自身包括 padding、内容区的宽度,不含边框,返回数值不带单位| 
| element clientHeight| 返回自身包括 padding、内容区的高度,不含边框,返回数值不带单位| 

| scroll系列属性| 作用| 
| ------ | ------ |
| element.scrollTop| 返回被卷去的上侧距离,返回数值不带单位| 
| element.scrollLeft| 返回被卷去的左侧距离,返回数值不带单位| 
| element.scrollwidth| 返回自身实际的宽度,不含边框,返回数值不带单位| 
| element.scrollHeight| ]返回自身实际的高度,不含边框,返回数值不带单位| 

| 三大系列大小对比| 作用| 
| ------ | ------ |
| element.offsetwidth| 返回自身包括padding、边框、内容区的宽度,返回数值不带单位| 
| element.clientWidth| 返回自身包括padding、内容区的宽度,不含边框,返回数值不带单位| 
| element.scrollWidth| 返回自身实际的宽度,不含边框,返回数值不带单位| 


```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <meta http-equiv="X-UA-Compatible" content="ie=edge">
    <title>Document</title>
    <style>
    div{
        position:absolute;
        left: 0;
        width: 100px;
        height: 100px;
        background-color: aqua;
    }
    </style>
</head>
<body>
    <div></div>
    <script>
        var div=document.querySelector('div');
        var timer=  setInterval(function(){
            if(div.offsetLeft<=400){
               div.style.left=div.offsetLeft + 1 +'px'
            }else{
                clearInterval(timer)
            }

        },100)
    </script>
</body>
</html>
```
```HTML
<div></div>
<span></span>
<script>
    function animate(obj,target){
       var timer=  setInterval(function(){
          if(obj.offsetLeft<=target){
               obj.style.left=obj.offsetLeft + 1 +'px'
          }else{
               clearInterval(timer)
          }
       },100)
    }
    var div=document.querySelector('div');
    var span=document.querySelector('span');
    animate(div,200);
    animate(span,100)
</script>
```
|事件列表 |说明 | 
| ------ | ------ |
| touchstart | 手指触摸DOM元素事件 | 
| touchmove | 手指在DOM元素身上移动事件 | 
| touchend | 手指离开DOM元素事件| 

| 触摸列表| 说明| 
| ------ | ------ |
| touches| 正在触摸屏幕的所有手指的一个列表| 
| targetTouches| 正在触摸当前DOM元素上的手指的一个列表| 
| changedTouches| 手指状态发生了改变的表,从无到有,从有到无变化| 
