## 类型
用于定义复合数据结构和相关方法。
```
class <name>[generic_signature] [: <interface_0>[, <interface_1>...]] {
   // 如VARIABLE.md所述以定义变量方式定义字段
   const <var_name>: <var_type>;
   // 名称为`init`的函数被作为构造函数
   fun init(<signature>) {

   }
   // 如FUNCTION.md所述定义方法
}
```
### 实例化
```
class A {
   fun init() {
      console.log("created!");
   }
}
fun main() {
    const a = new A();
}
```
### `this`
类型内的方法可以直接访问到类型的字段和方法，也可以通过`this`访问到对象本体：
```
class A {
   let text = "Hello";

   fun say() {
      console.log(text);
   }

   fun set(text: string) {
      // 显式使用this
      this.text = text;
   }

   fun set_and_say(text: string) {
      this.set(text);
      say();
   }
}
```

### 私有字段
名称以`@`开头的字段只能被对象自己访问。
内部通过`this.@<name>`和直接访问`@<name>`都是可行的。
```
class A {
   let @text = “Hello";
   fun set_text(val: string) {
      @text = val;
   }
   fun get_text(): string {
      return @text;
   }
}

fun main() {
   const a = new A();
   console.log(a.@text); // 错误
}
```
### 单例
将`class`替换为`object`将直接创建类的唯一实例而不是类。  
```
class User {
   name: string;
   id: u32;
   is_admin = false;
}

object UserBuilder {
   fun create_normal_user(name: string, id: u32): User {
      const user = new User();
      user.name = name;
      user.id = id;
      return user;
   }

   fun create_admin(name: string, id: u32): User {
      const user = create_normal_user(name, id);
      user.is_admin = true;
      return user;
   }
}

fun main() {
   const normal_user_0 = UserBuilder.create_normal_user("Tom", 1);
   const admin_user_0 = UserBuilder.create_admin("Alice", 2);
}
```
### 无继承
不支持对象的继承。复用请使用接口。

### `<generic_signature>`
详见[GENERIC.md](./GENERIC.md)