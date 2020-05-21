# flex布局

参考视频：

[flex属性介绍] https://www.bilibili.com/video/BV1hE411c7zz?from=search&seid=13478762790239323054

[grid栅格布局]https://www.bilibili.com/video/BV1kE411g7c8     

[flex快速入门----有图便于理解]https://www.cnblogs.com/abc-x/p/11100711.html

[flex属性解析----有图便于理解]https://www.cnblogs.com/kinblog/p/11545368.html

[知乎]https://zhuanlan.zhihu.com/p/103219555

## 属性一览：

+ #### 基本布局（只设置一个display：flex----- 所以大多属性都是默认值 ）

  在父元素.container中加入`display:flex `后，子元素 会依次从左到右横向排列（默认排列方式）；

  **这个时候就分情况： 如果父元素的宽度（因为默认横向，所以是看宽度）是否足够放下这些子元素：**

  ​		足以放下他的子元素，子元素就是他们自己的宽度；（右边会有空余空间）
  ​		如果不足以放下他们子元素，子元素的宽度会等比例缩小;（宽度还是宽，窄得还是窄）

  这时候如果想设置：分行显现：设置属性` flex-wrap:wrap  `（默认：nowrap）

  ​        此时 每个子元素的宽度就不用随着缩小了---在父元素宽度不够的时候

   **但是在多行显示中 ，如果子元素的高度 不到 400px，会出现 相邻行之间会有空白间隙；（就是说每一个flex行是有一个高度的，就是图书馆的每格书架一样 ），当超过这个400px，就没有空隙了，这个flex行的高度就是随之增大**

  

+ #### 父元素其他属性：

  + flex-direction：**改变主轴方向的**；row默认 （column 列）

    > justify-content 和 align-content 其实分别指的指 主轴和 副轴的方向的
    >
    > 

  + justify-content : 设置靠主轴的子元素布局方式   flex-start默认

    其他属性值：  flex-end  center  space-between（中间留空隙--空隙等宽）space-evenly（两边中间都溜空隙 ）

---

以上样式  ，如果出现分多行现象，高度又不够一个flex行的高度时候，还是有纵向的空白间隔





----

+ + align-content：设置靠副轴的子元素布局方式，属性值和上面一样    **没有默认值的**

    ​                -------flex-start，flex-end， center**可以消除 行与行之间的空白  **

    

  + align-items： 控制每flex行的内部的子元素**副轴**上的 布局； stretch  默认值

    ​		 stretch：**当子元素不设置高度的时候 会将子元素高度设置成每flex行的高度**

    ​        其他属性值 ：flex-end  center  space-between

    

+ ### 子元素属性

  + flex-shrink：缩小的比例值  （默认是1）  flex-shrink：2---------- 缩小的比例值  （默认是1）

    

     当 nowarp的时候一行显示不够，会压缩每个子元素得宽度；

     （若不想压缩某个子元素，则设置 **flex-shrink：0**）

     默认比例是1时，他们是按照每个子元素的宽度进行**等比例**压缩的。宽度大的压缩得多，

    设置比例越大，压缩得越狠；

  +  flex-grow：放大的比例值   默认是0  

    当一行**本来会留有空白（不设置flex-grow）**的时候， 设置flex-grow的子元素 宽度会将空白的宽度并给自己宽度：数值就是比例） 

  + flex-basis：设置宽度；设置每个子盒子的宽度；

    

  + flex ：栅格布局--------------最常用

    可以将flex-grow, flex-shrink, flex-basis进行连写。flex-grow属性定义项目的放大比例，默认为0，即如果存在剩余空间，也不放大。flex-shrink属性定义了项目的缩小比例，默认为1，即如果空间不足，该项目将缩小。flex-basis属性定义了在分配多余空间之前，项目占据的主轴空间。
    浏览器根据这个属性，计算主轴是否有多余空间。它的默认值为auto，即项目的本来大小。flex属性是flex-grow, flex-shrink 和 flex-basis的简写，默认值为flex: 0 1 auto。简写还包括：

    - flex: 1; -->> flex: 1 1 0%; flex: none; -->> flex: 0 0 auto
    - flex: auto; -->> flex: 1 1 auto; flex: 0 auto
    - flex: initial -->> flex: 0 1 auto; 即flex的初始值

  + order：控制子盒子顺序：（本身默认是0）（0排完了排1的）相同的order值，html结构中前面的在前面





# 栅格布局

