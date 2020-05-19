
静态语言（强类型语言）
静态语言是在编译时变量的数据类型即可确定的语言，多数静态类型语言要求在使用变量之前必须声明数据类型。 

例如：C++、Java、Delphi、C#等。
动态语言（弱类型语言）
动态语言是在运行时确定数据类型的语言。变量使用之前不需要类型声明，通常变量的类型是被赋值的那个值的类型。 
例如PHP/ASP/Ruby/Python/Perl/ABAP/SQL/JavaScript/Unix Shell等等。


1、script标签如果是引入外部的js文件,这个标签中不要添加内容~
2、变量名是地址的别名 ，可以通过变量名访问变量
3、null表示空值、 可以对一个变量赋值是null，NaN  不是一个数
   一般用  ！exp判断是不是空（但是不严谨）

4、parseInt(true)  ------结果 nan

    隐式转换
    ==是比较运算符，所有两边都是转成Number型。[ ]转成0，true转成1
    ！是逻辑运算符，所以会转成Boolean，[ ]转成true,前面加！！所以还是true
     两个不是值的值比较不可能相等


进制转换：num.toString(2)；---结果是字符串

5、if只要第一个条件满足了  后面的哪怕true也不会执行 了------好像不对

6、break 是跳出循环 和switch的---不是跳if的
    continue语句只能用在while语句、do/while语句、for语句、或者for/in语句的循环体内

7、//var arr1=new Array(10,80,60,50,20,30,40);
   //console.log(typeof arr1);/*   放回的是object*/  --------------------------联想原型
    arr1=[10,80,60,50,20,30,40];
    console.log(typeof arr1);   /*   放回的是object*/


    类型： 基本类型 number boolean null string undefined
            引用类型  object               --------这些都是typeof会返回的值

            引用类型 内部又包括 （Object Array Math RegExp Date Error  | 包装类型：Number String Boolean ）


8、函数没有返回值，却调用的时候用变量接收了，那么结果就是undefined；
   函数调用，如果某个参数没穿，这个值就是undefined
   function apt(a,b){
        console.log(a+"----"+b)
    }
    apt(2)  // 2------undefined；

    另外：
    var b=function(d,k,l){console.log("gsfg")};

    console.log(b.length)//返回形参的个数

9、函数也是一种数据类型： typeof func_name；  结果是function---------------------联想原型

10、函数表达式：
           var f1=function (){
                   console.log("dfasdf");
                  }；
            f1();//函数调用； 这里的函数调用可以 这样理解：f1相当于是变量  赋值的值是函数代码
                             加上（） 就是调用
            //（*************）本身函数调用实质   就是  函数代码+（）；


（*********）如何定义一个动态函数名的函数：

   var funcname=“fasdasd”；
   window[funcname]=function(){}

11、声明的变量是var声明的，那么这个变量就是全局变量；全局变量就可以在页面任何位置使用；
    除了在函数以外，其他的任何位置定义的变量都是全局变量；
    全局变量  是可以跨script标签使用的  --------（**************）很厉害呀


局部变量：在函数内部的定义的变量，是局部变量；只能在函数内部被调用；函数调用结束之后 内存就释放；也是var调用的

      函数内部用的不是局部变量的话  结束就不会被释放；
    函数内部调用的值；若本层中没有定义该局部变量，会去看看它的上一级 有没有同名的变量存在
          如果有的话，会去调用这个；一次从里向外找；

12、作用域链：
    在一个函数中使用一个变量，先在该函数中搜索这个变量，找到了则使用，找不到则继续
        向外面找这个变量，找到则使用，一直找到全局作用域，找不到则是undefined；

13、预解析：  变量声明  var n 和 函数声明 function（）{console.log("...")}都会提前到当前作用域的最上方
     所以函数声明在前在后 不影响调用执行
   另外  script的标签内的也是一个作用域  只能提前到当前的script标签内部上方

函数提升大于变量提升，变量提升会提升到除函数声明的后面；

14、对象： new Object（）    字面量方式  自定义构造函数
      通过自定义构造函数定义的   下面的结果是true（****-------------------------------------------------联想原型  先了解 ）
      console.log(obj instanceof Person)  放回true
  instanceof  表示 是引用类型的变量  obj instanceof Person  ---前面是变量  后面是构造函数的名字（书上叫引用类型）
    Person 叫一种引用类型


