# C

C 是一种命令式过程式语言，支持结构化编程、词法变量作用域和递归，具有静态类型系统。它被设计为编译以提供对内存的低级访问，以及能够高效映射到机器指令的语言结构，所有这些都具有最小的运行时支持。

C 语言由 丹尼斯·麦卡利斯泰尔·里奇 (Dennis MacAlistair Ritchie) 在 20 世纪 70 年代在贝尔实验室设计、开发出来。在 20 世纪 80 年代，C 语言逐渐流行，现已成为最广泛使用的编程语言之一，几乎所有现代计算机架构和操作系统都有 C 语言编译器。自 1989 年起，C 语言由美国国家标准协会（ANSI）标准化，随后由国际标准化组织（ISO）和国际电工委员会（IEC）共同标准化。

语言标准：C89, C95, C99, C11, C17, C23

## 参考文献

* 《The C Programming Language》Dennis M. Ritchie
* [cppreference.com](https://cppreference.com)

## Hello World

```c
#include <stdio.h>

int main() {
    printf("Hello World!\n");
}
```

## 注释

```c
// 单行注释

/*
多行注释 
*/
```

## 标识符

以字母或下划线开头，后面可以跟字母、数字、下划线，不允许其他符号，大小写敏感，不允许使用关键字作为标识符。

## 数据类型

一些数据类型根据处理器位数的不同（16 / 32 / 64 位）大小也不同。

| 类型                 | 大小           |
| -------------------- | -------------- |
| `bool` ( C23 )       | 1 字节         |
| `char`               | 1 字节         |
| `unsigned char`      | 1 字节         |
| `short`              | 2 字节         |
| `unsigned short`     | 2 字节         |
| `int`                | 2 / 4 / 4 字节 |
| `unsigned int`       | 2 / 4 / 4 字节 |
| `long`               | 4 / 4 / 8 字节 |
| `unsigned long`      | 4 / 4 / 8 字节 |
| `long long`          | 8 字节         |
| `unsigned long long` | 8 字节         |
| `float`              | 4 字节         |
| `double`             | 8 字节         |
| `long double`        | 至少 8 字节    |
| `void *`             | 2 / 4 / 8 字节 |

## 预处理

预处理指令用于在编译前预处理源代码。

### `#include`

使用 `#include` 指令包含其他源文件。

```c
// 包含编译器提供的头文件
#include <stdio.h>
// 包含用户提供的头文件
#include "./my_header.h"
```

### 宏定义

使用 `#define` 定义，`#undef` 取消定义。

```c
#define PI 3.1415926
#undef PI
#define MAX(a, b) ((a) > (b) ? (a) : (b))
```

#### 使用 `/` 进行换行

```c
#define REPEAT_PRINT(msg, n) \
    for (int i = 0; i < n; i++) { \
        printf(msg); \
    }
```

#### 使用 `#` 字符串化

```c
#define STR(s) #s
char *str = STR(string\n); // char *str = "string\n"; 
```

#### 使用 `##` 连接符号

```c
#define MK_ID(n) id##n
int MK_ID(1), MK_ID(2), MK_ID(3); // int id1, id2, id3;
```

#### 不定参数宏

多余参数使用 `...` 表示，且只能放在最后。在替换时使用 `__VA_ARGS__` 代表多余的参数。

```c
#define INFO(level, ...) \
    printf("[INFO]") \
    printf(__VA_ARGS__)
```

#### 预定义宏

`__FILE__` 进行编译的源文件名。  
`__LINE__` 文件当前的行号。  
`__DATE__` 文件被编译的日期。  
`__TIME__` 文件被编译的时间。  
`__STDC__` 如果编译器遵循ANSI C，其值为1，否则未定义。  

### 条件判断

```c
#define DEBUG 1
#define STATE 1

#if STATE == 1
    printf("STATE 1\n");
#elif STATE == 2
    printf("STATE 2\n");
#else
    printf("STATE else\n");
#endif

#if DEBUG
printf("DEBUG\n");
#endif

#if !DEBUG
printf("NOT DEBUG\n");
#endif

#if defined(DEBUG)
printf("DEBUG\n");
#enndif

#if !defined(DEBUG)
printf("NOT DEBUG\n");
#endif

#ifdef DEBUG
printf("DEBUG\n");
#endif

#ifndef DEBUG
printf("NOT DEBUG\n");
#endif
```

经典用例：防止重包含

```c
#ifndef __MY_HEADER_H__
#define __MY_HEADER_H__
// some code
#endif
```

### `#line`

`#line` 用于修改当前行号，可以覆盖 `__LINE__` 和 `__FILE__`。

```c
// 下一行行号变为 114514
#line 114514
// 下一行行号变为 1919810，文件名变为 homo.c
#line 1919810 "homo.c"
```

### `#error`

`#error` 用于生成编译错误，终止编译。

```c
#if __STDC_VERSION__ < 201112L
    #error "C11 or higher is required"
#endif
```

### `#pragma`

`#pragma` 指令提供了编译器特定的预处理功能。

```c
// 只包含一次
// 大多数编译器都支持
#pragma once
```
