# ES_study
学习ES6-11
1. ES6
1.1 let和const命令
1.1.1 let
特性

变量不能重复声明

let star='罗志祥';
let star='小猪'  //error2
let有块级作用域

{
    let girl='周扬青'
}
console.log(girl) //error24
不仅仅针对花括号，例如if（）里面

​

不存在变量提前

console.log(song)   //error
let song='恋爱达人'2
不影响作用域链

let school='abc'
function fn(){
    console.log(school) //abc
}24
案例

<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>Title</title>
</head>
<body>
    <div>
        <div class="item" style="width: 50px;height: 50px;background-color: red"></div>
        <div class="item" style="width: 50px;height: 50px;background-color: red"></div>
        <div class="item" style="width: 50px;height: 50px;background-color: red"></div>
    </div>
    <script>
        let items=document.getElementsByClassName("item");
        for (var i=0;i<items.length;i++){
            items[i].onclick=function (){
                items[i].style.backgroundColor='pink';
            }
        }
        console.log(windows.i)  //3 
        // 当var=3的时候，点击事件开始向外层作用域找，找不到，就是windows.i，此时是3，如果是let i，具有块级作用域，所以每一次触碰事件的i都是不同的。
    </script>
</body>
</html>

1.1.2 const
特性

声明常量

const A = 'abc'一定要赋初始值

一般常量使用大写（潜规则）

常量的值不能修改

也具有块级作用域

{
    const pyaler = 'uzi'
}
console.log(player) //error24
对于数组和对象的元素修改，不算作对常量的修改

const team = ['uzi','MXLG','Ming','Letme'];
team.push('Meiko'); //不报错，常量地址没有发生变化2

1.2 解构赋值
介绍

ES6 允许按照一定模式从数组和对象中提取值，对变量进行赋值，这被称为解构赋值。

数组的解构：

const F4 = ['小沈阳'，'刘能','赵四','宋小宝']
let [xiao,liu,zhao,song] = F4; 
console.log(xiao)
console.log(liu)
console.log(zhao)
console.log(song)
对象的解构

const zhao = {
    name : '赵本山'，
    age: '不详',
    xiaopin: function(){
        console.log("我可以演小品")
    }
}
let {name,age,xiaopin} = zhao;
console.log(name);
console.log(age);
console.log(xiaopin);
  
1.3 模板字符串
特性

声明

let str = `我也是一个字符串`
console.log(str,typeof str);2
内容中可以直接出现换行符

let str = `<ul>
			<li>冉海锋</li>
			<li>冉海锋</li>
		   </ul>`；24
变量拼接

let lovest = '冉海锋';
let out = `${lovest}是最帅的`;
console.log(out)  //冉海锋是最帅的2


1.4 对象的简化写法
介绍

ES6允许在大括号里面，直接写入变量和函数，作为对象的属性和方法,这样的书写更加简洁

特性

let name = 'aaa';
let change = function(){
    console.log('aaa');
}

const school = {
    name,
    change,
    improve(){
        consolg.log('bbb');
    }
}

1.5 箭头函数
介绍

ES6允许使用箭头（=>）定义函数

特性

this是静态的，this始终指向函数声明时所在作用域下的this的值

function A(){
    console.log(this.name)
}

let B = () => {
    console.log(this.name);
}

window.name = '尚硅谷';
const school = {
    name: 'ATGUIGU'
}

//直接调用
A()   //尚硅谷
B()  //尚硅谷

//call
A.call(school); //ATGUIGU
B.cal(school);  //尚硅谷
不能作为构造实例化对象

let A(name,age) => {
    this.name=name;
    this.age=age;
}
let me = new A('xiao',123);
console.me //error246
不能使用arguments变量

let fn = () => {
    console.log(arguments)；
}
fn(1,2,3)  //error24
简写

省略小括号，当形参有且只有一个的时候

let add = n => {
    return n + 1;
}2省略花括号，当代码体只有一条语句的时候，此时return也必须省略

let add = n => n+1;


1.6 函数参数默认值
介绍

ES6允许给函数参数赋值初始值

特性

可以给形参赋初始值，一般位置要靠后（潜规则）

function add(a,b,c=12){
    return a+b+c; 
}
let result = add (1,2);
console.log(result) // 1524与解构赋值结合

