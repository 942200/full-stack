# 第十六章 注解

## 什么是注解

注解是那些你插入到代码中以便有工具可以对它们进行处理的标签。

注解的语法和Java一样，可以对scala类使用Java注解，也可以使用Scala注解，scala注解是scala独有的。Java注解不影响编译器如何将源码编译成字节码，而Scala可以影响到编译过程。

## 什么可以被注解

在scala中，你可以为类、方法、字段、局部变量和参数添加注解，和Java一样。

```scala
@Entity class Credentials
@Test def test(){}
@BeanProperty var username = _
def doSomething(@NotNull message:String){}
```

也可以同时添加多个注解，先后次序没有影响。

```scala
@BeanProperty @Id var username = _
```

在给主构造器添加注解的时候，需要将注解放置在构造器之前，并加上一对圆括号（如果注解不带参数的话）

```
class Credential @inject() (var username:String, var password:String)
```

还可以为表达式添加注解，需要在表达式后面添加冒号，然后注解本身。

也可以为类型参数添加注解：

```scala
class MyContainer[@specialized T]
```

针对实际类型的注解应该放在类型名称之后：

```scala
String @cps[Unit]
```

## 注解参数

Java注解可以有带名参数：

```scala
@Test(timeout=100, expected=classOf[IOException])
```

如果参数名为 `Value` ，则参数名可以直接省略。如果注解不带参数，则圆括号可以省去。

```scala
@Named("credt") var credentials:Credentials = _
```

大多数注解参数都有缺省值。

Java注解的参数类型只能为：

- 数值型字面量
- 字符串
- 类字面量
- Java枚举
- 其他注解

scala注解可以是任何类型。

## 注解实现

注解必须扩展 `Annotation` 特质。

## 针对Java的注解

## Java修饰符