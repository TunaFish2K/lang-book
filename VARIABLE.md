## 变量
### 定义格式
```
// 不可变
const <var_name>[?]: <type> = <value>;
const <var_name>[?] = <value>; // 自动推导
const <var_name>[?]: <type>; // 延后初始化

// 可变
let <var_name>[?]: <type> = <value>;
let <var_name>[?] = <value>;
let <var_name>[?]: <type>;
```

### 基础部分
```
const text: string = "text content"; // 定义常量
text = "new content"; // 常量 报错
const text_1: string; // 允许后续初始化
text_1 = "text 1 content"; // 初始化
text_1 = "new content"; // 常量 报错

const text_2 = "text 2 content"; // 直接赋值可以自动推导类型

let text_3 = "mutable content"; // 相较于常量，可以重新赋值
text_3 = "new content";
```
### 可空变量
> [!IMPORTANT]  
> 可空变量，指值可以为指定类型或`null`的变量。  
> 与未初始化是不同的概念。  
> 读取未初始化的值是不合法的。
```
let var_0?: i32;
var_0 = 1;
var_0 = null; // 可行

const constant_0?: i32; // 未初始化
console.log(constant_0); // 错误!
constant_0 = null; // 初始化，值是`null`
console.log(constant_0); // 没有问题
```
### 变量遮蔽
```
const num: string = "0"; 
const num: i32 = parse_int(num); // 可以重新定义同名异类常量遮蔽原先常量
let num: string = "oops"; // let不可以遮蔽const

let num_0: string = "0";
const num_0: i32 = parse_int(num_0); // 反之可以
```
