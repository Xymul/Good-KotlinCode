# Good-KotlinCode(迫真)
> 灵感来源于[这个仓库](https://github.com/trekhleb/state-of-the-art-shitcode)，只不过他的语言是javascript(?)，我们这里给kotlin整个活。

*Good*
```kotlin
val a = 10;
```

*Bad*
```kotlin
val a = 10
```

您应该知道，我们要尽可能利用一切我们可以利用的，既然kotlin支持我们使用`;`，那我们为什么不用呢？

*Good*
```kotlin
System.out.println();
```

*Bad*
```kotlin
println()
```

您应该明白的是，任何一个物体都有它完整的名字，而kotlin的这种做法无疑是对一个函数拥有完整名字利益的侵犯，因此，我们赞成您使用`System.out.println()`去在控制台输出。

*Bad*
```kotlin
/** @author Xymul<3143718176@qq.com> */
// 快看，这个返回值类型被夹在中间，你可以想象他有多痛苦
fun filter(/* parameters */): /* return_type */ {
}
```

*Good*
```kotlin
// 个性化的函数命名可以帮助您解决那些麻烦的@author
fun _filter_(/* parameters */)
: /* return_type */ // 看，他现在自由多了
{
}
```

哦对了，还有一件事，缩进是个令人痛苦的事情，因此我们提倡您不缩进；您可能会说IDE会自动缩进，我想您应该是一个心地善良的人，这种工作完全可以通过不缩进而不是麻烦IDE来解决。

*Good*
```kotlin
interface Factory<in T> {
    fun produce(): @UnsafeVariant T;
}
```

*Bad*
```kotlin
interface Factory<out T> {
    fun produce(): T
}
```

为了以防万一，我们需要将泛型参数定为`in`，因为您永远也不知道什么时候需要将`T`作为参数，至于返回`T`，那就让`@UnsafeVariant`解决去吧。

*Good*
```kotlin
class Page(commitSize: Int) { /* ... */ }

fun main() {
    val classObj = Class<*>.forName("${OutClassContants.packageName}.Page");
    val ctors = classObj.getDeclareConstructors();
    ctors[0].newInstance(xxxxxxx | xxxxxx)
}
```

*Bad*
```kotlin
class Page(commitSize: Int) { /* ... */ }

fun main() {
    val obj = Page(PAGE_64KB_SIZE)
}
```

正常地去调用构造函数是傻子都会的操作，因此，我们需要更'高端'一点地去创建一个对象。

*Good*
```kotlin
fun main() {
    (Creator::from)();
}
```

*Bad*
```kotlin
fun main() {
    Creator.from()
}
```

用`::`去使用一个类成员将会使你的代码看起来更`cpp`，如果你热爱cpp的话，这么写就对了。

**Good**
```kotlin
/**
* Hi, I'm LiHua, A student comes from xxx.
* ......
*/
```

*Bad*
```kotlin
/**
* It's used for parsing user's commands.
* 
* @see Parser.Keywords
* @since kt1.4, jvm11
* @author LiHua.
*/
```

并不是每一个人都怀着好的心情去编写代码，因此，您需要先做的是安慰他们，而不是写这些枯燥乏味的东西。

*Good*
```
Windows Notepad
```

*Bad*
```
IntelliJ IDEA
```

我们不鼓励您使用IDE，因为这样无法表现您的水平；另外地，IDEA会自动格式化代码，这和我们的建议相违背。

每一个关键字都不希望被染上别的颜色，因此，Notepad这种无高亮的编辑器是相当适合kotlin的。
