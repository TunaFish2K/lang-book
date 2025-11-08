## 控制流
### `<condition>`
一个返回`boolean`数值的表达式。
### 条件
#### if语句
`else if`与`else`均可以省略
```
if (<condition>) {
    <content>
}
else if (<condition>) {
    <content>
}
else {
    <content>
}
```
### match-case
`case`结束后不会立刻跳出match。
```
match (<expression>) {
    case (<value_0>) {
        <content>
    }
    case (<value_1>) {
        <content>
    }
    default {

    }
}
```
### 循环
在循环结构内都可以用`break;`语句跳出循环。  
用`continue;` 跳过本次循环。
#### while
```
while (<condition>) {
    <content>
}
```
#### for
```
for (<init>; <condition>; <after_loop>) {
    <content>
}
```
##### `<init>`
一个语句，在循环开始前被调用。
##### `<condition>`
不符合时循环终止。
##### `<after_loop>`
一个语句。每次循环结束时会被调用。

例子：
```
for (let i = 0; i < 10; i++) {
    console.log(i);
}
```
#### for-of
对可迭代对象进行迭代。
```
for (const <var_name> of <iterable_object>) {
    <content>
}
```
##### `<iterable_object>`
实现了`Iterable`接口的对象。
##### Iterable接口
```
class IterationEnd : Error {}
interface Iterator<T> {
    next(): T throws IterationEnd;
}
interface Iterable<T> {
    fun iterate(): Iterator<T>;
}
```

### return
在无返回值函数中，使用`return;`结束函数。  
在有返回值函数中，使用`return <value>;`返回值并结束函数。  
不可以有没有正确类型返回值的分支。

### throw
立刻停止执行这个函数/类初始化，向上传递这个错误直到被接收。
```
throw <error>;
```
#### `<error>`
实现Error接口的类型的对象。详见[ERROR.md](./ERROR.md)