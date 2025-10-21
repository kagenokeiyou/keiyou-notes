# Python

Python，是一种广泛使用的解释型编程语言，支持多种编程范型，包括过程式、面向对象和函数式编程。它拥有动态类型系统和垃圾回收功能，能够自动管理内存使用，并且其本身拥有一个巨大而广泛的标准库。

Guido van Rossum 在 20 世纪 80 年代后期开始开发 Python，于 1991 年首次发布 Python 0.9.0。在1994年1月，Python版本1.0发布。Python 2.0 于 2000 年 10 月 16 日发布，Python 3.0 于 2008 年 12 月 3 日发布，是一次重大修订，与早期版本不完全向后兼容， Python 2 于 2020 年停止维护。

## 安装

### Windows

现在推荐在 Windows 上使用 Python 安装管理器（Python install manager）

从 [Microsoft Store](https://apps.microsoft.com/detail/9nq7512cxl7t) 或 [python.org/downloads](https://www.python.org/downloads/) 获取

**参考文献** <https://docs.python.org/zh-cn/3.14/using/windows.html>

这是一个独立的工具，它使 Python 可以作为 Windows 机器上的全局命令使用，与系统集成，并支持随时间更新，推荐为每个项目创建一个虚拟环境来使用。

## Hello World

```python
print("Hello World!")
```

## 注释

```python
# 单行注释

"""
多行注释 单双引号均可
"""
```

## 变量

Python 是动态类型语言，变量不需要声明类型，变量的值和类型可以改变。

```python
a = 114514
a = 'Ciallo'
a = True
```

## 常量

Python 不支持常量，约定俗成写法是使用全大写变量名来代表常量。

```python
PI = 3.1415926535
```

## 数据类型

整数 `int`  
浮点数 `float`  
布尔 `bool`  
字符串 `str`  
列表 `list`  
元组 `tuple`  
字典 `dict`  
对象 `object`  
空值 `None`  

## 运算符与优先级

**参考文献** <https://docs.python.org/zh-cn/3.14/reference/expressions.html#operator-precedence>

| 运算符                                                           | 描述                                                 |
| ---------------------------------------------------------------- | ---------------------------------------------------- |
| `(expr...)`, `[expr...]`, `{key: value...}`, `{expr...}`         | 绑定或加圆括号的表达式，列表显示，字典显示，集合显示 |
| `x[index]`, `x[index:index]`, `x(args...)`, `x.attr`             | 抽取，切片，调用，属性引用                           |
| `await x`                                                        | await 表达式                                         |
| `**`                                                             | 乘方                                                 |
| `+x`, `-x`, `~x`                                                 | 正，负，按位非 NOT                                   |
| `*`, `@`, `/`, `//`, `%`                                         | 乘，矩阵乘，除，整除，取余                           |
| `+`, `-`                                                         | 加和减                                               |
| `<<`, `>>`                                                       | 移位                                                 |
| `&`                                                              | 按位与 AND                                           |
| `^`                                                              | 按位异或 XOR                                         |
| `\|`                                                             | 按位或 OR                                            |
| `in`, `not in`, `is`, `is not`, `<`, `<=`, `>`, `>=`, `!=`, `==` | 比较运算，包括成员检测和标识号检测                   |
| `not x`                                                          | 布尔逻辑非 NOT                                       |
| `and`                                                            | 布尔逻辑与 AND                                       |
| `or`                                                             | 布尔逻辑或 OR                                        |
| `if ... ... else ...`                                            | 条件表达式                                           |
| `lambda`                                                         | lambda 表达式                                        |
| `:=`                                                             | 赋值表达式                                           |

### 赋值表达式（海象运算符）

**Python 3.8 新增** <https://docs.python.org/zh-cn/3.14/whatsnew/3.8.html#assignment-expressions>

`:=` 可在表达式内部为变量赋值。它被昵称为“海象运算符”因为它很像是 海象的眼睛和长牙。

```python
if (n := len(a)) > 10:
    print(f"List is too long ({n} elements, expected <= 10)")
```

```python
discount = 0.0
if (mo := re.search(r'(\d+)% discount', advertisement)):
    discount = float(mo.group(1)) / 100.0
```

```python
while (block := f.read(256)) != '':
    process(block)
```

```python
[clean_name.title() for name in names
 if (clean_name := normalize('NFC', name)) in allowed_names]
```

## 基本输入输出

以下为 `print()` 与 `input()` 的函数签名

```python
print(*objects, sep=' ', end='\n', file=None, flush=False)
input(prompt, /)
```

## 流程控制

```python
if x < 0:
    x = 0
    print('Negative changed to zero')
elif x == 0:
    print('Zero')
elif x == 1:
    print('Single')
else:
    print('More')
```

```python
a, b = 0, 1
while a < 10:
    print(a)
    a, b = b, a+b
```

```python
for i in [1, 2, 3]:
    print(i)

for i in range(5):
    print(i)
```

`range()` 返回一个可迭代对象，签名如下

```python
class range(start, stop, step=1, /)
```

`range()` 为左闭右开，若 start 未指定，则默认为 0

```python
print(list(range(5))) # [0, 1, 2, 3, 4]
```

### break 与 continue

`break` 语句将跳出最近的一层 `for` 或 `while` 循环

`continue` 语句将继续执行循环的下一次迭代

```python
for n in range(2, 10):
    for x in range(2, n):
        if n % x == 0:
            print(f"{n} equals {x} * {n//x}")
            break

for num in range(2, 10):
    if num % 2 == 0:
        print(f"Found an even number {num}")
        continue
    print(f"Found an odd number {num}")
```

### 循环的 else 子句

 `for` 循环中，`else` 子句会在循环结束其他最后一次迭代之后，即未执行 `break` 的情况下被执行。

在 `while` 循环中，它会在循环条件变为假值后执行。

在这两类循环中，当在循环被 `break` 终结时 `else` 子句 不会 被执行。 当然，其他提前结束循环的方式，如 `return` 或是引发异常，也会跳过 `else` 子句的执行。

```python
for n in range(2, 10):
    for x in range(2, n):
        if n % x == 0:
            print(n, 'equals', x, '*', n//x)
            break
    else:
        # 循环到底未找到一个因数
        print(n, 'is a prime number')
```

### match 模式匹配

**python 3.10 新增** <https://docs.python.org/zh-cn/3.14/tutorial/controlflow.html#match-statements>

`match` 语句接受一个表达式并把它的值与一个或多个 `case` 块给出的一系列模式进行比较，只有第一个匹配的模式会被执行，并且它还可以提取值的组成部分（序列的元素或对象的属性）赋给变量。如果没有匹配的case，则不执行任何分支。

```python
def http_error(status):
    match status:
        case 400:
            return "Bad request"
        case 404:
            return "Not found"
        case 418:
            return "I'm a teapot"
        case _:
            return "Something's wrong with the internet"
```

`_` 作为通配符必定会匹配成功。

可以用 `|` 将多个字面值组合到一个模式中

```python
case 401 | 403 | 404:
    return "Not allowed"
```

解包赋值

```python
# point 是一个 (x, y) 元组
match point:
    case (0, 0):
        print("Origin")
    case (0, y):
        print(f"Y={y}")
    case (x, 0):
        print(f"X={x}")
    case (x, y):
        print(f"X={x}, Y={y}")
    case _:
        raise ValueError("Not a point")
```

```python
class Point:
    def __init__(self, x, y):
        self.x = x
        self.y = y

def where_is(point):
    match point:
        case Point(x=0, y=0):
            print("Origin")
        case Point(x=0, y=y):
            print(f"Y={y}")
        case Point(x=x, y=0):
            print(f"X={x}")
        case Point():
            print("Somewhere else")
        case _:
            print("Not a point")
```

自定义类可通过在类中设置特殊属性 `__match_args__`，为属性指定其在模式中对应的位置。若设为 `("x", "y")`，则以下模式相互等价

```python
Point(1, var)
Point(1, y=var)
Point(x=1, y=var)
Point(y=var, x=1)
```

有一个由 Point 组成的列表，且 Point 添加了 `__match_args__` 时，可以这样来匹配它

```python
class Point:
    __match_args__ = ('x', 'y')
    def __init__(self, x, y):
        self.x = x
        self.y = y

match points:
    case []:
        print("No points")
    case [Point(0, 0)]:
        print("The origin")
    case [Point(x, y)]:
        print(f"Single point {x}, {y}")
    case [Point(0, y1), Point(0, y2)]:
        print(f"Two on the Y axis at {y1}, {y2}")
    case _:
        print("Something else")
```

可以为模式添加 `if` 作为守卫子句。如果守卫子句的值为假，那么 `match` 会继续尝试匹配下一个 `case` 块

```python
match point:
    case Point(x, y) if x == y:
        print(f"Y=X at {x}")
    case Point(x, y):
        print(f"Not on the diagonal")
```

使用 `as` 关键字可以捕获子模式

```python
case (Point(x1, y1), Point(x2, y2) as p2): ...
```

将把输入中的第二个元素捕获为 p2 （只要输入是包含两个点的序列）

模式可以使用具名常量。它们必须作为带点号的名称出现，以防止它们被解释为用于捕获的变量

```python
from enum import Enum
class Color(Enum):
    RED = 'red'
    GREEN = 'green'
    BLUE = 'blue'

color = Color(input("Enter your choice of 'red', 'blue' or 'green': "))

match color:
    case Color.RED:
        print("I see red!")
    case Color.GREEN:
        print("Grass is green")
    case Color.BLUE:
        print("I'm feeling the blues :(")
```

## 函数

```python
def fib(n):    # 打印小于 n 的斐波那契数列
    a, b = 0, 1
    while a < n:
        print(a, end=' ')
        a, b = b, a+b
    print()

# 调用刚定义的函数
fib(2000)
```

### 默认值参数

```python
def func(arg1, arg2=1, arg3='message'):...

func(0)
func(0, 2)
func(0, 2, 'msg')
```

**默认值只计算一次！** 默认值为 **列表**、**字典** 或 **类实例** 等可变对象时，会产生与该规则不同的结果

### 关键字参数

函数调用时可以使用关键字参数，关键字参数必须跟在位置参数后面

```python
def func(arg1, arg2, arg3, *args, **kwargs):...

func(0, arg2=2)
func(0, arg3='msg')
```

`*name` 形参接收一个 元组，该元组包含形参列表之外的位置参数。

形参为 `**name` 形式时，接收一个字典，该字典包含与函数中已定义形参对应之外的所有关键字参数

### 特殊参数

```python
def f(pos1, pos2, /, pos_or_kwd, *, kwd1, kwd2):...
#     -----------    ----------     ----------
#     仅位置         位置或关键字     仅关键字                         
```

函数定义中未使用 `/` 和 `*` 时，参数可以按位置或关键字传递给函数。

使用 `/` 和 `*` 时如下

```python
def pos_only_arg(arg, /):... # 仅位置
def kwd_only_arg(*, arg):... # 仅关键字
def combined(pos_only, /, standard, *, kwd_only):... # 混合
```

### 解包参数列表

```python
args = [3, 6]
range(*args)
# 等价于 range(3, 6)
```

### lambda

`lambda` 关键字用于创建小巧的匿名函数，可用于任何需要函数对象的地方。在语法上，匿名函数只能是单个表达式。在语义上，它只是常规函数定义的语法糖。与嵌套函数定义一样，可以引用包含作用域中的变量。

```python
f = lambda x: x * x
f(2)
```

## 数据结构

### list 列表

```python
l = [1, 2, 3]
```

list是一种有序的集合，可以随时添加和删除其中的元素。

`list.append(x)` 在列表末尾添加一项。

`list.extend(iterable)` 通过添加来自 `iterable` 的所有项来扩展列表。

`list.insert(i, x)` 在指定位置插入元素。第一个参数是插入元素的索引，因此，`a.insert(0, x)` 在列表开头插入元素， `a.insert(len(a), x)` 等同于 `a.append(x)`。

`list.remove(x)` 从列表中删除第一个值为 `x` 的元素。未找到指定元素时，触发 `ValueError` 异常。

`list.pop([i])` 移除列表中给定位置上的条目，并返回该条目。如果未指定索引号，则 `a.pop()` 将移除并返回列表中的最后一个条目。如果列表为空或索引号在列表索引范围之外则会引发 `IndexError`。

`list.clear()` 移除列表中的所有项。

`list.index(x[, start[, end]])` 返回列表中 `x` 首次出现位置的从零开始的索引。 如无此条目则会引发 `ValueError`。可选参数 `start` 和 `end` 是切片符号，用于将搜索限制为列表的特定子序列。返回的索引是相对于整个序列的开始计算的，而不是 `start` 参数。

`list.count(x)` 返回列表中元素 `x` 出现的次数。

`list.sort(*, key=None, reverse=False)` 就地排序列表中的元素（要了解自定义排序参数，详见 `sorted()`）。

`list.reverse()` 翻转列表中的元素。

`list.copy()` 返回列表的浅拷贝。

### 列表推导式

列表推导式创建列表的方式更简洁

```python
squares = [x**2 for x in range(10)]
```

等价于

```python
squares = []
for x in range(10):
    squares.append(x**2)
```

列表推导式的方括号内包含以下内容：一个表达式，后面为一个 `for` 子句，然后，是零个或多个 `for` 或 `if` 子句。结果是由表达式依据 `for` 和 `if` 子句求值计算而得出一个新列表。

```python
[(x, y) for x in [1,2,3] for y in [3,1,4] if x != y]
# [(1, 3), (1, 4), (2, 3), (2, 1), (2, 4), (3, 1), (3, 4)]
```

### tuple 元组

`tuple` 一旦初始化就不能修改

```python
t = (1, 2, 3)
```

### set 集合

### dict 字典

## 模块和包

为了方便维护，最好把脚本拆分成多个文件，在 Python 中，一个 Python 文件就是一个模块。

可使用 `import` 语句导入模块

```python
import mymodule
from mymodule import *
from mymodule import func
```

模块可以以脚本的方式执行，这时 `__name__` 变量会设置为 `"__main__"`

```python
# mymodule.py
def func():...

if __name__ == "__main__":
    print("hello from mymodule")
```

```bash
python mymodule.py
```

上面的模块既可以被引入，也可以被执行

当导入一个模块时，解释器首先会搜索具有该名称的内置模块。这些模块的名称在 `sys.builtin_module_names` 中列出。 如果未找到，它将在变量 `sys.path` 所给出的目录列表中搜索名为 spam.py 的文件。 `sys.path` 是从这些位置初始化的:

被命令行直接运行的脚本所在的目录（或未指定文件时的当前目录）。

PYTHONPATH （目录列表，与 shell 变量 PATH 的语法一样）。

依赖于安装的默认值（按照惯例包括一个 `site-packages` 目录，由 `site` 模块处理）。

初始化后，Python 程序可以更改 `sys.path`。脚本所在的目录先于标准库所在的路径被搜索。这意味着，脚本所在的目录如果有和标准库同名的文件，那么加载的是该目录里的，而不是标准库的。这一般是一个错误，除非这样的替换是你有意为之。

为了快速加载模块，Python 把模块的编译版本缓存在 `__pycache__` 目录中，文件名为 module.version.pyc，version 对编译文件格式进行编码，一般是 Python 的版本号。例如，CPython 的 3.3 发行版中，spam.py 的编译版本缓存为 `__pycache__/spam.cpython-33.pyc`。这种命名惯例让不同 Python 版本编译的模块可以共存。

Python 对比编译版与源码的修改日期，查看编译版是否已过期，是否要重新编译。此进程完全是自动的。此外，编译模块与平台无关，因此，可在不同架构的系统之间共享相同的库。

Python 在两种情况下不检查缓存。一，从命令行直接载入的模块，每次都会重新编译，且不储存编译结果；二，没有源模块，就不会检查缓存。为了让一个库能以隐藏源代码的形式分发（通过将所有源代码变为编译后的版本），编译后的模块必须放在源目录而非缓存目录中，并且源目录绝不能包含同名的未编译的源模块。

Python 自带一个标准模块的库。一些模块是内嵌到解释器里面的，它们给一些虽并非语言核心但却内嵌的操作提供接口，要么是为了效率，要么是给操作系统基础操作例如系统调入提供接口。这些模块集是一个配置选项，并且还依赖于底层的操作系统。

包是通过使用“带点号模块名”来构造 Python 模块命名空间的一种方式。

需要有 `__init__.py` 文件才能让 Python 将包含该文件的目录当作包来处理。这可以防止重名的目录如 string 在无意中屏蔽后继出现在模块搜索路径中的有效模块。在最简单的情况下，`__init__.py` 可以只是一个空文件，但它也可以执行包的初始化代码。

## 错误处理

```python
try:
    ...
except Exception as e:
    ...
```

`try` 语句的工作原理如下：

首先，执行 try 子句 （try 和 except 关键字之间的（多行）语句）。

如果没有触发异常，则跳过 except 子句，try 语句执行完毕。

如果在执行 try 子句时发生了异常，则跳过该子句中剩下的部分。 如果异常的类型与 except 关键字后指定的异常相匹配，则会执行 except 子句，然后跳到 try/except 代码块之后继续执行。

如果发生的异常与 except 子句 中指定的异常不匹配，则它会被传递到外层的 try 语句中；如果没有找到处理器，则它是一个 未处理异常 且执行将停止并输出一条错误消息。

try 语句可以有多个 except 子句 来为不同的异常指定处理程序。 但最多只有一个处理程序会被执行。 处理程序只处理对应的 try 子句 中发生的异常，而不处理同一 try 语句内其他处理程序中的异常。 except 子句 可以用带圆括号的元组来指定多个异常

raise 语句支持强制触发指定的异常

```python
raise Exception
```

为了表明一个异常是另一个异常的直接后果， `raise` 语句允许一个可选的 `from` 子句

```python
raise RuntimeError from err
```

还允许使用 from None 表达禁用自动异常链

```python
raise RuntimeError from None
```

程序可以通过创建新的异常类命名自己的异常。不论是以直接还是间接的方式，异常都应从 `Exception` 类派生。

异常类可以被定义成能做其他类所能做的任何事，但通常应当保持简单，它往往只提供一些属性，允许相应的异常处理程序提取有关错误的信息。

大多数异常命名都以 “Error” 结尾，类似标准异常的命名。

许多标准模块定义了自己的异常，以报告他们定义的函数中可能出现的错误。

`try` 语句还有一个可选子句 `finally`，用于定义在所有情况下都必须要执行的清理操作

如果存在 finally 子句，则 finally 子句是 try 语句结束前执行的最后一项任务。不论 try 语句是否触发异常，都会执行 finally 子句。以下内容介绍了几种比较复杂的触发异常情景：

如果执行 try 子句期间触发了某个异常，则某个 except 子句应处理该异常。如果该异常没有 except 子句处理，在 finally 子句执行后会被重新触发。

except 或 else 子句执行期间也会触发异常。 同样，该异常会在 finally 子句执行之后被重新触发。

如果 finally 子句执行 break、 continue 或 return 语句，异常不重新引发。 这可能会引起混淆，因此不鼓励使用。 从 3.14 版开始，编译器会为它发出一个 SyntaxWarning。

如果执行 try 语句时遇到 break,、continue 或 return 语句，则 finally 子句在执行 break、continue 或 return 语句之前执行。

如果一个 finally 子句包含一个 return 语句 ，返回的值将是来自 finally 子句的 return 语句 ，而不是来自 try 子句的 return 语句 。这可能会引起混淆，因此不提倡使用。从版 3.14 开始，编译器会为它发出一个 SyntaxWarning。

在有些情况下，有必要报告几个已经发生的异常。这通常是在并发框架中当几个任务并行失败时的情况，但也有其他的用例，有时需要是继续执行并收集多个错误而不是引发第一个异常。

内置的 `ExceptionGroup` 打包了一个异常实例的列表，这样它们就可以一起被引发。它本身就是一个异常，所以它可以像其他异常一样被捕获。

通过使用 `except*` 代替 `except` ，我们可以有选择地只处理组中符合某种类型的异常。在下面的例子中，显示了一个嵌套的异常组，每个 `except*` 子句都从组中提取了某种类型的异常，而让所有其他的异常传播到其他子句，并最终被重新引发。

```python
def f():
    raise ExceptionGroup(
        "group1",
        [
            OSError(1),
            SystemError(2),
            ExceptionGroup(
                "group2",
                [
                    OSError(3),
                    RecursionError(4)
                ]
            )
        ]
    )

try:
    f()
except* OSError as e:
    print("There were OSErrors")
except* SystemError as e:
    print("There were SystemErrors")
```

当一个异常被创建以引发时，它通常被初始化为描述所发生错误的信息。在有些情况下，在异常被捕获后添加信息是很有用的。为了这个目的，异常有一个 `add_note(note)` 方法接受一个字符串，并将其添加到异常的注释列表。标准的回溯在异常之后按照它们被添加的顺序呈现包括所有的注释。

```python
try:
    raise TypeError('bad type')
except Exception as e:
    e.add_note('Add some information')
    e.add_note('Add some more information')
    raise
```

## 类

```python
class MyClass:
    def __init__(self, name):
        self.name = name

my_class = MyClass('my_class')
```
