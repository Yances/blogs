###html代码展示（直接复制代码保存至本地文件运行即可）：
```
<!DOCTYPE html>
<html lang="en">

<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0, maximum-scale=1.0, user-scalable=no">
    <title>移动端隐藏滚动条解决方案</title>
    <style type="text/css">
    * {
        padding: 0;
        margin: 0;
    }

    .container {
        height: 50px;
        -webkit-box-sizing: border-box;
        box-sizing: border-box;
        overflow: hidden;
    }

    .nav {
        height: 100%;
        overflow-x: scroll;
        overflow-y: hidden;
        background-color: #999;
    }

    .con {
        width: 640px;
        height: 100%;
        display: flex;
        align-items: center;
    }

    .con>li {
        text-align: center;
        font-size: 16px;
        width: 80px;
        list-style: none;
    }
    .container ::-webkit-scrollbar {
        display: none;
    }
    </style>
</head>

<body>
    <div class="container">
        <nav class="nav">
            <ul class="con">
                <li>元素一</li>
                <li>元素二</li>
                <li>元素三</li>
                <li>元素四</li>
                <li>元素五</li>
                <li>元素六</li>
                <li>元素七</li>
                <li>元素八</li>
            </ul>
        </nav>
    </div>
</body>

</html>
```
**设置滚动条隐藏： .container ::-webkit-scrollbar {display: none;}**
此时效果已经实现，既可滑动对应元素的内容，也隐藏了滚动条。但是，ios上的滑动效果很不流畅，不利于用户体验，Android上是ok的；此时可以加上这样一句css代码（-webkit-overflow-scrolling: touch;），如下：

```
.nav {
        height: 100%;
        overflow-x: scroll;
        overflow-y: hidden;
        background-color: #999;
        /*解决ios上滑动不流畅*/
        -webkit-overflow-scrolling: touch;
    }
```
这时ios上滑动变得流畅了，但是又出现了一个新的问题，滚动条又重现了，如图：

![1506048482539.jpg](http://upload-images.jianshu.io/upload_images/7626406-0339817f2d7fab84.jpg?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
***
现在的需求是：既要不出现滚动条，又要滑动流畅，可以使用接下来一个小技巧：
**因为滚动条是出现nav这个标签元素上的，所以可以进行如下设置：**
```
.nav {
        /*width: 100%;*/
        height: 100%;
        overflow-x: scroll;
        overflow-y: hidden;
        background-color: #999;
        /*解决ios上滑动不流畅*/
        -webkit-overflow-scrolling: touch;
        /*纵向超出部分将会隐藏，即滚动条部分被挤出可视区域*/
        padding-bottom: 20px;
    }
```
PS：
>1.**nav的外层容器设置了固定高度，并且设置了内容溢出隐藏，所有nav的纵向的超出内容是不可见的，即：overflow:hidden;
2.padding-bottom等于20px并非固定值，只要你的设置的值大小足够将滚动条挤出可视区域即可。**
####说明：根据步骤更改对应的css样式，即可得出最终结果；也可直接访问完整代码：[http://www.jianshu.com/p/f282b1cc24fb]()。