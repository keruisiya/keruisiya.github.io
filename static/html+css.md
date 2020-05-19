


一共三个大案例： 云道、京东、学成在线
疑问：通栏居中为什么要用一个盒子嵌套包裹呀； 因为又要通栏又要居中呀


1、html常见标签（day1）
2、表单中label标签，label中的for 属性 用于和表单中的id 绑定
（****）重置按钮和提交按钮 在form中才可以用；

    表格（设置三参为0  border，cellspacing cellpadding）、介绍合并单元格
3、行内式；（偶尔使用）、内部样式表、外部样式表
   行内权重高，但是只能控制单个标签

4、标签命名规范：web前端开发规范手册.doc ---------- https://www.cnblogs.com/xiaonian0327/p/7735799.html
    常用查询文档： w3c、MDN
    拔网页小工具：day12中

5、css三大特性：
        层叠性： 后来的css代码中样式 会覆盖前面的；
                    样式不冲突 ，不会层叠；

        继承性：子标签会继承父标签的 某些样式；
            如： color  text-  font-  line- 都是可以继承的；
            但是高 是不继承的；margin和padding是不会继承的（显而易见好吧）

            恰当的利用继承性可以简化代码，降低css样式的复杂性；

        优先级：
             id选择> 类选择器> 标签选择器；

             标签权重  0，0，0，1；
             类选择器  0，0，1，0；
             id选择器  0，1，0，0；
             行内样式  1，0，0，0；
             ！important 无穷大；

            * 和继承   0，0，0，0  权重最小；
        记住的： 父元素的权重再大  继承过后  子元素的权重也还是0；

        权重是可以叠加的：(子代选择器 交集选择器都会叠加)
            div ul li  0，0，0，3
            .nav ul li 0，0，1，2
            a:hover 0,0,1,1;（********）


                1、权重相同 ，则就近原则；
                2、权重会叠加
                3、记住权重是不进位的   0005+0005 ！= 0010 的  而是0，0，0，10；


a:hover .mask （空格 表示后代选择器 表示 a里面的mask显示出来）（*********伪类选择器 的这种形式的理解）



6、标签的分类： 块级元素（独自站一行  可以设置宽高 对齐属性）
                      如：h1  p  div ul ol li

                 特点：默认的宽是100%
                        可以容纳内联元素和其他块元素

                行内元素
                         如 a strong em b i del s span等

                  特点：不占独立的区域； 仅仅依靠自身的字体大小和图片支撑结构
                        不可以设置宽度 高度 对齐属性（text-align 因为宽没用了 也没用了）；
                        默认的宽度就是他自身的内容的宽度；
                        行内元素只能容纳文本或者其他行内元素（a特殊）

                行内块元素（inline-block）
                    如： img input  td

                    特点： 和相邻的行内元素（行内块）在一行上 但是之间会有白色空隙；
                            默认宽度就是它本身内容宽度
                            高度行高 外边距和内边距都可以控制；

(************************)
 行内块元素和内容有关系的； 如果没有内容  又没有设置宽或者高  就是空的；
 行内元素和行内块元素 的宽度 不是设置的默认100%了  而是内容多少就是多少，内容为空就是0

 a标签 span行内元素  也是不会被图片撑开 ； 宽度是 图片的宽度， 但是高度还是自己的

行内元素与块级元素的区别之一就是 对于行内元素来说margin只
        有margin-left和margin-right有效，padding只有padding-left和padding-right有效


 (**************************)

                一、块级元素 内部文字水平居中
                      行内元素和行内块元素可以看成是文本  可以使用text-align居中对齐；

                二、 虽然块级元素内部可以放 块级元素和行内元素以及行内块元素；
               但是 对于p和 h1标签而言  文字才能组成段落  ，所以在p标签和 h1 标签中也一般不装块级元素


               三、虽然行内元素只能容纳文本或者其他行内元素
                 但是a特殊  是可以放块级元素的
                 （a放块级元素的时候是不是将自己变成行内块元素或者是块级元素）

