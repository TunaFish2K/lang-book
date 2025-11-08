## 泛型
### `generic_signature`
由多个泛型参数组成，以逗号分隔。  
参数格式：
- `<name>`
  - 没有接口约束的泛型。
- `<name>: <interface>[, <interface_2>...]`
  - 传入的类型必须实现了所要求的接口。

然后，可以在函数签名，返回值，函数体和类型体内内使用这一类型。
```
class Box<T> {
    value?: T;
    init(value?: T) {
        this.value = value;
    }
}

fun main() {
    const n = new Box<u32>(0);
    const n_1: Box<u32>;
}
```
### 自身类型
以`This`作为类型的时候，其会始终表示所在的位置所属的接口/类。
### 实例
```
interface Addable {
    add(y: This): This;
}
class Coffee : Addable {
    content: u32;

    init(content: u32 = 0) {
        this.content = content;
    }

    fun add(y: Coffee) {
        const result = new Coffee(content + y.content);
        return result;
    }
}
```