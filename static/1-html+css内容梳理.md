###	大案例﻿

一共三个大案例： 云道、京东、学成在线
疑问：通栏居中为什么要用一个盒子嵌套包裹呀； 因为又要通栏又要居中呀

### 查询文档和工具：

标签命名规范：[web前端开发规范手册.doc] ------（https://www.cnblogs.com/xiaonian0327/p/7735799.html）
常用查询文档： w3c、MDN
拔网页小工具：day12中

---

### 后知后觉

**div等容器文字只会单行显示**



--------------------

### 知识点回顾

1. html常见标签

   

2. 表单与表格   

   + 表单中label标签，label中的for属性用于和表单中的id 绑定
   + 重置按钮和提交按钮 在form中才可以用；

   + 表格（设置三参为0  border，cellspacing ，cellpadding），介绍合并单元格

     

3. 使用css样式表的三种方式：

   + 行内式（偶尔使用）、内部样式表、外部样式表

     

   +  **行内权重高，但是只能控制单个标签**

4. **css三大特性：**

   + 层叠性： 后来的css代码中样式 会覆盖前面的；
                    注：样式不冲突 ，前面的代码依旧有用，不会被覆盖；

     

   + 继承性：子标签会继承父标签的 某些样式；
             如： color  text-  font-  line- 都是可以继承的；

     ​        **但是高 是不继承的；margin和padding是不会继承的（显而易见好吧）**

     

     **恰当的利用继承性可以简化代码，降低css样式的复杂性；**

     

   +  优先级：行内样式最大；
              id选择> 类选择器> 标签选择器；

     **权重介绍**:				             

         	     标签权重  0，0，0，1；
                  类选择器  0，0，1，0；
                  id选择器  0，1，0，0；
                  行内样式  1，0，0，0；
                  ！important 无穷大；
                  * 和继承   0，0，0，0  权重最小；
     注意：

     > 1. 权重是可以叠加的：(子代选择器 交集选择器都会叠加)
     >        div ul li  0，0，0，3
     >        .nav ul li 0，0，1，2
     >        a:hover 0,0,1,1;（********）
     >
     > 2. 权重相同 ，则就近原则；
     >
     > 3. 记住权重是不进位的   0005+0005 ！= 0010 的  而是0，0，0，10；
     >
     >    
     >
     > 4. **父元素的权重再大  继承过后  子元素的权重也还是0；**



> 伪类选择器书写理解：
>
> a:hover .mask （空格 表示后代选择器 表示 a里面的mask显示出来）（**伪类选择器 的这种形式的理解**）

​				



5. 标签分类及width和height默认值问题。-----------见自己文档



6. 样式连写总结：

   + 字体font

     > font的连写： font：12px/1.5 （表示的是行高 1.5* font-size）

   +  背景background

   +  文本（color，text-decoration，text-align、line-height ）

   > **连写的样式覆盖现象**
   >
   > transform： translateX（-20px）；
   > transform： scale（0.8）
   > 后面的会覆盖的上面的；

注：**背景位置 background-position**

> + background-position : x，y （**可以用方位名词 center top left 也可与px 混合用也可以**）
>
>   ​	1. positon后面可以跟方位名词  他们之间可以没有上下顺序
>
>   	2. position 如果只写一个方位名词，另外一个默认是居中的
>    	3. position 后面也可以跟 值px 但是 必须有顺序 x 在前面 y 后面 不能颠倒 
>
>   
>
>   另外：***left top 是默认值；***
>
> + background-position设置center
>
>    **位置中的center 是把背景图放在盒子的中线上；**
>
>    如果图比盒子大的话 ，图会超出盒子 的  也就是图的中心部分还是在盒子的中心的；



注意：background-attachment了解：


​    

