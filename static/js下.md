1、对象： -------（所以一般对象 指的是实例化以后的）

2、对象中的属性是 基本类型的怎么存储？？？？

3、console.dir(per)的结果是  其构造函数定义的属性和方法（是赋值之后的）+_proto_(里面有一个constructor和_proto_)
   console.dir(Person)的结果  构造函数内容  + prototype+ __proto__（函数自己的原型Function.prototype）

   本来是 console.log(per.__proto__.constructor==Person);===》规定这样console.log(per.constructor==Person);//  true
                虽然per并没有这个constructor属性的；

注：console.dir(Person) 的结果 里面的Person.prototype.constructor 也有自己的构造函数：  --------------------注意

   关系可以在三者关系的图中反应出来；


实例对象dir后 会显示 定义的属性和方法（是赋值之后的）
构造函数内容中 并没有这些属性和方法 （没有 age和name 等）


4、进一步通过原型解释实例对象和 构造函数的结构

    * 构造函数可以实例化对象
    * 构造函数中有一个属性叫prototype,是构造函数的原型对象
    * 构造函数的原型对象(prototype)中有一个constructor构造器,这个构造器指向的就是原型对象所在的构造函数
    * 实例对象的原型对象(__proto__)指向的是该构造函数的原型对象
    * 构造函数的原型对象(prototype)中的方法是可以被实例对象直接访问的（*******）

通过原型添加的方法 可以实现数据共享  这个方法也只有在实例对象的原型中可以找到，实例对象可以用其原型的方法

    * 构造函数的原型对象(prototype)中有一个constructor构造器,这个构造器指向的就是该原型对象所在的构造函数

（因为原型对象是在构造函数结构 内部的      构造函数.prototype  ）

另外： //实例对象的原型__proto__指向的是该对象所在的构造函数的原型对象
    //构造函数的原型对象(prototype)指向如果改变了,实例对象的原型(__proto__)指向也会发生改变

5、原型的第一个作用就是共享数据 ---节约资源
   简单写法中需要手动指定构造器的指向    constructor:Student,

6、原型中的方法,是可以相互访问的

    背景： //实例对象的方法,是可以相互调用的
       而 原型中的方法也是可以相互访问的：（在调用eat（）中调用play）

7、实例对象使用的属性或者方法,先在实例中查找,
    找到了则直接使用,找不到则,去实例对象的__proto__指向的


8、局部变量变成全局变量：
    把这个局部变量给 window 就可以全局用了  （用到自调用函数 ---window参数是可以不加的 ）

    这里面应用了js语法中的两点：
          一、通过函数参数，对象局部修改可以修改，可以实现全局修改；----传入的是一个对象
          二、window是一个特殊的全局对象 ，window可以省略；  ------直接是num

          //把局部变量给window就可以了
      (function () {
        var num=10;//局部变量
        //js是一门动态类型的语言,对象没有属性,点了就有了
        window.num=num;
      })();
      console.log(num);

9、原型链 以及原型的最终指向：
    一个原型对象 也是有原型的（这时候 可以看成原型对象是一个 实例对象），
    举例： new Person（） 是通过Person()构造函数实例化出来的
        new Person() 是一个实例对象，其原型对象 是Person.prototype ,（person.__proto__ 指向 同Person.prototype）
        原型对象 也是一个对象 （可以认为它是 new Object 出来的实例对象  所以） 它的原型是 object.prototype

    （下一级原型相对 上一级 就像是一个实例对象 ）

10、原型的指向可以改变；  ------继承中会用到
     Student.prototype=new Person(10);
 这里面new Person(10)实例对象（它指向自己的原型对象）就是student的原型对象
        （原型链的层又多了一层了*************）


11、继承---
        组合继承:原型继承+借用构造函数继承（call）
          function Person(name,age,sex) {
            this.name=name;
            this.age=age;
            this.sex=sex;
          }

          Person.prototype.sayHi=function () {
            console.log("阿涅哈斯诶呦");
          };

          function Student(name,age,sex,score) {
            //借用构造函数:属性值重复的问题
            Person.call(this,name,age,sex);
            this.score=score;
          }

12、this指什么：
     普通函数中的this是谁?-----window
     * 对象.方法中的this是谁?----当前的实例对象
     * 定时器方法中的this是谁?----window
            定时器是window的方法,相当于window.setInterval，
     * 构造函数中的this是谁?-----实例对象
     * 原型对象方法中的this是谁?---实例对象

13、apply和call和blind的使用
    只要是想使用别的对象的方法,并且希望这个方法是当前对象的,
    那么就可以使用apply或者是call的方法改变this的指向 （也有函数调用的功能）

    func.apply(对象,[参数1,参数2,...]) 后面的参数是给func的形参  改成 函数是这个传入对象的方法

 //牛客网：---使用闭包
     实现函数 makeClosures，调用之后满足如下条件：
    1、返回一个函数数组 result，长度与 arr 相同
    2、运行 result 中第 i 个函数，即 result[i]()，结果与 fn(arr[i]) 相同
    //function makeClosures(arr, fn) {
    //    var result=[];
    //    for(var i=0;i<arr.length;i++){
    //        result[i]=function(){
    //            return fn(arr[i]);
    //        }
    //    }
    //    return result
    //} ---这种写法i是等到执行的时候  i是arr.length;因为闭包中的变量不释放；

    function makeClosures(arr, fn) {
        var result=[];
        for(var i=0;i<arr.length;i++){
            result[i]=fn.bind(null,arr[i])//  写成fn 没有参数 ，写成fn（arr[i]）是一个调用（***************）
        }
        return result
    }

14、函数作为返回值使用：
        个人感觉，1、使用函数作为返回值，可以增加一个函数的参数的的方法：
               适用在不方便给函数添加形参的时候，就像arr中的sort方法中的形参函数；他只能传数组中的两个值；

          2、 后面结合闭包使用 可以达到缓存值得用法；

15、闭包：（函数A内部有一个函数B ，函数B用了函数A中的参数）
   结合函数作为返回值 （返回的函数就是函数B，形成闭包）
   函数作为返回值 ，可以做到  缓存数据功能
   三次调用生成同一个随机数  （缓存数据）

   ----闭包中的变量不会被回收；

16、沙箱：
    (function(){})  沙箱内部发生的事情并不影响外界的变量； 就像是 一个函数内部

    沙箱解决了 变量名和函数名冲突的问题，

17、深拷贝和浅拷贝：----还是得靠百度；

18、正则表达式
