## 错误处理
```
try {
    <content>
}
catch (e: <error_type>) {

}
// 此处可以有任意多个catch
finally {

}
```
### `<error_type>`
实现`Error`接口的类型的实例。
### `Error`接口
`Error`是对错误的约定，`ErrorWithMessage`是简单情况下可采用的错误接口。
```
interface Error {}
interface ErrorWithMessage : Error {
    message: string;
    init(message?: string) {
        this.message = message;
    }
}
```
在`try`中报错后，会被`catch`语句依次匹配。  
没有匹配时，若有`finally`，先执行它；然后继续向上抛出。  
无论如何，`try`和`catch`执行完毕后，会执行`finally`。
`finally`中报错且有没有捕获的错误时，优先抛出`finally`的错误。