7.  经常混淆的几个样式：

   ​    背景透明：rbga() 用在background中  

   ​			>  **透明设置方式背景：background： rgba(0,0,0,0.3 )**

   ​    盒子阴影 box-shadow

   ​		   >  盒子阴影（css3）box-shadow：水平阴影  垂直阴影  模糊距离  阴影尺寸（就是影子的大小）  颜色   内外阴影（默认外阴影）

   ​    盒子透明 opacity:  **盒子包括盒子的内容都透明**

   ​		 >  盒子透明 opacity: 0.2;  /*盒子半透明  字也透明了 盒子也透明了*/

   ​	

   注：**CSS:opacity:0,visibility:hidden,display:none的区别**

   ```
   1 opacity=0，该元素隐藏起来了，但不会改变页面布局，并且，如果该元素已经绑定一些事件，如click事件，那么点击该区域，也能触发点击事件的,位置还在；
   2 visibility=hidden，该元素隐藏起来了，但不会改变页面布局，但是不会触发该元素已经绑定的事件
   3 display=none，把元素隐藏起来，并且会改变页面布局，可以理解成在页面中把该元素删除掉一样
   ```




8. 水平居中垂直居中整理------见 自己 文档；

   

9. margin的两种坍塌现象；**子元素带着父元素垂直方向跑；**
           现象描述： 对于两个嵌套关系的块元素， 如果父元素没有上内边距 和边框 则父元素的
           上外边距会与子元素的上外边距发生合并 ，合并后的外边距为两者中的较大者，即使父元素
           的上外边距为0，也会发生合并。

   

10.  在css2盒子模型中；添加padding只会撑开带有width和height的盒子； **没有设置宽高的不会撑开**

    > ​	解释：如果一个子盒子没有给定宽度/高度，就会用其父类的属性，这时padding不会影响子盒子的大小(会自适应调节width)



11. **浮动**---------详情见浮动介绍

​	**浮动并不是完全意义上的脱标（文字不会被盖住  还有图片也是）**

​	**浮动的盒子跨越不 了父元素 padding和border**

>  ***另外：因为浮动是在原有位置基础上 浮动的( 三个div 中间一个不设置float：left  第三个不是接在第一个div后面的)***



12. **定位**

    定位的主要属性 就是定位模式（static（默认） relative absolute fixed）和边偏移 top left...；

- 静态定位static   唯一的用处就是取消定位

- 相对定位：根据自己的**左上角**进行定位，

  ​			**相对定位 原先的盒子位置依旧是保留的，会是压住标准流中的元素的**

  **不会打扰标准流的元素，只会叠盖；只有原有位置影响布局，定位后的位置是不影响布局的**

- 绝对定位：将元素依据最近的已经定位的 父元素（祖先）进行定位，是脱离标准文档流， 不占位置的 

  ​                            **-----完全脱标**

+ 固定定位： **父元素加不加position  top和left值都是相对浏览器页面的**

+ z-index：（叠放次序）  表示的是z轴 ；

  > 只有定位（relative，absolute，fixed都有）的盒子才有z-index
  >  浮动  静态定位都是没有z-index的；
  >
  > -z-index取值相同，后来者居上；

  另外：如果没有设置z-index 相同的 就后来者居上覆盖（**但是并不是说它的z-index 依次变大**）



> **边偏移 top left**
>
> > left: % 的时候是父元素的盒子宽度的大小；（就是说 width+padding的后的值）
> >
> > 

补充：**left的值和right的值同时出现的时候**

> 定位中left的值和right的值同时出现的时候 以 left和top为准
>     这个和css的层叠性没关系  也就是和先后设置没关系
>
> 同时设置margin-left和margin-right也是  以left为准



13. 显示与隐藏：

    + opacity:0,

    + visibility:hidden,

    + display:none

    三者区别：

    ```
    1 opacity=0，该元素隐藏起来了，但不会改变页面布局，并且，如果该元素已经绑定一些事件，如click事件，那么点击该区域，也能触发点击事件的,位置还在；
    	但是h5c3中用了 position：就可以达到不占位置了
    
    2 visibility=hidden，该元素隐藏起来了，但不会改变页面布局，但是不会触发该元素已经绑定的事件
    3 display=none，把元素隐藏起来，并且会改变页面布局，可以理解成在页面中把该元素删除掉一样
    ```



14. 鼠标拖拽  轮廓和防止拖拽：

+  轮廓 outline: ---------一般都是结合表单和表单域使用
          outline: none;  *取消轮廓线的做法*/ /*取消蓝色边框*/      或者用outline：0

+ 防止拖拽 防止它影响布局
        resize: none;  /*防止拖拽*/