function A({host='127.0.0.1',username,password,port}){
    console.log(host+username+password+port)
}
A({
    username:'ran',
    password:'123456',
    port:3306
})

1.7 rest参数
介绍

ES6引入rest参数，用于获取函数的实参，用来代替arguments

特性

function date(...args){
    console.log(args);
}
date('aaa','bbb','ccc')；24

1.8 扩展运算符
介绍

扩展运算符是能将数组转换为逗号分隔的参数序列

特性

const tfboys=['AA','BB','CC']
function chunwan(){
    console.log(arguments);
}
chunwan(...tfboys);  //0:'AA' 1:'BB' 2:'CC'24应用

数组的合并

const A = ['aa','bb'];
const B = ['cc','dd'];
const C = [...A,...B];
console.log(C)   //[aa,bb,cc,dd]24
数组的克隆

const A = ['a','b','c'];
const B = [...A];
console.log(B)   //[a,b,c]2将伪数组转换为真正的数组

const A = documents.querySelectorAll('div');
const B = [...A];
console.log(B) // [div,div,div]2

1.9 Symbol
介绍

ES6引入了一种新的原始数据类型 Symbol，表示独一无二的值。它是JavaScript语言的第七种数据类型，是一种类似于字符串的数据类型。

Symbol特点：

Symbol的值是唯一的，用来解决命名冲突的问题
Symbol值不能与其他数据进行运算
Symbol定义的对象属性不能使用for…in循环遍历，但是可以使用Reflect.ownKeys来获取对象的所有键名
特性

创建

let s = Symbol('aa');
let s2= Symbol('aa');
console.log(s===s2)   //false

let s3 = Symbol.for('bb');
let s4 = Symbol.for('bb');
comsole.log(s3===s4) ///true357不能与其他数据进行运算

let result = s + 100  //error
let result = s > 100  //error
let result = s + s  //error2Symbol内置值

class Person {
    static [Symbol.hasInstance](param){
        console.log(param);
        console.log("我被用来检测了")；
        return false;
    }
}
let o = {};
console.log(o instanceof Person); //我被用来检测了，false2468应用

给对象添加方法方式一：

let game = {
    name : 'ran'
}
let methods = {
    up:Symbol()
    down:Symbol()
}
game[methods.up]=function(){
    console.log('aaa');
}
game[methods.down]=function(){
    console.log('bbb');
}
console.log(game)    // name: 'ran',Symbol(),Symbol()2468101214
给对象添加方法方式二

let youxi = {
    name: '狼人杀'，
    [Symbol('say')]:function(){
        console.log('阿萨德')
    }
}
console.log(youxi)    // name:'狼人杀',Symbol(say)246

1.10 迭代器
介绍

迭代器(lterator)是一种接口，为各种不同的数据结构提供统一的访问机制。任何数据结构只要部署lterator接口，就可以完成遍历操作。

原理：创建一个指针对象，指向数据结构的起始位置，第一次调用==next（）==方法，指针自动指向数据结构第一个成员，接下来不断调用next（），指针一直往后移动，直到指向最后一个成员，没调用next（）返回一个包含value和done属性的对象

特性

const xiyou=['AA','BB','CC','DD'];
// for(let v of xiyou){
//     console.log(v)  // 'AA','BB','CC','DD'  //for in保存的是键名，for of保存的是键值
// }
let iterator = xiyou[Symbol.iterator]();
console.log(iterator.next()); //{{value:'唐僧'，done:false}}
console.log(iterator.next()); //{{value:'孙悟空'，done:false}}246应用

const banji = {
    name : "终极一班",
    stus: [
        'aa',
        'bb',
        'cc',
        'dd'
    ],
    [Symbol.iterator](){
        let index = 0;
        let _this = this;
        return {
            next: () => {
                if(index < this.stus.length){
                    const result = {value: _this.stus[index],done: false};
                    //下标自增
                    index++;
                    //返回结果
                    return result;
                }else {
                    return {value: underfined,done:true};
                }
            }
        }
    }
}
for(let v of banji){
    console.log(v);  // aa bb cc dd
}

1.11 生成器
介绍

生成器函数是ES6提供的一种异步编程解决方案，语法行为与传统函数完全不同，是一种特殊的函数

特性