15、访问对象的两种方式： 点访问和[]访问；

对于点访问  无论属性的键 带不带双引号，在访问时候加不了双引号；（可以访问带双引号的键值）

对于[]访问  访问属性的时候，不管属性的键带不带双引号，则访问的都要带双引号（此时引号不能省），----在控制台上面测试的


16、遍历对象 for (var key in json){}

17、11-5-4 是很重要的一节    ----------------自己懂了
   主要介绍两点： 基本类型值和引用类型  解析器会做不同处理
       在   复制变量值 和 函数传递参数的时候  会有区别 -----对象中存入的是地址  函数传递也是传值
                                                            所以 函数内部操作属性方法  会改变外面的对象的 结构

    对象中也是这样存储的；  4-28   见 11-5-4   有测试里：
          objtest={a:"123",b:[1,2,3],c:{"a":"1","b":"2"},func:function(a,b){return a+b}}
            var k1=objtest.a;
            k1="234";
            console.log(objtest);  //原对象没有改变
            var a1=objtest.b;
            a1[2]=7;
            console.log(objtest);   //原对象改变了； 因为传递的是地址
            console.log(a1[2]);
            a1=[6,7,8];
            console.log(objtest);
            console.log(a1);

18、静态对象（不需要实例化对象 直接调用） 和 实例对象（实例化以后 对实例进行调用）
        实例方法----必须通过new的方式创建的对象（实例对象）来调用方法；
        静态方法----直接通过大写的构造函数的名字调用的方法 如：String.fromCharCode()


19、string 和String对象
   普通的string是没有方法的 在调用方法的时候  会去先包装成String对象  在调用方法

   字符串的不可变性：var string="hello";  string[1]="w"   //这个是不可以操作的； --------记住就好 可能和语言底层设计有关；
    字符串可以遍历；

20 如何判断一个对象属性和方法是不是存在的
   if（obj[name]）{}


21、常见内置对象的方法：
        Math.ceil(Math.random()*5) 生成  0-5的方法  也可以用parseInt（）
    字符串：
        1、str.indexOf("xiadasdo",5); 从下标5开始找  ，没找到返回-1；----通常用于判断是否拥有某个字符串
        2、str.match(); ---正则表达式（replace也只支持正则表达式）

-------这是一个不改变自身实例的一个方法------------
        3、str=str.replace(str1，str2)  替换值 在str中 把str1 换成str2  但是 str没有改变
                要用一个返回值接住 再用str 就是的到改变后的了
        例子：
            var str1="起码的是五分豪情";
            str2=str1.replace("五分","十分");
            console.log(str1);          //起码的是五分豪情
            console.log(str2);          //起码的是十分豪情

        4、str.slice(start,end)  ---截取切片；没有end   返回的是截取后的片段  依然不改变原有实例；
        5、str.concat()
        6、str.split("")  返回数组
        7、substring(start，end)  也是切字符串  （） （****于slice的区别是）  substring() 不接受负的参数。

       8.match() ---查找字符串
	            var str = "今天天气好好";
                var result = str.match("天天");
         	    console.log(result);//["天天", index: 1, input: "今天天气好好", groups: undefined]
       9.search()-----查找字符串返回下标
	var str = "今天天气天天好好";
        	var result = str.search("天天");
        	console.log(result);//1

      10、includes--检测是否包含指定字符串


     数组方法：
        arr.every(function（ele,index，arr本身）) 用来测试数组的每个元素；返回布尔类型 (如果所有的元素都复合条件，才返回true)

        arr.filter(func),  返回数组中每一个元素都复合条件的元素，组成了一个新的数组

---------这几种方法  调用就会改变调用它们的对象  arr直接变---------叫变异方法：
        .push(val): 在数组后面追加一个val； 返回值是追加的值
        .pop(): 删除最后一个元素；返回值是删除的值
        .shift(): 删除数组中的第一个元素； 返回值是删除的值
        .unshift(): 向数组的第一个元素前面插入一个新的元素
        .sort()  但是排序不稳定  （sort中也可以传函数，写固定的函数就稳定了）
             函数的写法也有讲究：return 1 0 -1；  //形参的a,b 相当于以前 a[j],a[j+1]

         .splice(index,要删除的个数,val)  //返回的是 切的以后的值  在index后面添加val    ，一般是用于删除数组中的元素；
                              或是替换元素，或是插入元素；
                .splice(index,1)------删除index元素；，index也算；  -------只删除不替换

         关于数组方法splice用法：

            splice（1，0，'Tom'）：表示在索引为1的元素前面（注意是前面插入）插入元素’Tom‘（也可以理解为从索引为1的元素开始
            删除，删除0个元素，再在索引为1的元素前面添加元素'Tom'）；

            splice（1，1，'Tom'）：表示从索引为1的元素开始删除（包括索引为1的元素），共删除1个元素，并添加
            元素'Tom'。即把索引为1的元素替换为元素'Tom'。
