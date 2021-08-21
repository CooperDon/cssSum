# CSS知识总结

### 一、CSS体系化学习

			+ Copy    抄文档
			+ Run      在电脑上运行
			+ Modify 加入自己的想法继续运行



### 二、CSS基础概念

1. css语法

   ```html
   <!--css语法样式一-->
    <div class="xxx">
           css语法样式
    </div>
   	<style>
           .xxx {
               color: red;
           }
       </style>
   注意：
   	所有符号都是英文的；
   	区分大小写；
   <!--css语法样式二	@语法-->
    		@charset "UTF-8";
           @import url(xxx.css);
           @media (min-width:100px) and (max-width:200px){
               语法一
           }
   ```

2. border调试法

   通过给某个class添加border属性查看所添加样式是否生效

   ```html
    <div class="xxx">
           css语法样式
    </div>
   	<style>
           .xxx {
               color: red;
               border: 1px solid green;
           }
       </style>
   ```

3. css文档流(normal flow)

   |        |              流动方向              |            宽度            |               高度               |
   | :----: | :--------------------------------: | :------------------------: | :------------------------------: |
   | inline | 元素从左至右排列，到达右边界时换行 |      内联元素宽度总和      |      由line-height间接决定       |
   | block  |            元素独占一行            |     width：auto(!100%)     | 默认文档流内容高度，可设置height |
   |  i-b   |  从左至右，单个元素成块分布不分离  | 初始值同span,但width可设置 |             同block              |

   ![flow](https://i.loli.net/2021/08/09/U8m1NT4QIOyxgSe.png)

   #### 注意

    + 不在inline元素内包含block元素

    + inline设置width属性时无效果

    + 当block元素设置的height比内容低时，会出现overflow，文档溢出的情况，解决办法：

      ```css
      overflow:visible;
      overflow:hidden;
      overflow:scroll;
      overflow:auto;
      ```

4. css盒模型

   ##### 基本概念

   	+ 当对一个文档进行布局(layout)的时候，浏览器的渲染引擎会根据 **CSS 基础框盒模型**（**CSS basic box model**），将所有元素表示为一个个矩形的盒子（box）。CSS 决定这些盒子的大小、位置以及属性（例如颜色、背景、边框尺寸…）。
   	+ 每个盒子由四个部分（或称*区域*）组成，其效用由它们各自的边界（Edge）所定义（原文：defined by their respective edges，可能意指容纳、包含、限制等）。与盒子的四个组成区域相对应，每个盒子有四个边界：*内容边界* *Content edge*、*内边距边界* *Padding Edge*、*边框边界* *Border Edge*、*外边框边界* *Margin Edge*。

   ![盒模型](https://i.loli.net/2021/08/15/iMTRpxmt4PNqdJ7.png)

   ##### 代码

   ```html
   <!DOCTYPE html>
   <html lang="en">
   <head>
       <meta charset="UTF-8">
       <meta http-equiv="X-UA-Compatible" content="IE=edge">
       <meta name="viewport" content="width=device-width, initial-scale=1.0">
       <title>CSS盒模型</title>
       <style>
           .content-box {
               margin: 25px;
               border: 3px solid blueviolet;
               padding: 15px;
               box-sizing: content-box;
               width: 100px;
               height: 100px;
           }
           .border-box {
               margin: 25px;
               border: 3px solid blueviolet;
               padding: 15px;
               box-sizing: content-box;
               width: 100px;
               height: 100px;
           }
       </style>
   </head>
   
   <body>
       <div class="content-box">content box</div>
       <div class="border-box">border box</div>
   </body>
   </html>
   ```

   ##### margin合并

   	+ margin合并只存在于上下边距
   	+ 两上下相邻子元素间会出现margin合并
   	+ 第一个和最后一个子元素会与父元素出现margin合并
   	+ 可通过加border、padding、overflow：hidden是进行解决
   	+ <img src="https://i.loli.net/2021/08/15/n4WYUGXV8gZOPhS.png" alt="margin合并" style="zoom: 50%;" />

   
### 三、CSS布局

 1. css布局是什么

    + 将页面分成一块一块更小的区域，并按一定顺序进行排列；
    + 固定宽度布局、非固定宽度布局、响应式布局(混合布局)；

 2. 如何进行css布局

    + 先确定大的整体的布局，再完善小的部分；
      	 <img src="https://i.loli.net/2021/08/15/YCW4VTq5xn7r1pZ.png" alt="Snipaste_2021-08-15_11-14-16" style="zoom:50%;" />

 3. float布局

    ##### 说明

    + 元素使用float布局时，标签会脱离文档流，不占空间；
    + 在子元素style加float：left或float：right；
    + 在父元素加.clearfix{}清除浮动；

    ##### 代码

    ```html
    <!DOCTYPE html>
    <html lang="zh-CN">
    <head>
        <meta charset="UTF-8">
        <meta http-equiv="X-UA-Compatible" content="IE=edge">
        <meta name="viewport" content="width=device-width, initial-scale=1.0">
        <title>Float布局</title>
        <style>
            * {
                margin: 0;
                padding: 0;
                box-sizing: border-box;
            }
    
            .logo {
                border: 1px solid red;
                height: 30px;
                width: 100px;
                float: left;
            }
    
            nav {
                border: 1px solid red;
                width: 200px;
                height: 50px;
                float: right;
            }
    
            .clearfix::after {
                content: '';
                display: block;
                clear: both;
            }
        </style>
    </head>
    <body>
        <header class="clearfix">
            <div class="logo">XDML</div>
            <nav></nav>
        </header>
    </body>
    </html>
    ```

### 四、CSS动画

1. ​	何为动画？

   + 许多静止的画面(帧)以一定的速度连续播放，使人产生的视觉错觉

2. 动画简单演示

   ##### 代码

   ```html
   <!DOCTYPE html>
   <html lang="zh-CN">
   <head>
       <meta charset="UTF-8">
       <meta http-equiv="X-UA-Compatible" content="IE=edge">
       <meta name="viewport"
           content="width=device-width, initial-scale=1.0, maximum-scale=1.0, minimum-scale=1.0, user-scalable=no">
       <title>CSS动画</title>
       <style>
           #demo {
               width: 500px;
               height: 500px;
               border: 10px solid red;
               position: relative;
               left: 0;
           }
       </style>
   </head>
   <body>
       <div id="demo"></div>
       <script>
           var n = 1;
           var id = setInterval(() => {
               if (n <= 200) {
                   demo.style.left = n + 'px';
                   n = n + 1;
               } else {
                   clearInterval(id);
               }
           }, (1000 / 60))
       </script>
   </body>
   </html>
   ```

   ```html
   <!DOCTYPE html>
   <html lang="zh-CN">
   <head>
       <meta charset="UTF-8">
       <meta http-equiv="X-UA-Compatible" content="IE=edge">
       <meta name="viewport"
           content="width=device-width, initial-scale=1.0, maximum-scale=1.0, minimum-scale=1.0, user-scalable=no">
       <title>CSS动画</title>
       <style>
           #demo {
               width: 100px;
               height: 100px;
               border: 10px solid red;
               position: relative;
               left: 0;
           }
           #demo.end {
               transform: translateX(200px);
           }
       </style>
   </head>
   <body>
       <div id="demo"></div>
       <script>
           setInterval(() => {
               demo.classList.add('end')
           }, 1000)
       </script>
   </body>
   </html>
   ```

3. 浏览器渲染原理

   <img src="https://i.loli.net/2021/08/21/9kPohDWlxawIR7m.png" alt="浏览器渲染" style="zoom:50%;" />

   + 样式更新
     + JS/CSS > 样式 > 布局 > 绘制 > 合成 
     + JS/CSS > 样式 > 绘制 > 合成
     + JS/CSS > 样式 > 合成

4. transform属性

   + 四个常用功能
     + 位移：translate
     + 缩放：scale
     + 旋转：rotate
     + 倾斜：skew

5. animation属性

   ```css
   @keyframes slidein{
       from{
           transform:translateX(0%);
       }
       to{
           transform:translateX(100%);
       }
   }
   
   @keyframes identifier{
       0%{
           transform:translateX(0%);
       }
       30%{
           transform:translateX(25%);
       }
       68%{
           transform:translateX(50%);
       }
       100%{
           transform:translateX(80%);
       }
   }
   ```

   