> ​			不是只有a才可以设置cursor  p img div 都可以
> ​    	 			cursor: pointer; 让我们的鼠标样式变成小手
> ​					cursor: text;  让我们的鼠标样式变成选择 
> ​					cursor: default;  让我们的鼠标样式小白
> ​       			 cursor: move;  鼠标变成十字架样子
>
> 

15.  溢出文字隐藏  三个样式；
        white-space: nowrap;      /*1.强制在同一行内显示所有文本，直到文本结束或者遭遇br标签对象才换行*/
        	overflow: hidden;             /* 2. 超出的部分 隐藏*/
        	text-overflow: ellipsis;       /* 3. 溢出的部分用省略号替代*/

​    

16. **div直接装一个图片出现一条缝隙问题 **-------div没设置 图片的height 高度；

+ 原因：图片和文字等inline行内元素默认是和父级元素的baseline基线对齐的，而baseline又和父级底边有一定距离（这个距离和 font-size，font-family 相关，不一定是 5px）div不设置高度的时候 视其内容撑开盒子；所以导致这个问题

+ 解决办法：   

  > ​		设置盒子div 的 font-size: 0;  
  >
  > ​		或者设置盒子div 的line-height: 0; 
  > ​    	**还有设置img为block**



------------------------------------

# 实操应用部分

18. 精灵图

    + 目的：为了有效地减少服务器接受和发送请求的次数，避免来回跑；

      > ​       产生背景，一个网页中往往会应用很多小的背景图像作为修饰， 当网页中的图像过多时，服务器就会频繁地接受和发送请求，这将大大降低页面的加载速度。为了有效地减少服务器接受和发送请求的次数，提高页面的加载速度，出现了CSS精灵技术(也称CSSSprites、CSS雪碧)。

    + 操作：设置background-position 

      background: url(images/index.png) no-repeat -2px -184px;

    

    注：> 不好做的那个精灵图 在 day12 中的携程案例中

    

17. 滑动门
    + 功能：根据内容 框适当变大 也是利用了背景图片：（父子都设置背景）
    
+ 结构：
  
  ​       
  
         <a href="#">
     

         			<span>首页</span>
         </a>
         a 左边放左圆角  但是文字需要向右移动15px
         span 右边放右圆角  但是文字需要向左移动15px
         ​       



18. 字体图标-------自己下载的放到D盘下了 D:\python\icomoon

    看上去是图片  其实是字体 （可以设置font-size） 文字 以小图标的形式展示的；

    + 下载字体图标 （ icomoon  德国的和 iconfont 中国）

      ​          先点左上角的icomoon app
      ​          再选择想要的图标 后点击  右下角的generate font
      ​          再找右下角的download 下载压缩包iconmoon；

      ​		  解压后 我们只需要**font文件夹**复制到项目中----------用别人的就直接copy这个目录

      ​          其中的demo.html中是我们要去复制的 
      ​          styles.css 里面有 @font-face {...}（下载的不同 这里也不同）

      

    + 字体图标的使用：
              首先： @font-face {...} 复制这个内容到style标签中；
              其次：  在下载的 文件夹中的demo.html文件中 粘贴 想要的图标
              再： font-family申明字体；(必须要声明font-size中声明的字体)

      >  还有一种伪元素结合图标字体使用；（div::before { content: "\ea51";）
      >
      > 

    + 添加自定义的图标：  点击 import icons（了解）
          将svg图片导入到 icomoon网站上就可以转换了； svg不可以设置字体大小和颜色；
          重新下载新的压缩包 新的图标 添加 解决；

      

    + 追加新的图标；（又想下载新的图标了）
           不能合并  得重新下载
           将 selection.json （方便追加的）导入点击import-icons  再下载就可以重新下载后 再更新index



------------

#	H5C3部分



19. h5 新标签和 css选择器：
       表单标签     \<fieldset>
       新增的表单 （type=url等）具有鉴定功能

       选择器（ul:last-child 结构伪类， div[class] 属性选择器）

    

20. **伪元素：（::before 和:: end ）**
        必须带一个属性  content
    	**伪元素 其实这个 before 是个盒子,这个盒子是行内  可以转换**

      before 和 after 都是在div的内部的inline-block；

21. css3盒子模型：box-sizing

    width 包括边框  、会自适应调节 盒子内容（就是以前的width）



22. 过渡transition：**加在 要让变化的元素身上**

    `

      /*transition: width 0.5s ease 0s, height 0.3s; 多组属性用逗号分隔*/

    `

    

23. 移动、放缩、旋转(2d变换transform)

    + 移动 translate：

      transform： translate（x,y）    translateX（-20px)；

      translate（x，y）  只有一个值时 默认y为0；

        50% 是走自己**盒子宽度**的一半

      **移动后： 原来的位置还占用，和设置relative一样，不会打扰标准流的元素，只会叠盖；只有原有位置影响布局，移动后的位置是不影响布局的** 

    + 缩放scale： 默认中心点缩放

    + 旋转rotate：  默认中心点旋转；