7、样式连写：字体font 背景background 文本（color，text-decoration，text-align、line-height）
     背景位置介绍：
        background-position : x，y （可以用方位名词 center top left 也可以用px 混合用也可以） （精灵图用的）
            /*1. positon后面可以跟方位名词  他们之间可以没有上下顺序*/
			/*2. position 如果只写一个方位名词，另外一个默认是居中的*/
			/*3. position 后面也可以跟 值px 但是 必须有顺序 x 在前面 y 后面 不能颠倒 */
        background-position : 10px，center   是可以的
     left top 是默认值；

（*******） 位置中的center 是把背景图放在盒子的中线上；

          如果图比盒子大的话 ，图会超出盒子 的  也就是图的中心部分还是在盒子的中心的；

    font的连写： font：12px/1.5 （表示的是行高 1.5* font-size）

    注意：background-attachment

    行高是用在单行文本中的

8、 经常混淆的几个样式：
    背景透明：rbga() 用在background中   盒子阴影 box-shadow
     盒子透明 opacity  盒子包括盒子的内容都透明

        透明设置方式背景：background： rgba(0,0,0,0.3 )

        盒子阴影（css3）box-shadow：水平阴影  垂直阴影  模糊距离  阴影尺寸（就是影子的大小）  颜色   内外阴影（默认外阴影）

        盒子透明 opacity: 0.2;  /*盒子半透明  字也透明了 盒子也透明了*/

盒子模型：
9、input中的边框也可以使用border；

10、盒子居中；满足条件： 必须是块级元素；盒子必须指定了width才可以； margin ：0 auto （设置左右自动充满）
    块级元素单行文本垂直居中 --------  line-height=height
    定位的盒子居中对齐

11、margin的两种坍塌现象；-----子元素带着父元素垂直方向跑；
        现象描述： 对于两个嵌套关系的块元素， 如果父元素没有上内边距 和边框 则父元素的
        上外边距会与子元素的上外边距发生合并 ，合并后的外边距为两者中的较大者，即使父元素
        的上外边距为0，也会发生合并。

12、 添加padding会撑开带有width和height的盒子； （********）没有设置宽高的不会撑开

    如果一个子盒子没有给定宽度/高度，就会用其父类的属性，这时padding不会影响子盒子的大小(会自适应调节width)

浮动和定位：
13 浮动----最早是用来实现文字环绕图片的；现在目的就是为了让多个块级元素在同一行上显示
   （同一行上显示以前用inner-block做的，  但是它实现不了 靠页面右边显示。还有一个是inner-block 是有缝隙的）

14、浮动特性：
浮动式脱离文档流   是不占位置的；会影响后面的标准流
             因为浮动是在原有位置基础上 浮动的( 三个div 中间一个不设置float：left  第三个不是接在第一个div后面的)

（********） 浮动并不是完全意义上的脱标（文字不会被盖住  还有图片也是）

15、清除浮动：---清除浮动的本质就是： 为了解决父级元素因为子级浮动而引起内部高度为0 的问题；

    四种方法：伪元素清除浮动

16、定位的主要属性 就是定位模式（static（默认） relative absolute fixed）和边偏移 top left...；

17、静态定位static   唯一的用处就是取消定位

18、left: % 的时候是父元素的盒子宽度的大小；（就是说 width+padding的后的值）
（*******************************）
    定位中left的值和right的值同时出现的时候 以 left和top为准
        这个和css的层叠性没关系  也就是和先后设置没关系

      同时设置margin-left和margin-right也是  以left为准


19、相对定位：根据自己的左上角进行定位，相对定位 原先的盒子位置依旧是保留的，会是压住标准流中的元素的（*******）

20、绝对定位是将元素依据最近的已经定位的 父元素（祖先）进行定位，是脱离标准文档流， 不占位置的 -----叫做完全脱标；

21、定位的盒子居中对齐： （设置relative的盒子基本不受影响，一般父盒子会有relative 也会有margin：0 auto）
    ps： 加了浮动和定位（不包括relative） margin：x  auto  就失效了（**************）

      position：absolute；
      left：50%；
      margin-left：-50%*weight；（盒子宽度的一半）

       top:50%
       margin-top:-50%*height

