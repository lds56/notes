

[TOC]
### Scala

- Tips
	- 如果没有发现任何显式的返回语句,Scala 方法将返回方法中最后一个计 算得到的值。
	- 类和它的伴生对象(Companion class)可以互相访问其私有成员。
	- 单例对象(Singleton Object)会在第一次被访问的时候初始化。
	- 如果没有对特 定的 while 或 do 循环较好的决断,请尝试找到不用它们也能做同样事情的方式。
	- 因此通常最好还是 避免从 finally 子句中返回值。
	- 在它们最后一个动作调用自己的 函数,被称为尾递归:tail recursive。
	- Scala 里定义不带参数也没有副作用的方法为无参数方法,也就是说,省略空的括号, 是鼓励的风格。另一方面,永远不要定义没有括号的带副作用的方法,因为那样的话方法调用看 上去会像选择一个字段。
	- 你可以改 变类 ArrayElement 中 contents 的实现,从一个方法变为一个字段,而无需修改类 Element 中 contents 的抽象方法定义。
	- Scala把字段和方法放进同一个命名空间的理由很清楚,因为这样你就可以使用val重载无参数的方法,这种你在Java里做不到的事情。
	- ++操作符串连两个数组。
	- 第一点,特质不能有任何“类”参数,也就是说,传递给类的 主构造器的参数。
	- 类和特质的另一个差别在于不论在类的哪个角落,super 调用都是静态绑定的,在特质中,它们 是动态绑定的。
	- 粗略地说,越靠近右侧的特质越先起 作用。
- List
```
	 //::: concat 
	 val oneTwoThreeFour = oneTwo ::: threeFour
```
```
	//:: [cons] append at the front of list
	 val oneTwoThree = 1 :: twoThree
```
l.head
l.tail
l.last: The list's last element
l.init: A list consisting of all elements of l except the last one
l take n: A list consisting of the first n elements of l
l drop n: the rest of the collection after taking n
l(n) or l apply n: the nth element of l
xs ++ ys: concat
xs.reverse
xs.update(n, x)
xs indexOf x
xs contains x

- Tuple
	
```
val pair = (99, "Luftballons")
println(pair._1)
println(pair._2)
```

- Set
```
var jetSet = Set("Boeing", "Airbus")
jetSet += "Lear"
```

- Map
```
import scala.collection.mutable.Map
val treasureMap = Map[Int, String]()
treasureMap += (1 -> "Go to island.")
treasureMap += (2 -> "Find big X on ground.")
treasureMap += (3 -> "Dig.")
```

- Read from file
```
import scala.io.Source
val lines = Source.fromFile(args(0)).getLines.toList
if (args.length > 0) {
  for (line <- lines)
    print(line.length + " " + line)
}
else
Console.err.println("Please enter filename")
```

- Class 
```
class ChecksumAccumulator {
  private var sum = 0
}
```

- Print
```
println("""|Welcome to Ultamix 3000.
           |Type "HELP" for help.""".stripMargin)
OUTPUT: 
Welcome to Ultamix 3000.
Type "HELP" for help.
```

- Unary
```
PREFIX: Only + - ! ~
(2.0).unary_-
```

- Require
```
class Rational(n: Int, d: Int) {
  require(d != 0)
  override def toString = n +"/"+ d
}
```

- Override
```
override def toString = n +"/"+ d
```

- Auxiliary Constructor
```
  def this(n: Int) = this(n, 1)
```
- Implicit conversion
```
implicit def intToRational(x: Int) = new Rational(x)
```

- Functional If
```
val a = if (!args.isEmpty) args(0) else "default.txt"
```

- For
```
for (file <- filesHere)
	  println(file)
for (i <- 1 to 4)  
      println("Iteration " + i)
for (i <- 1 until 4)  //exclude upperbound
	  println("Iteration " + i)
```
- Filter 
```
for (
  file <- filesHere
  if file.isFile;
  if file.getName.endsWith(".scala")
) println(file)
```

- Nested Enumation
```
  for {
    file <- filesHere
    if file.getName.endsWith(".scala")
    line <- fileLines(file)
    if line.trim.matches(pattern)
  } println(file + ": " + line.trim)
```

- For-Yield
```
def scalaFiles =
  for {
   file <- filesHere
   if file.getName.endsWith(".scala")
  } yield file
```

- Try-Catch
```
try {
  val f = new FileReader("input.txt")
  // Use and close file
} catch {
  case ex: FileNotFoundException => // Handle missing file
  case ex: IOException => // Handle other I/O error
}
```

- Match
```
val friend =
￼￼firstArg match {
  case "salt" => "pepper"
  case "chips" => "salsa"
  case "eggs" => "bacon"
  case _ => "huh?"
}
```
- Collection Function
```
someNumbers.foreach((x: Int) => println(x))
someNumbers.filter((x: Int) => x > 0)
someNumbers.filter(_ > 0)
```

-  _
```
val f = (_: Int) + (_: Int)
val b = sum(1, _: Int, 3) // partially applied function
```

- Duplicate Parameters
```
def echo(args: String*) =
         for (arg <- args) println(arg)
```

- Curry
```
def curriedSum(x: Int)(y: Int) = x + y
```

- By-name Parameter
```
def byNameAssert(predicate: => Boolean) =
  if (assertionsEnabled && !predicate)
￼throw new AssertionError
```

- Abstract Class
```
abstract class Element {
def contents: Array[String]
}
```

- Inheritance
```
class ArrayElement(conts: Array[String]) extends Element {
  def contents: Array[String] = conts
￼}
```

- Trait
```
class Animal
class Frog extends Animal with Philosophical {
  override def toString = "green"
}
```