function * gen (){    //函数名和function中间有一个 * 
    yield '耳朵'；     //yield是函数代码的分隔符
    yield '尾巴'；
    yield '真奇怪'；
}
let iterator = gen();
console.log(iteretor.next()); 
//{value:'耳朵',done:false} next（）执行第一段，并且返回yield后面的值
console.log(iteretor.next()); //{value:'尾巴',done:false}
console.log(iteretor.next()); //{value:'真奇怪',done:false}246810
应用

生成器函数的参数传递

function * gen(args){
    console.log(args);
    let one = yield 111;
    console.log(one);
    let two = yield 222;
    console.log(two);
    let three = yield 333;
    console.log(three);
}

let iterator = gen('AAA');
console.log(iterator.next());
console.log(iterator.next('BBB'));  //next中传入的BBB将作为yield 111的返回结果
console.log(iterator.next('CCC'));  //next中传入的CCC将作为yield 222的返回结果
console.log(iterator.next('DDD'));  //next中传入的DDD将作为yield 333的返回结果2468101214实例1：用生成器函数的方式解决回调地狱问题

function one(){
    setTimeout(()=>{
        console.log('111')
        iterator.next()
    },1000)
}
function two(){
    setTimeout(()=>{
        console.log('222')
        iterator.next();
    },2000)
}
function three(){
    setTimeout(()=>{
        console.log('333')
        iterator.next();
    },3000)
}

function * gen(){
    yield one();
    yield two();
    yield three();
}

let iterator = gen();
iterator.next();
实例2：模拟异步获取数据

function one(){
    setTimeout(()=>{
        let data='用户数据';
        iterator.next(data)
    },1000)
}
function two(){
    setTimeout(()=>{
        let data='订单数据';
        iterator.next(data)
    },2000)
}
function three(){
    setTimeout(()=>{
        let data='商品数据';
        iterator.next(data)
    },3000)
}

function * gen(){
    let users=yield one();
    console.log(users)
    let orders=yield two();
    console.log(orders)
    let goods=yield three();
    console.log(goods)
}

let iterator = gen();
iterator.next();



1.12 Promise
介绍

Promise是ES6引入的异步编程的新解决方案。语法上 Promise是一个构造函数，用来封装异步操作并可以获取其成功或失败的结果。

特性

基本特性

<script>
    const p =new Promise((resolve, reject)=>{
        setTimeout(()=>{
            let data='数据库数据'
            // resolve(data);
            reject(data);
        })
    })

    p.then(function (value){         //成功则执行第一个回调函数，失败则执行第二个
        console.log(value)
    },function (reason){
        console.error(reason)
    })
</script>2468101214Promise.then（）方法

<script>
    const p =new Promise((resolve, reject) =>{
        setTimeout(()=>{
            resolve('用户数据');
        })
    });

//then（）函数返回的实际也是一个Promise对象
//1.当回调后，返回的是非Promise类型的属性时，状态为fulfilled，then（）函数的返回值为对象的成功值，如reutnr 123，返回的Promise对象值为123，如果没有返回值，是undefined

//2.当回调后，返回的是Promise类型的对象时，then（）函数的返回值为这个Promise对象的状态值

//3.当回调后，如果抛出的异常，则then（）函数的返回值状态也是rejected
    let result = p.then(value => {
        console.log(value)
        // return 123;
        // return new Promise((resolve, reject) => {
        //     resolve('ok')
        // })
        throw 123
    },reason => {
        console.log(reason)
    })
    console.log(result);
</script>
Promise.catch（）方法

//catch（）函数只有一个回调函数，意味着如果Promise对象状态为失败就会调用catch（）方法并且调用回调函数
<script>
    const p = new Promise((resolve, reject) => {
        setTimeout(()=>{
            reject('出错啦')
        },1000)
    })

    p.catch(reason => {
        console.log(reason)
    })
</script>
  
应用：发送AJAX请求

<script>
    //ajax请求返回一个promise
    function sendAjax(url){
        return new Promise((resolve, reject) => {

            //创建对象
            const x =new XMLHttpRequest();

            //初始化
            x.open('GET',url);

            //发送
            x.send();

            //时间绑定
            x.onreadystatechange = ()=>{
                if(x.readyState === 4 ){
                    if(x.status >= 200 && x.status < 300){
                        //成功
                        resolve(x.response)
                    }else {
                        //失败
                        reject(x.status)
                    }
                }
            }
        })
    }

    //测试
    sendAjax("https://api.apiopen.top/getJoke").then(value => {
        console.log(value)
    },reason => {
		console.log(reason)
    })