22、固定定位： 父元素加不加position  top和left值都是相对浏览器页面的；


23、z-index：（叠放次序）  表示的是z轴 ；-----改变叠放次序
-----------只有定位（relative，absolute，fixed都有）的盒子才有z-index
            ----浮动  静态定位都是没有z-index的；
-----------z-index取值相同，后来者居上；

   如果没有设置z-index 相同的 就后来者居上覆盖（但是并不是说它的z-index 依次变大）


24、显示与隐藏：（三种 j visibility overflow）
      display：none 隐藏  block就是显示
            隐藏之后是不保留位置的（************）

       opacity隐藏保留位置（但是h5c3中用了 position：就可以达到不占位置了）

    （了解）
      visibility:visible hidden (inherid 是默认的  )
            隐藏后是保留位置的；

      overflow; 溢出隐藏；


25、鼠标拖拽  轮廓和防止拖拽
   不是只有a才可以设置cursor  p img div 都可以
     /*cursor: pointer; 让我们的鼠标样式变成小手*/
		/*cursor: text;  让我们的鼠标样式变成选择  I*/
		cursor: default; /* 让我们的鼠标样式小白*/
        cursor: move;  /*鼠标变成十字架样子*/

  轮廓 outline: ---------一般都是结合表单和表单域使用
        outline: none;  /*取消轮廓线的做法*/ /*取消蓝色边框*/
             或者用outline：0

  防止拖拽 防止它影响布局
      resize: none;  /*防止拖拽*/

26、div直接装一个图片也会出现一条缝隙问题； -------div没设置 图片的height 高度；

   图片和文字等inline元素默认是和父级元素的baseline基线对齐的，div不设置高度的时候 视其内容撑开盒子；所以导致这个问题
   而baseline又和父级底边有一定距离（这个距离和 font-size，font-family 相关，不一定是 5px）

   所以设置盒子div 的 font-size: 0;或者
        line-height: 0; 也是可以的 还有设置img为block

27、溢出文字隐藏  三个样式；
    white-space: nowrap;
	/*1.强制在同一行内显示所有文本，直到文本结束或者遭遇br标签对象才换行*/
	overflow: hidden;  /* 2. 超出的部分 隐藏*/
	text-overflow: ellipsis;  /* 3. 溢出的部分用省略号替代*/

    div等容器文字只会单行显示

28、精灵图---一张大图 --操作background-position ： background: url(images/index.png) no-repeat -2px -184px;

    不好做的那个精灵图 在 day12 中的携程案例中

29、滑动门----根据内容 框适当变大 也是利用了背景图片：（父子都设置背景）

    <a href="#">
		<span>首页</span>
	</a>
    a 左边放左圆角  但是文字需要向右移动15px
   span 右边放右圆角  但是文字需要向左移动15px



30、字体图标的使用   看上去是图片  其实是字体 （****可以设置font-size） 文字 以小图标的形式展示的；
一、下载字体图标  icomoon  德国的和 iconfont 中国的 -----自己下载的放到d盘下了 D:\python\icomoon

下载： 先点左上角的icomoon app
          在选择想要的图标 后点击  右下角的generate font
           再找右下角的download 下载压缩包iconmoon；

解压后 我们只需要font文件夹复制到项目中
           其中的demo.html中是我们要去复制的 
           styles.css 里面有 @font-face {...}（下载的不同 这里也不同）

