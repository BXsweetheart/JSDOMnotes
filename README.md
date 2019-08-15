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
