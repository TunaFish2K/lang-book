## 接口
接口描述了一个对象应实现的方法与字段，也可以为变量提供初始值，函数提供默认实现。
```
interface <name>[<generic_signature>] {
    let <var_name>: <type>;
    let <var_name>: <type> = <value>;
    fun <name>(<signature>): <return_type>;
    fun <name>(<signature>): <return_type> {
        <content>
    };
}
```
使用如下语法实现接口:
 ```
class <name> : <interface_0>[,<interface_1>...] {
    <content>
}
```
实现接口时必须实现所有非默认方法并初始化所有未初始化值。 
### 实现中的省略
定义延后初始化的接口定义字段可以省略类型标注。
可以省略接口定义与函数返回值。
```
interface A {
    let field_0: string;
    fun to_string(): string;
} 
class B : A {
    let field_0;
    fun to_string() {
        return `B, field_0='${field_0}'`;
    }
}
```
### 常量退化
允许继承时变量由`const`退化到`let`。
```
interface A {
    const name: string;
}
class B : A {
    let name: string;
}
```

### 函数接口
```
interface B[<generic_signature>](<signature>): <return_type>;
```
可以视作函数类型描述的别名。

### `<generic_signature>`
详见[GENERIC.md](./GENERIC.md)