二、字体图标的使用：
        首先： @font-face {...} 复制这个内容到style中；
        其次：  在下载的 文件夹中的demo文件中 粘贴 想要的图标
        再： font-family申明字体；(必须要声明font-size中声明的字体)

     还有一种伪元素结合图标字体使用；（div::before { content: "\ea51";）


三、添加自定义的图标：  点击 import icons（了解）
    将svg图片导入到 icomoon网站上就可以转换了； svg不可以设置字体大小和颜色；
    重新下载新的压缩包 新的图标 添加 解决；

四、（*******************）追加新的图标；（又想下载新的图标了）
     不能合并  得重新下载
     将 selection.json （方便追加的）导入点击import-icons  再下载就可以

    重新下载后 再更新index

31、h5 新标签和 css选择器：
   表单标签 <fieldset>
   新增的表单 （type=url等）具有鉴定功能

   选择器（ul:last-child 结构伪类， div[class] 属性选择器）

32、伪元素：（::before 和:: end ）
    /*必须带一个属性  content
		伪元素 其实这个 before 是个盒子*/
		/* 这个盒子是行内的盒子  可以转换*/

    before 和 after 都是在div的内部的inline-block；

33、css3的盒子  量的时候包括边框  、会自适应调节 盒子内容（就是以前的width）

34、过渡：加在 要让变化的元素身上；
    /*transition: width 0.5s ease 0s, height 0.3s; 多组属性用逗号分隔*/

35、2d：移动、放缩、旋转
    移动后： 原来的位置还占用   位移 缩放都是这样
    移动后和缩放放大后的区域 和设置relative一样，不会打扰标准流的元素，只会叠盖；只有原有位置影响布局，
    translate（x，y）  只有x值 默认y为0；   50% 是走自己盒子宽度的一半

    （****************************）
        transform： translateX（-20px）；
        transform： scale（0.8）

        后面的会覆盖的

        解决：
        连写 就可以了；
        transform： translateX（-20px）scale（0.8）  （//先移动 后缩放）

36、scale和rotate 可以设置 transform-origin的
    默认中新点缩放

37、animation：动画名称 花费时间 运动曲线 何时开始  播放次数（n 或者 infinite）  是否反方向（alternate 反向  normal（直接回原点））;
    /*声明动画  关键帧  @keyframes 动画名称 {  }  */
	@keyframes

38、伸缩布局 ：flex；----默认 按列分 flex-direction: column
    父元素设置 diplay:flex; 子元素设置分数份数 ， 有margin 先用总的扣掉 再分份数
    当子元素 设置固定大小时，去掉固定的 剩下的 不固定（伸缩的）分；

    父元素可以设置min-width


39、background-size ：规定背景图片的大小；
    /*background-size:  w  h 规定背景图像的尺寸;*/
	/*background-size: 100px  100px;*/
	/*background-size: 100px;  如果只有一个值  后面一个值默认为 auto  等比例缩放*/
                    /*也可以设置百分比： */
	/*background-size: cover;*/    cover  ：把背景图片尽可能放大；保证图片始终充满背景区域，（如有溢出部分则隐藏）

	background-size: contain;     contain： 会自动调整缩放比例，保证图片始终完整显示在背景区域

   多背景：background: url(images/2.jpg) no-repeat top left , url(images/3.jpg) no-repeat bottom right;
   背景渐变：background: -webkit-linear-gradient(top, red 0%, green 50%, blue 100%);

40、浏览器前缀
    -webkit  为了让低版本浏览器支持（谷歌前缀）；
    -moz   让火狐支持 火狐前缀
    -ms  让微软支持

41、3d变化  transform: translateX();translateY()（这两个2d中也有）;translateZ(); translate3d(x,y,z)
            rotateX()  沿着x轴旋转；  2d旋转用的是 rotate（）、rotateZ()



ps操作：
   一、标尺；（ctrl+r 显示标尺）右击标尺 改成像素

   二、吸管 ： 可以吸取颜色；
   按住空格键可以移动 ；
    测量宽高： 选中矩形 选框工具（可以测得宽高） 取消选中的  用ctrl+d
    辅助线： 直接从标尺中拖拉出来  测量版心 他用了
          用顶行的视图 里面有清除所有的辅助线：

    切图工具：在切logo的时候用的 切片大小可以调节  再导出 点击 web所用格式：
          存储的结果中  ：要选中 选中的切片（*****）

    删除切片： 用切片选择工具： 选中就删除；
            或者用顶行的视图 ： 里面有清除切片  可以清除掉所有的切片；



(如何看字体的大小  不会弄  )
    如何看一个字体的大小： 选中ps中的文本框：

   ps中的图层的操作  ： 删除了图中的几个小圆点

   图层切图  这块不行