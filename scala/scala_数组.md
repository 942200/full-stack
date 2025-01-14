# 第四章 数组

## 定长数组

如果需要一个长度不变的数组，可以使用scala中的 `Array` 。

```scala
val z:Array[String] = new Array[String](3)
or
val z = new Array[String](3)
or
var z = Array("a","b","c")
```

## 变长数组

变长数组使用 `ArrayBuffer` ，在数组缓存的尾端添加或者移除元素是一个高效的操作。

使用 `toArray` 将数组缓存转为数组，使用 `toBuffer` 将数组转成缓存。

## 遍历数组和数组缓存

使用 `for` 循环遍历数组或者缓存：

```scala
for( i <- 0 until a.length)
println(i)
```

如果想每两个元素一跳，可以这样遍历：

```scala
0 until (a.length,2)
```

如果想从数组的尾端开始，遍历写法为:

```scala
(0 until a.length).reverse
```

## 数组转换

从一个数组出发，以某种方式对它进行转换，这些转换操作不会修改原数组，而是产生一个新的数组。

```scala
val a = Array(1,2,3,4)
val result = for(elem <- a) yield 2*elem
```

结果返回一个类型与原始集合相同的新集合。

我们也可以给转换增加过滤条件：

```scala
for(elem <- a if elem % 2 == 0） yield 2 * elem
```

注意原始集合并没有受到影响。

另一种做法是：

```scala
a.filter(_ % 2 == 0).map(2 * _)
```

甚至：

```scala
a.filter{ _ % 2 == 0 } map {2 * _}
```

> _ 表示值的形式只能用于当前只有一个表达式的时候

## 常用算法

**求和**

```scala
Array(1,2,3).sum
```

**最小值和最大值**

```scala
Array(1,2,3).min
Array(1,2,3).max
```

**排序**

```scala
Array(5,2,1,4).sortWith(_ < _)
```

**显示数组内容**

```scala
a.mkString
a.mkString(" and ")
a.mkString("<",",",">")
```

## 多维数组

```scala
import Array._

object Demo {

        def main(args: Array[String]) {
                var myMatrix = ofDim[Int](3,3)

                // build a matrix
                for (i <- 0 to 2) {
                        for ( j <- 0 to 2) {
                                myMatrix(i)(j) = j;
                        }
                }

                // Print two dimensional array
                for (i <- 0 to 2) {
                        for ( j <- 0 to 2) {
                                print(" " + myMatrix(i)(j));
                        }
                        println();
                }
        }
}
```