--------------------------------------------------------------------------------------------------
-------这是一个不改变自身实例的一个方法------------

        .slice(firstindex，lastindex)  // 切一部分返回一个数组，不包含结束的索引
	.slice(0)   就是不切返回（相当于克隆一个新的）
		高手代码里看到.slice(0)，查了下这样写的好处：
	1.对原数组进行深拷贝，这样进行一系列操作的时候就不影响原数组了；

	2.将类数组对象转化为真正的数组对象：var anchorArray = [].slice.call(document.getElementsByTagName(‘a’), 0); 

       arr1.concat(arr2) -----------组合数组 不改变arr1 和arr2

        .foreach(func):  遍历数组  相当于for循环 -----内置的回调函数 可以实现对每一个元素操作
                var arr=[10,20,30];
                arr.forEach(function (ele,index) {
                    console.log(ele+"==="+index)
                });

        arr.indexOf(val):  //返回的是索引，没有就是-1；

        .join("|")   //  返回字符串；

        .map(func):  数组中的所有元素都要执行一次这个方法~ ,把执行后的结果重新放在一个新的数组中；




总结： 这些方法 有的会对调用实例 产生改变 ，有的不会 ，有的因为功能在于 其返回值  一个不关心调用实例是否变化，一个也肯定不会变化

        主要在意那些会对调用实例 改变的方法  数组中的有 splice push pop shift unshift（插入） sort
                                               字符串中目前没有


22、基本包装类型： 本身是基本类型；但在执行代码过程中，如果这个类型的变量调用了属性或者是方法
那么这种类型就不再是基本类型了，而实基本包装类型，这个变量也不是普通的变量了，而实基本包装类型对象；

    var num=10;
    console.log(num.toString())
    console.log(typeof num)---------还是number  可能是应该 该方法 不会对调用实例做改变？？  这和语言的设计有关

JS 中值的类型分为原始值类型和对象类型。原始值类型包括 number, string, boolean, null 和 undefined；对象类型即 object。首先原始值类型它就不是对象。
另外，要注意 'hello' 和 new String('hello') 的区别，前者是字符串字面值，属于原始类型，而后者是对象。用 typeof 运算符返回的值也是完全不一样的：
1
2
typeof 'hello';  // 'string'
typeof new String('hello');  // 'object'
之所以很多人分不清字符串字面值和 String 对象，归根结底就是 JS 的语法对你们太过纵容了。当执行 'hello'.length 时，发现可以意料之中的返回 5，
你们就觉得 'hello' 就是 String 对象，不然它怎么会有 String 对象的属性。
其实，这是由于 JS 在执行到这条语句的时候，内部将 'hello' 包装成了一个 String 对象，执行完后，再把这个对象丢弃了，
这种语法叫做 “装箱”，在其他面向对象语言里也有（如 C#）。不要认为 JS 帮你装箱了，你就可以在写代码的时候不分箱里箱外了


js的单线程环境、定时器运行---https://blog.csdn.net/Febby_/article/details/94763441
    在所有同步任务执行完之前，任何的异步任务是不会执行的


//console.log(parseInt(true))//   结果是NaN 因为 （会先默认转成字符串 ---所以是nan）

     //if 判断 true了后  后面的不会执行
    // var num1=10;
    //  if(num1>5){
    //      console.log("dayu ")
    //  }else if(num1>6){
    //      console.log("fasdfasd")
    //  }

   //预解析的例子
  // function f1() {
  //    console.log(num);//undefined
  //    var num=10;
  //  }
  //  f1();
  //  console.log(num);//  报错


   // 跨script标签的预解析：
    // var  num=10;
    function f1() {
      console.log("哈哈");
    }
    f1()
    console.log(num)

----/script
----script----

      var  num=10;
    f1();
    function f1() {
      console.log("嘎嘎");
    }
    console.log(num)