</script>

1.13 集合
1.13.1 Set
介绍

ES6提供了新的数据结构set(集合）。它类似于数组，但成员的值都是唯一的，集合实现了iterator接口，所以可以使用「扩展运算符』和「 for…of…』进行遍历，集合的属性和方法:

size返回集合的元素个数
add增加一个新元素，返回当前集合
delete删除元素，返回boolean值has检测集合中是否包含某个元素，返回boolean值
特性

<script>
    let s = new Set();
    let s2 = new Set(['A','B','C','D'])

    //元素个数
    console.log(s2.size);

    //添加新的元素
    s2.add('E');

    //删除元素
    s2.delete('A')

    //检测
    console.log(s2.has('C'));

    //清空
    s2.clear()

    console.log(s2);
</script>

<script>
    let arr = [1,2,3,4,5,4,3,2,1]

    //1.数组去重
    let result = [...new Set(arr)]
    console.log(result);
    //2.交集
    let arr2=[4,5,6,5,6]
    let result2 = [...new Set(arr)].filter(item => new Set(arr2).has(item))
    console.log(result2);
    //3.并集
    let result3=[new Set([...arr,...arr2])]
    console.log(result3);
    //4.差集
    let result4= [...new Set(arr)].filter(item => !(new Set(arr2).has(item)))
    console.log(result4);

</script>

1.13.2 Map
介绍

ES6提供了Map数据结构。它类似于对象，也是键值对的集合。但是“键”的范围不限于字符串，各种类型的值（包括对象）都可以当作键。Map也实现了iterator接口，所以可以使用『扩展运算符』和「for…of…』进行遍历。Map的属性和方法。

特性

<script>
    let m = new Map();
    m.set('name','ran');
    m.set('change',()=>{
        console.log('改变！')
    })
    let key={
        school:'atguigu'
    }
    m.set(key,['成都','西安']);

    //size
    console.log(m.size);

    //删除
    m.delete('name');

    //获取
    console.log(m.get('change'));

    // //清空
    // m.clear()

    //遍历
    for(let v of m){
        console.log(v);
    }
</script>

1.14 Class
1.14.1 初体验
介绍

ES6提供了更接近传统语言的写法，引入了Class（类）这个概念，作为对象的模板。通过class关键字，可以定义类。基本上，ES6的class可以看作只是一个语法糖，它的绝大部分功能，ES5都可以做到，新的class写法只是让对象原型的写法更加清晰、更像面向对象编程的语法而已。

特性

<script>
    class shouji {
        constructor(brand,price) {
            this.brand=brand;
            this.price=price
        }

        call(){
            console.log('我可以打电话')
        }
    }

    let A = new shouji('1+',1999);
    console.log(A)
</script>

1.14.2 静态成员
<script>
  class Person{
      static name='手机'
  }
  let nokia = new Person();
  console.log(nokia.name);
</script>

1.14.3 构造函数继承
<script>
  function Phone(brand,price){
      this.brand=brand;
      this.price=price;
  }
  Phone.prototype.call=function (){
      console.log("我可以打电话");
  }
  function SmartPhone(brand,price,color,size){
      Phone.call(this,brand,price);
      this.color=color;
      this.size=size;
  }

  //设置子级构造函数原型
  SmartPhone.prototype=new Phone;
  SmartPhone.prototype.constructor=SmartPhone;

  //声明子类方法
  SmartPhone.prototype.photo = function (){
      console.log('我可以玩游戏');
  }
  const chuizi = new SmartPhone('锤子',2499,'黑色','5.5inch')
  console.log(chuizi);
</script>

1.14.4 Class的类继承
<script>
    class Phone{
        constructor(brand,price) {
            this.brand=brand;
            this.price=price;

        }
        //父类的成员属性
        call(){
            console.log('我可以打电话')
        }
    }
    class SmartPhone extends Phone{
        constructor(brand,price,color,size) {
            super(brand,price);
            this.color=color;
            this.size=size;
        }
        photo(){
            console.log('拍照');
        }

        playGame(){
            console.log('打游戏');
        }
    }
    const xiaomi=new SmartPhone('小米',1999,'黑色','4.7inch')
    xiaomi.call();
    xiaomi.photo();
    xiaomi.playGame();
</script>

1.14.5 子类对父类方法的重写
<script>
    class Phone{
        constructor(brand,price) {
            this.brand=brand;
            this.price=price;

        }
        //父类的成员属性
        call(){
            console.log('我可以打电话')
        }
    }
    class SmartPhone extends Phone{
        constructor(brand,price,color,size) {
            super(brand,price);
            this.color=color;
            this.size=size;
        }
        photo(){
            console.log('拍照');
        }

        playGame(){
            console.log('打游戏');
        }

        //重写！
        call(){
            console.log('我可以进行视频通话')
        }
    }
    const xiaomi=new SmartPhone('小米',1999,'黑色','4.7inch')
    xiaomi.call();
    xiaomi.photo();
    xiaomi.playGame();
</script>


1.14.6 get和set设置
<script>
  class Phone{
      get price(){
          console.log("价格被读取了")
          return 'I LOVE YOU'
      }

      set price(val){
          console.log('价格被修改了')
          return val;
      }
  }

    //实例化对象
    let s = new Phone();
    s.price=12  
    // console.log(s.price)   //其实是调用price方法
</script>

1.15 数值扩展
<script>
   // Number.EPSILON是 JavaScript的最小精度，属性的值接近于 2.22044...E-16
   function equal(a,b){
       if(Math.abs(a-b) < Number.EPSILON){
           return true;
       }else {
           return false;
       }
   }

   console.log(equal(0.1 + 0.2 === 0.3))  //false
   console.log(equal(0.1+0.2,0.3))  //true

   //二进制和八进制
   let b = 0b1010; //2进制
   let o = 0o777;  //8进制
   let d = 100;    //10进制
   let x = 0xff;   //16进制
   console.log(x)   //255

   //检测一个数是否为有限数
   console.log(Number.isFinite(100));  //true
   console.log(Number.isFinite(100/0));  //false
   console.log(Number.isFinite(Infinity));  //false

   //检测一个数值是否为NaN
   console.log(Number.isNaN(123))  //false

   //字符串转整数
   console.log(Number.parseInt('5213123love')); //5213123
   console.log(Number.parseFloat('5.123123神器')); //5.123123

   //判断是否为整数
   console.log(Number.isInteger(5));  //true
   console.log(Number.isInteger(2.5)); //false
   
   //将小数部分抹除
   console.log(Math.trunc(3.45345345345)) //3

   //检测一个数到底是正数、负数、还是0
   console.log(Math.sign(100)) //1
   console.log(Math.sign(0))  //0
   console.log(Math.sign(-123)) //-1
</script>

1.16 对象方法扩展
<script>
    //1.Object.is 判断两个值是否完全相等
    console.log(Object.is(120,120))  //true
	console.log(Object.is(NaN,NaN))  //false

    //2.Object.assign 对象的合并
    const a = {
        name:'ran',
        age:12
    }
    const b = {
        pass:'i love you'
    }
    console.log(Object.assign(a,b))   //{name:'ran',age:'12',pass:'i love you'}

    //3.Object.setPrototypeOf 设置原型对象 Object.getPrototypeof
    const school = {
        name:'尚硅谷'
    }
    const cities = {
        xiaoqu:['北京','上海']
    }
    Object.setPrototypeOf(school,cities)
    console.log(Object.getPrototypeOf(school))  //{xiaoqu: Array(2)}
    console.log(school)  //{name: "尚硅谷"}
</script>


1.17 模块化
1.17.1 基本介绍
介绍

模块化是指将一个大的程序文件,拆分成许多小的文件，然后将小文件组合起来。

模块化的好处：

防止命名冲突
代码复用
高维护性
模块化规范产品

ES6之前的模块化规范有：

CommonJS ====> NodeJS、Browserify
AMD ====> requireJS
CMD ====> seaJS
语法

模块功能主要有两个命令构成：export和inport

export命令用于规定模块的对外接口
inport命令用于输入其他模块提供的功能
export let school = '尚硅谷'
export function teach(){
    console.log('教技能')
}
<script type="module">
    import * as m1 from "./src/js/m1.js";
	console.log(m1);
</script>

1.17.2 暴露语法汇总
统一暴露

//统一暴露
let school = '尚硅谷';
function findjob(){
    console.log('找工作吧');
}
//export {school,findjob}246
默认暴露

//默认暴露
export default {
    school:'ATGUIGU',
    change:function(){
        console.log('我们可以改变你')
    }
}

1.17.3 引入语法汇总
通用导入方式

import * as m1 from "./src/js/m1.js"
import * as m2 from "./src/js/m2.js"
import * as m3 from "./src/js/m3.js"2解构赋值方式

import {school,teach} from "./src/js/m1.js"
import {school as guigu,findJob} from "./src/js/m2.js"
import {default as m3 } from "./src/js/m3.js"2简便形式（只针对默认暴露）

import m3 from "./src/js/m3.js"

1.17.4 模块化方式2
<script src="./src//js/app.js" type=modeule></script>

2. ES7
介绍

Array.prototype.includes：用来检测数组中是否包含某个元素，返回布尔类型值
在ES7中引入指数操作符**，用来实现幂运算，功能与Math.pow结果相同
应用

<script>
    //include
   const mingzhu = ['西游记','红楼梦','水浒传','三国演义']
   console.log(mingzhu.includes('西游记'))  //true
   console.log(mingzhu.includes('金瓶梅'))  //false

    //**
    console.log(2**10) // 1024
</script>

3. ES8
3.1 async函数
介绍

async和await两种语法结合可以让异步代码像同步代码一样

async函数：

async函数的返回值为promise对象
async返回的promise对象的结果值由async函数执行的返回值决定
特性

async function fn(){
   //1.如果返回的是一个非Promise的对象，则fn（）返回的结果就是成功状态的Promise对象，值为返回值
   //2.如果返回的是一个Promise对象，则fn（）返回的结果与内部Promise对象的结果一致
   //3.如果返回的是抛出错误，则fn（）返回的就是失败状态的Promise对象
   return new Promise((resolve,reject)=>{
       resolve('成功的数据');
   });
}
const result = fn();
result.then(value=>{
   console.log(value)  //成功的数据
},reason=>{
   console.log(reason)
})

3.2 await表达式
介绍

await必须放在async函数中
await右侧的表达式一般为promise对象
await可以返回的是右侧promise成功的值
await右侧的promise如果失败了，就会抛出异常，需要通过try…catch捕获处理
特性

<script>
    //创建Promise对象
    const p = new Promise((resolve, reject) => {
        // resolve("成功的值")
        reject("失败了")
    })

    //await 必须放在async函数中
    async function main() {
        try {
            let res = await p;
            console.log(res);
        } catch (e) {
            console.log(e);
        }
    }

    //调用函数
    main()  //失败了
</script>
应用：发送AJAX请求

<script>
    //ajax请求返回一个promise
    function sendAjax(url){
        return new Promise((resolve, reject) => {

            //创建对象
            const x =new XMLHttpRequest();

            //初始化
            x.open('GET',url);

            //发送
            x.send();

            //时间绑定
            x.onreadystatechange = ()=>{
                if(x.readyState === 4 ){
                    if(x.status >= 200 && x.status < 300){
                        //成功
                        resolve(x.response)
                    }else {
                        //失败
                        reject(x.status)
                    }
                }
            }
        })
    }

   //async 与 await 测试
    async function main(){
        let result = await sendAjax("https://api.apiopen.top/getJoke")
        console.log(result);
    }
    main()

</script>

3.3 ES8对象方法扩展
<script>
    const school = {
        name:'尚硅谷',
        cities:['北京','上海','深圳'],
        xueke:['前端','Java','大数据','运维']
    };

    //获取对象所有的键
    console.log(Object.keys(school));

    //获取对象所有的值
    console.log(Object.values(school));

    //entries,用来创建map
    console.log(Object.entries(school));
    console.log(new Map(Object.entries(school)))

    //对象属性的描述对象
    console.log(Object.getOwnPropertyDescriptor(school))
    
    const obj = Object.create(null,{
        name:{
            value:'尚硅谷',
            //属性特性
            writable:true,
            configurable:true,
            enumerable:true,
        }
    })
</script>

4. ES9
4.1 运算扩展符与rest参数
<script>
    function connect({host,port,...user}){
        console.log(host);
        console.log(port);
        console.log(user)
    }
    connect({
        host:'127.0.0.1',
        port:3306,
        username:'root',
        password:'root',
        type:'master'
    })  //127.0.0.1  3306  {username: "root", password: "root", type: "master"}

</script>2468101214<script>
    const AA={
        username:'ran'
    }
    const BB={
        password:'lyyrhf'
    }
    const CC={
        job:'Java'
    }
    const D={...AA,...BB,...CC};
    console.log(D) //{username: "ran", password: "lyyrhf", job: "Java"}
</script>
  
5. ES10
5.1 对象扩展方法
<script>
   //二维数组
   const res = Object.fromEntries([
       ['name','冉海锋'],
       ['cities','成都','武汉']
   ])
   console.log(res) //{name: "冉海锋", cities: "成都"}

   //Map
   const m = new Map();
   m.set('name','ranhaifeng')
   const result = Object.fromEntries(m)
   console.log(result); //{name: "ranhaifeng"}
</script>

5.2 字符串扩展方法
<script>
   //trim
   let str= ' asd  '
   console.log(str) //asd
   console.log(str.trimStart()) //asd  清空头空格
   console.log(str.trimEnd()) //  asd  清空尾空格
</script>

5.3 flat与flatMap
<script>
    const arr = [1,2,3,[4,5,6,[7,8,9]]]
    //参数为深度，是一个数字
    console.log(arr.flat(2)) //[1,2,3,4,5,6,7,8,9]

	const arr2=[1,2,3,4]
    const result = arr2.flatmap(item => [item * 10]); //如果map的结果是一个多维数组可以进行flat 是两个操作的结合
	
</script>

5.4 Symbol的description
介绍

用来获取Symbol的字符串描述

实例

let s = Symbol('尚硅谷');
console.log(s.description) //尚硅谷2

5.5 私有属性
<script>
    class Person {
        //公有属性
        name;
        //私有属性
        #age;
        #weight;

        //构造方法
        constructor(name, age, weight) {
            this.name = name;
            this.#age = age;
            this.#weight = weight;
        }
        intro(){
            console.log(this.name);
            console.log(this.#age);
            console.log(this.#weight);
        }
    }

    //实例化
    const girl = new Person('冉', 18, '45kg');
    console.log(girl.#age) //error
    console.log(girl); //Person{name: "冉", #age: 18, #weight: "45kg"}
    girl.intro(); // 冉 18  45kg
</script>

5.6 Promise
<script>
    //声明两个promise对象
    const p1 = new Promise((resolve, reject) => {
        setTimeout(()=>{
            resolve('商品数据-1')
        },1000)
    })

    const p2 = new Promise((resolve, reject) => {
        setTimeout(()=>{
            reject('出错了！')
        },1000)
    })

    //调用allsettled方法:返回的结果始终是一个成功的，并且异步任务的结果和状态都存在
    const res = Promise.allSettled([p1,p2]);
    console.log(res)

    // Promise {<pending>}
    //     __proto__: Promise
    //     [[PromiseState]]: "fulfilled"
    //     [[PromiseResult]]: Array(2)

    //调用all方法：返回的结果是按照p1、p2的状态来的，如果都成功，则成功，如果一个失败，则失败，失败的结果是失败的Promise的结果
    const result = Promise.all([p1,p2])
    console.log(result)

</script>

5.7 可选链操作符
//相当于一个判断符，如果前面的有，就进入下一层级
function main(config){
    const dbHost = config?.db?.host
    console.log(dbHost) //192.168.1.100
}

main({
    db:{
        host:'192.168.1.100',
        username:'root'
    },
    cache：{
    	host:'192.168.1.200',
    	username:'admin'
	}
})

5.8 动态import
btn.onclick = function(){
    //使用之前并未引入，动态引入，返回的其实是一个Promise对象
    import('./hello.js').then(module=>{
        module.hello();
    })
}

5.9 BigInt类型
//大整型
let n = 521n;
console.log(n,typeof(n))  // 521n  n 

//函数
let n = 123;
console.log(BigInt(n)) // 123n  //不要使用浮点型，只能用int

//大数值运算
let max = Number.MAX_SAFE_INTEGER; // 9007199254740991
console.log(max +1) // 9007199254740992
console.log(max +2) // 9007199254740992 出问题了
console.log(BigInt(max)+BigInt(1)) 9007199254740992n
console.log(BigInt(max)+BigInt(2)) 9007199254740993n
  
5.10 绝对全局对象globalThis
console.log(globalThis) //window  //适用于复杂环境下直接操作window
