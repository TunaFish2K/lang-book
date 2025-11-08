## 函数
### 基本格式
```
// 在不返回值时`: void`可以省略
fun <name>[generic_signature](<signature>): return_type [throws] {
    <content>
}
fun(signature): return_type [throws] {
    <content>
}
const var0 = (signature): return_type => [throws] {
    <content>
};
const var1 = (signature) => <expression>; // 自动类型推导与错误推导 
```
#### `<signature>`:  
由多个参数组成，以逗号分隔。  
参数类型：
- 必须参数：`<param_name>: <param_type>`  
- 可选参数
  - `<param_name>?: <param_type>`
    - 不传入时为`null`
  - `<param_name>: <param_type>=<default_value>`
- 剩余参数
  - `...<param_name>: <params_type>[]`

可选参数出现后不能再出现必须参数；剩余参数后不能有其他参数。
#### `<return_type>`: 
正常的类型。
#### `<throws>`:
所有可能抛出的异常。会传染到调用者，要求调用者指定throws或用catch处理。不会抛出时省略。

### 函数作为值
上述的函数定义式都可以作为表达式使用。  
所有直接定义的函数都是存有函数的常量。
```
fun execute(fun: () => void): void {
    fun();
}

fun a(): void {
    console.log("Im a.");
}

const b: () => void;
b = a;

execute(b);
```
#### 对函数的类型描述
`(<signature>) => <return_type>`
```
fun make_adder(x: i32): (y: i32) => i32 {
    return (y: i32) => x + y;
}
```
##### 签名匹配
- 传入函数参数和类型描述匹配的，可以传入。
- 传入函数参数少于要求，但是已有部分和类型描述匹配的，可以传入  。
- 类型描述返回`void`,传入函数的返回类型不做限制。

### `generic_signature`
详见[GENERIC.md](./GENERIC.md)