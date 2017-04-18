#### TypeScript编译器安装
```angular2html
sudo npm install typescript -g

```

#### TypeScript语法新特性
+ 多行字符串
```angular2html
var name = "ren\nping\njun";
```
+ 字符串模板
```angular2html
var name = "ren\nping\njun";
console.log(`Hello ${name}`);
```
+ 自动拆分字符串
```angular2html
function test(tpl,name,age){
    console.log(tpl);
    console.log(name);
    console.log(age);
}
var myname = `ren
ping
jun`;
var getMyAge = function () {
    return 25;
};
test`Hello, my name is ${myname},I'm ${getMyAge()} years old`;
```

#### TypeScript参数新特性
- 参数类型：在参数名称后面使用冒号来指定参数类型
```angular2html
var name: string = 'renpingjun';
name = 25 //错误的参数类型
```
###### Options
1.TypeScript本身具有类型推断机制，会在第一次给变量赋值时赋予其类型;
2.TypeScript数据有五种类型：number、string、any、void、boolean;
- 默认参数：在参数声明后面用等号来指定参数的默认值
```angular2html
function doSomething(param1,param2,param3=morning){
    console.log(`${param1},${param2} and ${param3}`);
}
doSomething('hello','good');
```
- 可选参数：在方法的参数声明后面用？来表示此参数为可选参数
```angular2html
function doSomething(param1:string,param2?:string,param3:string = morning){
    console.log(`${param1},${param2} and ${param3}`);
}
doSomething('hello');
```

#### TypeScript函数新特性
+ Rest and Spread操作符（用来声明任意数量的函数参数）
```angular2html
function work(...args){
    args.forEach(function (arg) {
        console.log(arg);
    })
}
work(2,3,4,5,6)
```
+ generator函数（控制函数的执行过程，手动暂停和恢复代码执行）
```angular2html
function* goWork(){
    console.log('start');
    yield ;
    console.log('end');
}
var func1 = goWork();
func1.next();
func1.next();
```
+ destructuring析构表达式（通过表达式将对象或数组拆解成任意数量的变量）
```angular2html
//example1 object
function getStock(){
    return {
        code:'IBM',
        price:100
    }
}
var {code:codeName,price} = getStock();
console.log(`${codeName} && ${price}`);
//example2 array
var arr1 = [1,2,3,4,5,6];
var [,,num1,num2,...others] = arr1;
console.log(`${num1} && ${num2} && ${others}`);// 3 && 4 &&  1 2 5 6
```
+ 箭头表达式（用来声明匿名函数，消除传统匿名函数的this指针问题）
```angular2html
var arrayN = [1,2,3,4,5];
console.log(arrayN.filter(value=>value%2==0));
```
#### 面向对象TypeScript
##### 类
- 类的访问控制符
public（默认为public）：可以在类的外部被引用
private：私有的，只能在类的内部被引用
protected：受保护的，不能在类的外部被引用
- 类的构造函数

类被实例化的时候被调用，且只被调用一次 constructor(){}

- 类的继承
关键字：extends  eg：class employee extends person{}
关键字：super 用来调父类的构造函数或其他方法
```angular2html
class Person {
    constructor(public name: string){
    }
    fork=()=>console.log('fork latter')
}
class Employee extends Person {
    constructor(name:string){
        super(name);
    }
    work=()=>console.log('working……')
}
var e1 = new Employee('rpj');
console.log(`${e1.name} is ${e1.work()} `);
```
##### 泛型（generic）
参数化的类型，一般用来限制集合的内容
##### 接口（interface）
用来建立某种代码约定，使得其他开发者在调用某个方法或创建新的类时必须遵循接口所定义的代码约定
```angular2html
interface IPerson {
    name:string,
    age:number
}
class People {
    constructor(public config: IPerson){
    }
}
var p1 = new People({
    name:'ganrenping',
    age:25
});
```
##### 模块(Module)
帮助开发者将代码分割为可重用的单元

export 公开,对外暴露，别的模块可以引用;
import 引用模块
##### 注解（annotation）
为程序的变量、方法、类加上更为直观明了的说明
##### 类型定义文件（*.d.ts）
类型定义文件用来帮助开发者在TypeScript中使用已有的javascript的工具包，如jquery

来源：github repo DefinitelyTyped 可用工具下载[typings] <https://github.com/typings/typings>