scale和rotate 都可以设置 transform-origin的     

**另外：缩放放大后的区域 和设置移动元素一样，不会打扰标准流的元素，只会叠盖；只有原有位置影响布局，放大后的位置是不影响布局的**

**设置transform顺序决定变化的顺序，出来的结果也会不一样。**

> ```
> transform： translateX（-20px）scale（0.8）  （//先移动 后缩放）
> ```


  **3d变化**

  transform: translateX(); translateY()（这两个2d中也有）;translateZ(); translate3d(x,y,z)
            	        rotateX()  沿着x轴旋转；  2d旋转用的是 rotate（）、rotateZ()





24. 动画制作

    animation：动画名称 花费时间 运动曲线 何时开始  播放次数（n 或者 infinite）  是否反方向（alternate 反向  normal（直接回原点））;

    **步骤：**

    > ```
    > @keyframes heart {
    >    0% {
    >       transform: scale(1);
    >    }
    > 
    >    50% {
    >       transform: scale(1.1);
    >    }
    > 
    >    100% {
    >       transform: scale(1);
    >    }
    > }
    > //在css样式中使用：
    > animation: heart 0.5s  infinite;  /*一个叫heart 的动画  每隔0.5s 执行动画 无限次*/
    > ```

      

25. 伸缩布局 ：flex；---------见新的文档
        父元素设置 diplay:flex; 子元素设置flex份数 ， -----最简单的应用。

    > 基本规则：
    >
    > 		**有margin 先用总的扣掉 再分份数；**
    > 		**当子元素 设置固定大小时，去掉固定的 剩下的 不固定（伸缩的）分；**



26. 一些冷门样式：

    + background-size ：规定背景图片的大小；

      ​	background-size: 100px  100px;   -----可以设置百分比哦~

         **background-size: 100px;-------  如果只有一个值  后面一个值默认为 auto  等比例缩放**

         background-size: cover;  把背景图片尽可能放大；保证图片始终充满背景区域，如有溢出部分则隐藏

         background-size: contain;    会自动调整缩放比例，保证图片始终完整显示在背景区域

    

    + 多背景：background: url(images/2.jpg) no-repeat top left , url(images/3.jpg) no-repeat bottom right;
    + 背景渐变：background: -webkit-linear-gradient(top, red 0%, green 50%, blue 100%);



27. 浏览器前缀
        -webkit  为了让低版本浏览器支持（谷歌前缀）；
        -moz   让火狐支持 火狐前缀
        -ms  让微软支持



--------------------

## 辅助工具ps和fw的操作

+ ps操作：day5----13
     标尺；（ctrl+r 显示标尺）右击标尺 改成像素

     吸管 ： 可以吸取颜色；
     测量宽高： 选中矩形 选框工具（可以测得宽高） 取消选中的  用ctrl+d
     辅助线： 直接从标尺中拖拉出来  测量版心 他用了
     用顶行的视图 里面有清除所有的辅助线

  

  切图工具：在切logo的时候用的 切片大小可以调节  再导出 点击 web所用格式：
        存储的结果中  ：要选中 选中的切片

  删除切片： 用切片选择工具： 选中就删除；
  或者用顶行的视图 ： 里面有清除切片  可以清除掉所有的切片；

注：不会的操作：

> (如何看字体的大小  不会弄  )
>     如何看一个字体的大小： 选中ps中的文本框：
>
>    ps中的图层的操作  ： 删除了图中的几个小圆点
>
>    图层切图  这块不行



+ fw操作（精灵图最佳）---day7 滑动门