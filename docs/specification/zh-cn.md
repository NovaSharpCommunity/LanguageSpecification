# NovaSharp Beta 1.0 语言标准快照

NovaSharp 起源于其第一位作者对编程语言的美好幻想，他希望编程语言能够美观、能够不受阻碍地开发任何程序、能够让他用得舒服。

NovaSharp 是一门混合范式的编程语言，以强大的多场景适配能力与高表达力为设计目标，能够使用高级语法轻松驾驭底层开发。

它面向资深程序员，为极端开发场景提供锋利而听话的工具。

> [!CAUTION]
> NovaSharp Beta 1.0 是一个不稳定版本。
>
> 这意味着该版本 NovaSharp 随时可能发生破坏性变更。

## 目录

- [1. 词法](#1-词法)
  - [1.1 源代码文本文件](#11-源代码文本文件)
  - [1.2 空白与行终止](#12-空白与行终止)
  - [1.3 注释](#13-注释)
  - [1.4 标识符](#14-标识符)
  - [1.5 标识符定义简写](#15-标识符定义简写)
  - [1.6 关键字](#16-关键字)
  - [1.7 字面量](#17-字面量)
    - [1.7.1 字面量](#171-字面量)
    - [1.7.2 整数](#172-整数)
    - [1.7.3 浮点数](#173-浮点数)
    - [1.7.4 布尔值](#174-布尔值)
    - [1.7.5 字符](#175-字符)
    - [1.7.6 字符串](#176-字符串)
    - [1.7.7 编码与编码标注](#177-编码与编码标注)
    - [1.7.8 转义序列](#178-转义序列)
    - [1.7.9 数组](#179-数组)
    - [1.7.10 函数](#1710-函数)
    - [1.7.11 无穷值](#1711-无穷值)
    - [1.7.12 非法值](#1712-非法值)
    - [1.7.13 未初始化](#1713-未初始化)
  - [1.8 语句终止](#18-语句终止)
  - [1.9 语义映射表](#19-语义映射表)
- [2. 类型](#2-类型)
  - [2.1 类型构造语法](#21-类型构造语法)
  - [2.2 基本类型](#22-基本类型)
  - [2.3 值类型](#23-值类型)
  - [2.4 引用类型](#24-引用类型)
  - [2.5 引用](#25-引用)
  - [2.6 类型构造器](#26-类型构造器)
    - [2.6.1 类型构造器](#261-类型构造器)
    - [2.6.2 数组类型构造器](#262-数组类型构造器)
    - [2.6.3 指针类型构造器](#263-指针类型构造器)
    - [2.6.4 函数类型构造器](#264-函数类型构造器)
  - [2.7 自定义类型](#27-自定义类型)
    - [2.7.1 类](#271-类)
    - [2.7.2 结构体](#272-结构体)
    - [2.7.3 接口](#273-接口)
    - [2.7.4 枚举](#274-枚举)
    - [2.7.5 变体](#275-变体)
    - [2.7.6 共同体](#276-共同体)
    - [2.7.7 继承列表](#277-继承列表)
  - [2.8 成员](#28-成员)
    - [2.8.1 字段](#281-字段)
    - [2.8.2 访问器](#282-访问器)
    - [2.8.3 扩展](#283-扩展)
- [3. 表达式](#3-表达式)
  - [3.1 表达式](#31-表达式)
  - [3.2 值表达式](#32-值表达式)
  - [3.3 括号表达式](#33-括号表达式)
  - [3.4 类型转换表达式](#34-类型转换表达式)
  - [3.5 访问表达式](#35-访问表达式)
    - [3.5.1 访问表达式](#351-访问表达式)
    - [3.5.2 成员访问表达式](#352-成员访问表达式)
    - [3.5.3 指针成员访问表达式](#353-指针成员访问表达式)
    - [3.5.4 索引访问表达式](#354-索引访问表达式)
  - [3.6 函数调用表达式](#36-函数调用表达式)
  - [3.7 构造表达式](#37-构造表达式)
  - [3.8 成员构造表达式](#38-成员构造表达式)
  - [3.9 is 表达式](#39-is-表达式)
  - [3.10 运算符](#310-运算符)
    - [3.10.1 运算符](#3101-运算符)
    - [3.10.2 运算符优先级](#3102-运算符优先级)
    - [3.10.3 运算符重载](#3103-运算符重载)
    - [3.10.4 取负表达式](#3104-取负表达式)
    - [3.10.5 逻辑非表达式](#3105-逻辑非表达式)
    - [3.10.6 按位取反表达式](#3106-按位取反表达式)
    - [3.10.7 引用表达式](#3107-引用表达式)
    - [3.10.8 解引用表达式](#3108-解引用表达式)
    - [3.10.9 乘法表达式](#3109-乘法表达式)
    - [3.10.10 除法表达式](#31010-除法表达式)
    - [3.10.11 求余表达式](#31011-求余表达式)
    - [3.10.12 加法表达式](#31012-加法表达式)
    - [3.10.13 减法表达式](#31013-减法表达式)
    - [3.10.14 逻辑左移表达式](#31014-逻辑左移表达式)
    - [3.10.15 逻辑右移表达式](#31015-逻辑右移表达式)
    - [3.10.16 小于表达式](#31016-小于表达式)
    - [3.10.17 大于表达式](#31017-大于表达式)
    - [3.10.18 小于等于表达式](#31018-小于等于表达式)
    - [3.10.19 大于等于表达式](#31019-大于等于表达式)
    - [3.10.20 相等表达式](#31020-相等表达式)
    - [3.10.21 不等表达式](#31021-不等表达式)
    - [3.10.22 按位与表达式](#31022-按位与表达式)
    - [3.10.23 按位异或表达式](#31023-按位异或表达式)
    - [3.10.24 按位或表达式](#31024-按位或表达式)
    - [3.10.25 逻辑和表达式](#31025-逻辑和表达式)
    - [3.10.26 逻辑或表达式](#31026-逻辑或表达式)
    - [3.10.27 空值合并表达式](#31027-空值合并表达式)
    - [3.10.28 条件表达式](#31028-条件表达式)
- [4. 语句](#4-语句)
  - [4.1 语句](#41-语句)
  - [4.2 代码块](#42-代码块)
  - [4.3 变量](#43-变量)
  - [4.4 常量](#44-常量)
  - [4.5 堆分配](#45-堆分配)
  - [4.6 赋值语句](#46-赋值语句)
  - [4.7 dispose 语句](#47-dispose-语句)
  - [4.8 逻辑控制流](#48-逻辑控制流)
    - [4.8.1 逻辑控制流名称](#481-逻辑控制流名称)
    - [4.8.2 if 语句](#482-if-语句)
    - [4.8.3 while 语句](#483-while-语句)
    - [4.8.4 do while 语句](#484-do-while-语句)
    - [4.8.5 for 语句](#485-for-语句)
    - [4.8.6 match 语句](#486-match-语句)
    - [4.8.7 break 语句](#487-break-语句)
    - [4.8.8 continue 语句](#488-continue-语句)
  - [4.9 控制流](#49-控制流)
    - [4.9.1 异常处理](#491-异常处理)
    - [4.9.2 return 语句](#492-return-语句)
    - [4.9.3 throw 语句](#493-throw-语句)
    - [4.9.4 trap 语句](#494-trap-语句)
- [5. 名称](#5-名称)
  - [5.1 作用域](#51-作用域)
  - [5.2 可访问性](#52-可访问性)
  - [5.3 标识符唯一性](#53-标识符唯一性)
  - [5.4 遮蔽](#54-遮蔽)
- [6. 模块](#6-模块)
  - [6.1 模块](#61-模块)
  - [6.2 导入](#62-导入)
- [7. 函数](#7-函数)
  - [7.1 函数定义语法糖](#71-函数定义语法糖)
  - [7.2 参数](#72-参数)
  - [7.3 实参](#73-实参)
  - [7.4 方法](#74-方法)
  - [7.5 重载决议](#75-重载决议)
- [8. 修饰符](#8-修饰符)
  - [8.1 修饰符](#81-修饰符)
  - [8.2 可访问性修饰符](#82-可访问性修饰符)
  - [8.3 public 修饰符](#83-public-修饰符)
  - [8.4 private 修饰符](#84-private-修饰符)
  - [8.5 protected 修饰符](#85-protected-修饰符)
  - [8.6 scoped 修饰符](#86-scoped-修饰符)
  - [8.7 readonly 修饰符](#87-readonly-修饰符)
  - [8.8 implicitable 修饰符](#88-implicitable-修饰符)
  - [8.9 verbatim 修饰符](#89-verbatim-修饰符)
  - [8.10 linkable 修饰符](#810-linkable-修饰符)
  - [8.11 abstract 修饰符](#811-abstract-修饰符)
  - [8.12 sealed 修饰符](#812-sealed-修饰符)
  - [8.13 virtual 修饰符](#813-virtual-修饰符)
  - [8.14 override 修饰符](#814-override-修饰符)
  - [8.15 aligned(N) 修饰符](#815-alignedn-修饰符)
  - [8.16 static 修饰符](#816-static-修饰符)
- [9. 泛型](#9-泛型)
  - [9.1 泛型参数](#91-泛型参数)
  - [9.2 单态化表达式](#92-单态化表达式)
- [10. 编译期](#10-编译期)
  - [10.1 编译期执行](#101-编译期执行)
  - [10.2 编译期执行顺序](#102-编译期执行顺序)
  - [10.3 编译期表达式](#103-编译期表达式)
  - [10.4 编译期块](#104-编译期块)
  - [10.5 编译期常量参数](#105-编译期常量参数)
  - [10.6 编译期边界](#106-编译期边界)
  - [10.7 编译器 API](#107-编译器-api)
- [11. 内存模型](#11-内存模型)
  - [11.1 内存分配](#111-内存分配)
  - [11.2 NOLAA](#112-nolaa)
- [12. ABI](#12-abi)
  - [12.1 NovaSharp ABI](#121-novasharp-abi)
  - [12.2 名称修饰](#122-名称修饰)
- [13. 程序](#13-程序)
  - [13.1 主函数](#131-主函数)
  - [13.2 启动流程](#132-启动流程)
  - [13.3 编译优化](#133-编译优化)
    - [13.3.1 编译优化总则](#1331-编译优化总则)
    - [13.3.2 体积优化](#1332-体积优化)
    - [13.3.3 速率优化](#1333-速率优化)
- [14. 设计基准](#14-设计基准)
  - [14.1 核心设计哲学](#141-核心设计哲学)
  - [14.2 设计原则](#142-设计原则)
  - [14.3 Built-In Library 设计原则](#143-built-in-library-设计原则)
- [15. 附录](#15-附录)
  - [15.1 语法速查表](#151-语法速查表)
  - [15.2 Built-In Library 完整内容](#152-built-in-library-完整内容)
  - [15.3 Compile-Time Library 完整内容](#153-compile-time-library-完整内容)

## 1. 词法

### 1.1 源代码文本文件

**源代码文本文件**是承载 NovaSharp 代码的文本文件。

要求源代码文本文件**必须**满足如下**所有**条件：

- 文本编码**必须**是 UTF-8
- 文件扩展名**必须**是 `.ns`
- 内容**必须**仅包含 NovaSharp 代码
- 内容**必须**全部符合 NovaSharp 语法规范

### 1.2 空白与行终止

**空白和行终止符**是用于分隔 Token 的字符集合。

**定义**以下**任一**字符为空白字符：

- 空格：`U+0020`
- 水平制表：`U+0009`
- 换行：`U+000A`
- 回车：`U+000D`

其中：

- **定义**换行与回车为行终止符

有关行终止符：

- 编译器**必须**使用行终止符进行行号映射

### 1.3 注释

**注释**是编译器忽略的代码说明文本。

注释由以下**任一**形式组成：

- 单行注释：由 `//` 起始、至行终止符（见 [空白与行终止](#12-空白与行终止)）终止的字符序列
- 多行注释：由 `/*` 起始、至其后第一个 `*/` 终止的字符序列

其中：

- 单行注释中的 `//` **不得**处于字符串字面量内
- 多行注释中的 `/*` **不得**处于字符串字面量内
- 多行注释**不得**嵌套

有关注释：

- 编译器**必须**将注释内容视为空白
- 注释内容**不得**参与编译

### 1.4 标识符

**标识符**是开发者自定义内容的名称**或**成员访问表达式，其格式如下：

```ebnf
Identifier       = Name | MemberAccessExpression .

Name             = ( "a" .. "z" | "A" .. "Z" | "_" ) { "a" .. "z" | "A" .. "Z" | "0" .. "9" | "_" } .
```

其中：

- **定义** `Identifier` 为标识符
- **定义** `Name` 为名称
  - 名称**不得**由数字开头
  - 名称中**不得**出现 `.`、`->`、`<`、`>`、`[`、`]`
- 有关 `MemberAccessExpression`，见 [成员访问表达式](#352-成员访问表达式)

有关语法：

- 有关标识符定义简写，见 [标识符定义简写](#15-标识符定义简写)
- 访问运算符**不得**与两侧的标识符**或**名称之间存在空白（见 [访问表达式](#351-访问表达式)）

有关解析：

- **允许**在标识符前使用字符 `@`，以将标识符强制解析为关键字（见 [关键字](#16-关键字)）原义
  - 字符 `@` 与标识符之间**不得**存在空白

> [!NOTE] NovaSharp vs. C#
> NovaSharp 中 `@` 字符的作用和 C# 是相反的：
>
> - C# 中的 `@` 字符将关键字解析为标识符
> - NovaSharp 中的 `@` 字符将标识符解析为关键字。

例如：

```novasharp
// 声明：标识符 class
variable class: integer(4) = 1;

// 在当前作用域下，可以访问到标识符 class
// 认为标识符 class 已经被定义，遮蔽关键字 class

// 定义：类 MyClass
// 合法：必须在 class 前加入字符 @，以将 class 解析为关键字
@class MyClass { }

// 在当前作用域下，不可以访问到标识符 structure
// 认为关键字 structure 没有被遮蔽

// 定义：结构体 MyStructure
// 合法：仍然可以在 structure 前加入字符 @，将 structure 解析为关键字
@structure MyStructure { }

// 定义：类 integer
class integer { }

// 在当前作用域下，integer 遮蔽基本类型关键字

// 合法：必须加入 @ 才能解析为基本类型
variable x: @integer(4);

// 非法：@ 与标识符之间存在空白
// @ class A { }
// 错误：字符 @ 与标识符之间不得存在空白
```

### 1.5 标识符定义简写

**标识符定义简写**是在标识符定义中以参数列表**或**维度列表替代 `Name ":" Type` 的语法形式，其格式如下：

```ebnf
IdentifierDefinitionShorthand = FunctionShorthand | ArrayShorthand .

FunctionShorthand = Name [ GenericParameters ] "(" [ Parameters | "wildcard" ] [ ";" CallingConventionExpression ] ")" [ ":" Type ] .

ArrayShorthand    = Name "[" Expression { "," Expression } "]" [ ":" Type ] .
```

其中：

- **定义** `IdentifierDefinitionShorthand` 为标识符定义简写
- **定义** `FunctionShorthand` 为函数简写
- **定义** `ArrayShorthand` 为数组简写
- **定义** `Name` 为被定义标识符的名称（见 [标识符](#14-标识符)）
- 有关 `GenericParameters`，见 [泛型参数](#91-泛型参数)
- 有关 `Parameters`，见 [参数](#72-参数)
- 有关 `wildcard`，见 [函数类型构造器](#264-函数类型构造器)
- 有关 `CallingConventionExpression`，见 [函数类型构造器](#264-函数类型构造器)
- **定义** `Expression` 为数组维度表达式（见 [表达式](#31-表达式)）
- **定义** `Type` 为被定义标识符的类型（见 [类型构造语法](#21-类型构造语法)）

有关适用：

- 简写**必须**在类型检查前展开
- 简写**允许**出现在所有带 `Name ":" Type` 的标识符定义位置
  - 变量定义（见 [变量](#43-变量)）
  - 常量定义（见 [常量](#44-常量)）
  - 字段定义（见 [字段](#281-字段)）
  - 共同体成员（见 [共同体](#276-共同体)）
  - variant 状态（见 [变体](#275-变体)）
  - 访问器定义（见 [访问器](#282-访问器)）
  - 堆分配定义（见 [堆分配](#45-堆分配)）
  - 函数参数与函数字面量参数（见 [参数](#72-参数)、[函数](#1710-函数)）
  - `for` 迭代变量（见 [for 语句](#485-for-语句)）
  - `catch` 绑定（见 [trap 语句](#494-trap-语句)）
  - 其它带类型的模式绑定
- 运算符使用 [运算符](#3101-运算符) 的运算符简写；本页简写不适用于 `operator`
- 简写**不得**用于类型声明名、模块名**或**导入别名

有关函数简写：

- `Name(Parameters): Type` **必须**展开为 `Name: function(Parameters) Type`
- `Name(Parameters)` **必须**展开为 `Name: function(Parameters)`
  - **当**省略 `: Type` **时**，返回值类型**必须**为空类型
- 参数列表**允许**包含泛型参数、`#` 参数、`&` 参数、默认值和 `wildcard`
- 调用约定**允许**以 `;` 与参数列表分隔
- 函数简写**不得**与数组简写组合

有关数组简写：

- `Name[Expression { "," Expression }]: Type` **必须**展开为 `Name: array(Expression { "," Expression }) Type`
- `: Type` **不得**省略
  - **当**省略 `: Type` **时**，元素类型**必须**为空类型，**且**该简写**必须**报错
- 数组简写**不得**与函数简写组合
- 数组简写**仅**提供维度，**不得**推断元素类型

有关省略类型：

- 简写**不得**因省略 `: Type` 而进行自动类型推断
- **当**函数简写省略 `: Type` **时**，**必须**使用空返回类型
- **当**数组简写省略 `: Type` **时**，**必须**报错
- **当**需要类型推断**时**，**必须**使用不带简写的定义，例如 `x = Expression`

例如：

```novasharp
// 合法：函数简写
constant Main(): integer(4)
{
    return 0;
}

// 合法：零参数、空返回类型
constant Foo()
{
}

// 非法：返回类型为空，return 0 类型不匹配
// constant Bad()
// {
//     return 0;
// }

// 合法：数组简写
variable a[5]: integer(4);
variable b[5, 5]: integer(4);

// 非法：数组元素类型为空
// variable c[5];

// 合法：需要推断时使用非简写定义
variable d = 0;

// 非法：函数简写与数组简写组合
// variable e[5](): integer(4);

// 合法：显式形式与简写等价
constant Explicit: function() integer(4) { return 0; }
constant Shorthand(): integer(4) { return 0; }

// 合法：循环参数简写
variable matrix: array(5) array(5) integer(4);

for row[5]: integer(4) in matrix
{
    // row: array(5) integer(4)
}
```

### 1.6 关键字

**关键字**是 NovaSharp 中具有固定语义的保留词。由以下保留词组成：

| 类别                   | 语义                                 | 关键字                                                                                                                                     |
| ---------------------- | ------------------------------------ | ------------------------------------------------------------------------------------------------------------------------------------------ |
| **标识符种类**         | 定义标识符的种类                     | `class`、`structure`、`interface`、`enumeration`、`variant`、`union`、`module`、`variable`、`constant`、`accessor`、`allocate`、`operator` |
| **类型构造器**         | 声明高级类型                         | `array`、`function`、`pointer`                                                                                                             |
| **基本类型**           | 内置基础类型                         | `integer`、`unsigned`、`float`、`boolean`                                                                                                  |
| **基础可访问性修饰符** | 给出可访问对象的基础集合             | `public`、`private`、`protected`                                                                                                           |
| **可访问性裁剪修饰符** | 以具名目标收窄基础集合               | `scoped`                                                                                                                                   |
| **行为限定修饰符**     | 限制行为                             | `readonly`                                                                                                                                 |
| **行为激活修饰符**     | 允许行为                             | `implicitable`                                                                                                                             |
| **优化修饰符**         | 授权并要求编译器进行（或不进行）优化 | `verbatim`                                                                                                                                 |
| **其它修饰符**         | -                                    | `linkable`、`abstract`、`virtual`、`override`、`sealed`、`aligned`、`static`                                                               |
| **逻辑控制流**         | -                                    | `if`、`else`、`while`、`do`、`for`、`in`、`match`、`case`、`break`、`continue`、`when`                                                     |
| **控制流**             | -                                    | `return`、`throw`、`trap`、`catch`、`finally`                                                                                              |
| **内存管理关键字**     | 定义主动内存分配/销毁行为            | `manual`、`dispose`                                                                                                                        |
| **作用域访问关键字**   | 访问所属作用域中的成员               | `this`、`owner`、`base`                                                                                                                    |
| **字符编码**           | 字符编码标注                         | `ascii`、`utf8`、`utf16`、`utf32`、`ucs2`、`ucs4`                                                                                          |
| **其它关键字**         | -                                    | `wildcard`、`true`、`false`、`illegal`、`infinite`、`uninitialized`、`import`、`is`、`extension`、`Cast`、`basic`                          |

其中：

- 有关各关键字的语义，见 [语义映射表](#19-语义映射表)
- 有关修饰符，见 [修饰符](#81-修饰符)
- 有关保留词的遮蔽与转义，见 [标识符](#14-标识符)

有关标识符种类：

- **定义**标识符种类为定义标识符时位于修饰符列表之后、名称之前的保留词
- 修饰符列表**必须**位于标识符种类之前
- 标识符种类**必须为**上表「标识符种类」行之一
- 标识符种类**不得**被省略

有关模块：

- 有关 `module`，见 [模块](#61-模块)
- 有关 `import`，见 [导入](#62-导入)

### 1.7 字面量

#### 1.7.1 字面量

**字面量**是表示常量的语法形式，其格式如下：

```ebnf
Literal = IntegerLiteral
        | FloatLiteral
        | ArrayLiteral
        | CharacterLiteral
        | StringLiteral
        | FunctionLiteral
        | BooleanLiteral
        | IllegalLiteral
        | InfiniteLiteral
        | UninitializedLiteral .
```

其中：

- **定义** `Literal` 为字面量
- 有关 `IntegerLiteral`，见 [整数](#172-整数)
- 有关 `FloatLiteral`，见 [浮点数](#173-浮点数)
- 有关 `ArrayLiteral`，见 [数组](#179-数组)
- 有关 `CharacterLiteral`，见 [字符](#175-字符)
- 有关 `StringLiteral`，见 [字符串](#176-字符串)
- 有关 `FunctionLiteral`，见 [函数](#1710-函数)
- 有关 `BooleanLiteral`，见 [布尔值](#174-布尔值)
- 有关 `IllegalLiteral`，见 [非法值](#1712-非法值)
- 有关 `InfiniteLiteral`，见 [无穷值](#1711-无穷值)
- 有关 `UninitializedLiteral`，见 [未初始化](#1713-未初始化)

#### 1.7.2 整数

**整数字面量**是整数类型的字面量表示，其格式如下：

```ebnf
IntegerLiteral = DecimalLiteral | HexLiteral | BinaryLiteral .

DecimalLiteral = Digit { Digit | "_" } .
HexLiteral     = "0x" HexDigit { HexDigit | "_" } .
BinaryLiteral  = "0b" ("0" | "1") { ("0" | "1") | "_" } .

Digit    = "0" .. "9" .
HexDigit = Digit | "A" .. "F" | "a" .. "f" .
```

其中：

- **定义** `DecimalLiteral` 为十进制整数字面量
- **定义** `HexLiteral` 为十六进制整数字面量
  - 十六进制整数字面量**必须**按照十六进制解析
- **定义** `BinaryLiteral` 为二进制整数字面量
  - 二进制整数字面量**必须**按照二进制解析
- **定义**字符 `_` 为分隔符
  - 分隔符在编译期擦除

有关类型：

- 整数字面量的类型可能为 `integer(N)`、`unsigned integer(N)` 或 `float(N)`
- 具体类型**必须**由编译器根据语句上下文推断
  - 上述推断与当前整数字面量内容无关
  - 上述推断**不得**导致编译错误
- **当**无法推断**时**：
  - 类型为 `integer(N)`
  - N **必须**为足以表示该字面量的最小合法字节数
  - **若**上述默认推断失败，**则**编译器**必须**报错
- N 必须为合法值
- 更多，见：[基本类型](#22-基本类型)

例如：

```novasharp
// 合法：十进制整数字面量
variable decimal: integer(4) = 42;

// 合法：带分隔符的十进制整数字面量
variable decimalWithSeparator: integer(4) = 1_000_000;
// 等价于 1000000，分隔符编译期擦除

// 合法：十六进制整数字面量
variable hex: integer(4) = 0xFF;

// 合法：二进制整数字面量
variable binary: integer(4) = 0b1010;

// 合法：类型推断为 unsigned integer(4)
variable unsignedValue: unsigned integer(4) = 0xFFFFFFFF;

// 合法：类型推断为 float(4)
variable floatValue: float(4) = 100;
// 整数字面量在此上下文中推断为 float(4)

// 合法：默认类型推断
// 无显式类型约束时，编译器选择足以表示该字面量的最小合法字节数
variable define = 127;
// 推断为 integer(1)

// 非法：十六进制包含非法字符
// variable bad: integer(4) = 0xFG;
// 错误：意外的字符

// 非法：二进制包含非 0/1 字符
// variable bad: integer(4) = 0b2010;
// 错误：意外的字符

// 非法：值超出目标类型范围
// variable bad: integer(1) = 256;
// 错误：256 超出类型 integer(1) 的取值范围
```

#### 1.7.3 浮点数

**浮点数字面量**是浮点类型的字面量表示，其格式如下：

```ebnf
FloatLiteral = DecimalLiteral "." DecimalLiteral [ Exponent ] .

Exponent = ("e" | "E") [ "+" | "-" ] DecimalLiteral .
```

其中：

- **定义** `Exponent` 为以 10 为底的指数部分，其中：
  - 字符 `e` 和字符 `E` 等价
  - 字符 `+` 表示正指数，字符 `-` 表示负指数
  - 当省略字符 `+` 或 `-` 时，默认为正指数

有关词法：

- 浮点数字面量的扫描**必须**在 `..` **或** `..!` 前终止

有关类型：

- 浮点数字面量的类型为 `float(N)`
- 具体类型**必须**由编译器根据语句上下文推断
  - 上述推断与当前浮点数字面量内容无关
- **当**无法推断**时**：
  - 类型为 `float(N)`
  - N **必须**为足以表示该字面量的最小合法字节数
  - **若**上述默认推断失败，**则**编译器**必须**报错
- N **必须**为合法值
- 更多，见 [基本类型](#22-基本类型)

例如：

```novasharp
// 合法：基本浮点数字面量
variable pi: float(4) = 3.14;

// 合法：带指数
variable large: float(8) = 1.5e10;

// 合法：负指数
variable small: float(4) = 2.5e-3;

// 非法：缺少小数部分
// variable bad: float(4) = 1.;
// 错误：意外的字符：;

// 非法：指数后无数字
// variable bad: float(4) = 1.0e;
// 错误：意外的字符：;

// 非法：值超出目标类型范围
// variable bad: float(4) = 1.0e100;
// 错误：1.0e100 无法由 float(4) 表示
```

#### 1.7.4 布尔值

**布尔值字面量**是布尔类型的字面量表示，其格式如下：

```ebnf
BooleanLiteral = "true" | "false" .
```

有关类型：

- 布尔值字面量的类型为 `boolean`
- 更多，见 [基本类型](#22-基本类型)

#### 1.7.5 字符

**字符字面量**是将字符映射为无符号整数的字面量表示，其格式如下：

```ebnf
CharacterLiteral = "'" ( Character | EscapeSequence ) "'" [ ":" CharacterEncodingTag ] .
```

其中：

- **定义** `Character` 为任意字符
- **定义** `EscapeSequence` 为转义序列（见 [转义序列](#178-转义序列)）
- **定义** `CharacterEncodingTag` 为编码标注（见 [编码与编码标注](#177-编码与编码标注)）

有关语法：

- 字符字面量内部**不得**出现行终止符（有关空白字符，见 [空白与行终止](#12-空白与行终止)）
- 无法直接表达或在上下文中具有二义性的字符（例如换行符）**必须**通过转义序列表达（见 [转义序列](#178-转义序列)）

有关类型：

- 字符字面量的类型为 `unsigned integer(N)`
- N **必须**为合法值
- **当**包含显式编码标记时，N 由编码标注决定（见 [编码与编码标注](#177-编码与编码标注)）
- **当**不包含编码标记**时**：
  - 编码和 N 由编译器根据语句上下文推断
    - 编码**必须**为编码标注表中"对于字符，需要显式标注"一栏为 "否" 的编码（见 [编码与编码标注](#177-编码与编码标注)）
  - **当**推断失败**时**，编码**必须**采用 UTF-8，**且** N **必须为** 4
- `Character` 和 `EscapeSequence` 的内容**必须**为当前字符字面量所用编码支持的内容（见 [编码与编码标注](#177-编码与编码标注)）

例如：

```novasharp
// 合法：基本字符（默认 UTF-8）
variable character: unsigned integer(4) = ' ';

// 合法：显式编码标注
variable asciiCharacter: unsigned integer(1) = 'a':ascii;

// 合法：转义序列
variable newline: unsigned integer(4) = '\n';

// 合法：默认推断
variable c = '中';
// 推断为 unsigned integer(4)，UTF-8 编码

// 非法：空字符字面量
// variable bad = '';
// 错误：缺少字符内容

// 非法：多字符
// variable bad = 'ab';
// 错误：CharacterLiteral 只能包含一个字符或转义序列

// 非法：编码不支持的内容
// variable bad: unsigned integer(1) = '中':ascii;
// 错误：内容超出 ascii 编码范围
```

#### 1.7.6 字符串

**字符串字面量**是将字符串映射为无符号整数类型数组的字面量表示，其格式如下：

```ebnf
StringLiteral = NormalStringLiteral | VerbatimStringLiteral .

NormalStringLiteral       = '"' { Character | EscapeSequence } '"' [ ":" CharacterEncodingTag ] .
VerbatimStringLiteral = '@"' { Character | '""' } '"' [ ":" CharacterEncodingTag ] .
```

其中：

- **定义** `Character` 为任意字符
- **定义** `EscapeSequence` 为转义序列（见 [转义序列](#178-转义序列)）
- **定义** `CharacterEncodingTag` 为编码标注（见 [编码与编码标注](#177-编码与编码标注)）
- **定义** `NormalStringLiteral` 为普通字符串字面量
- **定义** `VerbatimStringLiteral` 为逐字字符串字面量
  - 字符 `@` 与字符 `"` 之间**不得**存在空白

有关普通字符串：

- 普通字符串内部出现行终止符时，该行终止符不作为字符串内容
  - 上述行终止符后紧跟的空白字符不作为字符串内容，直至遇到第一个非空白字符（有关空白字符，见 [空白与行终止](#12-空白与行终止)）
- 无法直接表达或在上下文中具有二义性的字符（例如换行符）**必须**通过转义序列表达（见 [转义序列](#178-转义序列)）

有关逐字字符串：

- 逐字字符串内部出现换行符时，该换行符**必须**作为字符串内容保留
- 上述换行符后紧跟的空白字符**必须**作为字符串内容保留
- 编译器**必须**将逐字字符串内部两个连续的 `"` 解析为一个 `"` 字符
- 逐字字符串**不得**解析转义序列

有关类型：

- 有关字面量池化，见 [体积优化](#1332-体积优化)

- 字符串字面量的类型为 `array(L / N) unsigned integer(N)`
- **定义** `L` 为字符串编码后得到的字节序列长度（有关 `array(N)`，见 [数组类型构造器](#262-数组类型构造器)）
  - `L` **必须为** `N` 的倍数
- `N` **必须**为合法值
- **当**包含显式编码标记时，`N` 由编码标注决定（见 [编码与编码标注](#177-编码与编码标注)）
- **当**不包含编码标记时，`N` 为 1，采用 UTF-8 编码
- `Character` 和 `EscapeSequence` 的内容**必须**为当前字符串字面量所用编码支持的内容（见 [编码与编码标注](#177-编码与编码标注)）

> [!NOTE] NovaSharp 字符串字面量的返回值不以 `\0` 结尾，其长度由类型决定
> 当和 C API 互操作时，需要手动添加 `\0`。

> [!NOTE] NovaSharp 字符串字面量长度**不是**字符数量
> NovaSharp 字符串字面量长度是字符串字节数，受内容和编码决定。

例如：

```novasharp
// 合法：基本字符串（默认 UTF-8）
variable hello[13]: unsigned integer(1) = "Hello, World!";

// 合法：普通字符串换行丢弃
variable singleLine[27]: unsigned integer(1) = "第一行，
    还是第一行";
// 等价于 "第一行，还是第一行"
// 注意：行终止符前的空白字符会被保留

// 合法：转义序列
variable withNewline[19]: unsigned integer(1) = "第一行\n第二行";

// 合法：显式编码标注
variable explicitAscii[5]: unsigned integer(1) = "Hello":ascii;

// 合法：逐字字符串换行保留
variable multiLine[33]: unsigned integer(1) = @"第一行,
    不是第一行了";
// 换行和缩进空白均保留

// 合法：逐字字符串转义失效
variable path[13]: unsigned integer(1) = @"C:\Users\test";
// 内容等价于 C:\Users\test，反斜杠不视为转义

// 合法：逐字字符串连续引号
variable quote[15]: unsigned integer(1) = @"He said ""Hello""";
// 内容等价于 He said "Hello"

// 非法：逐字字符串中 @ 与 " 之间存在空白
// variable bad: array(5) unsigned integer(1) = @ "Hello";
// 错误：意外的字符：@

// 非法：编码不支持的内容
// variable bad: array(1) unsigned integer(1) = "中":ascii;
// 错误：内容超出 ascii 编码范围
```

#### 1.7.7 编码与编码标注

**编码标注**是字符和字符串的字符集标注方式，其格式如下：

```ebnf
CharacterEncodingTag = "ascii"
                     | "utf8"
                     | "utf16"
                     | "utf32"
                     | "ucs2"
                     | "ucs4" .
```

NovaSharp 的字符和字符串**仅**支持如下编码：

| 编码   | 字符类型中的 N 值 | 对于字符，<br>需要显式标注 | 字符串类型中的 N 值 | 对于字符串，<br>需要显式标注 | 标注    |
| ------ | ----------------- | -------------------------- | ------------------- | ---------------------------- | ------- |
| ASCII  | 1                 | **否**                     | 1                   | 是                           | `ascii` |
| UTF-8  | 4                 | **否**                     | 1                   | **否**                       | `utf8`  |
| UTF-16 | 2 或 4            | 是                         | 2                   | 是                           | `utf16` |
| UTF-32 | 4                 | 是                         | 4                   | 是                           | `utf32` |
| UCS-2  | 2                 | 是                         | 2                   | 是                           | `ucs2`  |
| UCS-4  | 4                 | 是                         | 4                   | 是                           | `ucs4`  |

#### 1.7.8 转义序列

**转义序列**是字符和字符串中表示特殊字符的字符组合，其格式如下：

```ebnf
EscapeSequence = "\" ( "a" | "b" | "f" | "n" | "r" | "t" | "v" | "\" | '"' | "'" | "0" )
               | "\x" HexDigit HexDigit
               | "\u" HexDigit HexDigit HexDigit HexDigit
               | "\U" HexDigit HexDigit HexDigit HexDigit HexDigit HexDigit HexDigit HexDigit .
```

其中：

- **定义** `EscapeSequence` 为转义序列
- 有关 `HexDigit`，见 [整数](#172-整数)

NovaSharp 的字符和字符串**仅**支持如下转义序列：

| 序列            | 含义                 |
| --------------- | -------------------- |
| `\a`            | 响铃                 |
| `\b`            | 退格                 |
| `\f`            | 换页                 |
| `\n`            | 换行                 |
| `\r`            | 回车                 |
| `\t`            | 水平制表             |
| `\v`            | 垂直制表             |
| `\\`            | 反斜杠               |
| `\"`            | 双引号               |
| `\'`            | 单引号               |
| `\0`            | 空字符               |
| `\x` _hh_       | 两位十六进制字节     |
| `\u` _hhhh_     | 四位十六进制 Unicode |
| `\U` _hhhhhhhh_ | 八位十六进制 Unicode |

#### 1.7.9 数组

**数组字面量**是数组类型的字面量表示，其格式如下：

```ebnf
ArrayLiteral = "{" [ Element { "," Element } [ "," ] ] "}" .

Element      = Expression | RepeatElement | RangeElement .

RepeatElement = "[" Expression ":" Expression "]" .

RangeElement  = "[" Expression [ ".." Expression ] ( ".." | "..!" ) Expression "]" .
```

其中：

- **定义** `Element` 为元素
- **定义** `Expression` 为值表达式（见 [表达式](#31-表达式)）
- **定义** `RepeatElement` 为重复展开
  - **定义**其首个 `Expression` 为被重复的值
  - **定义**其第二个 `Expression` 为次数
- **定义** `RangeElement` 为区间展开
  - **定义**其首个 `Expression` 为起始值
  - **定义**其第二个 `Expression` 为步长
  - **定义**其第三个 `Expression` 为终止值
- **允许**元素为数组字面量

有关元素：

- 重复展开的次数、区间展开的起始值、步长与终止值都**必须**为编译期常量
- 展开**必须**在编译期完成
- 区间展开**必须**遵循 for 语句的区间闭开规则（见 [for 语句](#485-for-语句)）
- **当**省略区间展开的步长**时**，**必须**按 for 语句的规则确定默认步长（见 [for 语句](#485-for-语句)）

有关类型：

- 数组字面量的类型为 `array(N) T`，其中：
  - **定义** `T` 为各元素展开后所得的值的公共可推断类型
  - **定义** `N` 为各元素展开后长度之和
- 数组字面量的所有展开值**必须**满足以下**任一**条件：
  - 类型为 `T`
  - 类型可隐式转换为 `T`
- **允许** `T` 为数组类型
- **若**无法推断 `T`（如空数组 `{}` 且无上下文约束），**则**编译器**必须**报错
- 更多，见 [数组类型构造器](#262-数组类型构造器)

有关解析：

- **当** `{` 出现于表达式位置**时**，**判定**其为数组字面量
- **当** `{` 出现于定义体位置**时**，**判定**其为代码块（见 [代码块](#42-代码块)）

例如：

```novasharp
// 合法：基本数组
variable arr[3]: integer(1) = { 1, 2, 3 };

// 合法：嵌套数组
variable nested[2, 2]: integer(1) = { { 1, 2 }, { 3, 4 } };

// 合法：尾随逗号
variable trailing[2]: integer(1) = { 1, 2, };

// 合法：重复展开
variable filled[4]: integer(4) = { 1, [2: 3] }; // 1, 2, 2, 2

// 合法：区间展开
variable expanded[6]: integer(4) = { 1, [1..5] }; // 1, 1, 2, 3, 4, 5

// 合法：带步长的区间展开
variable stepped[6]: integer(4) = { [0..2..10] }; // 0, 2, 4, 6, 8, 10

// 合法：空数组（有上下文约束）
constant TakeArray(empty[0]: integer(4)) { }
TakeArray({});

// 非法：空数组无上下文约束
// variable bad = {};
// 错误：无法推断元素类型

// 非法：元素类型不兼容
// variable bad: array(2) integer(1) = { 1, 1.5 };
// 错误：元素类型不可隐式转换

// 定义：变量 count
variable count: unsigned integer(4) = 3;

// 非法：展开参数不是编译期常量
// variable bad: array(4) integer(4) = { [0: count] };
// 错误：展开参数必须为编译期常量
```

#### 1.7.10 函数

**函数字面量**实现被调用方的约定，是创建函数的唯一方式，其格式如下：

```ebnf
FunctionLiteral = "(" [ LiteralParameters ] [ ";" CallingConventionExpression ] ")" [ Type ] "=>" Block .
```

其中：

- 有关 `LiteralParameters`，见 [参数](#72-参数)
- 有关 `CallingConventionExpression`，见 [函数类型构造器](#264-函数类型构造器)
- **定义** `Type` 为返回类型（**允许**省略）
- **定义** `Block` 为函数体（见 [代码块](#42-代码块)）

有关类型：

- 函数字面量的类型**必须为** `function(LiteralParameters, CallingConvention) Type`，其中：
  - `LiteralParameters` 由参数列表决定
  - `CallingConvention` 由 `CallingConventionExpression` 决定；省略时为 `CallingConvention.PlatformDefault`
  - `CallingConvention.PlatformDefault` **必须**表示目标平台的默认调用约定
  - `Type` 为返回类型
- **当**省略 `Type` **时**，返回值类型**必须为**空类型
- **当**省略参数类型**时**，参数类型**必须**由期望的函数类型推断
  - **当**无法推断**时**，编译器**必须**报错
  - 返回类型**不得**由期望的函数类型推断
- 更多，见 [函数类型构造器](#264-函数类型构造器)

有关调用约定：

- 调用约定**必须**满足如下**所有**条件：
  - 返回值类型为 `CallingConvention`
  - **必须**可在编译期求值
- **当**省略调用约定**时**，调用约定默认为 `CallingConvention.PlatformDefault`

有关参数：

- 参数名**必须**出现
- **允许**在参数类型可由期望的函数类型推断时省略参数类型（见 [参数](#72-参数)）
- **允许**参数携带 `#` 编译期常量约定；该参数在函数体内是编译期绑定（见 [参数](#72-参数)、[编译期常量参数](#105-编译期常量参数)）
- 参数类型**允许**使用 [标识符定义简写](#15-标识符定义简写)
- **允许**参数名被在函数体内部定义的名称遮蔽（见 [遮蔽](#54-遮蔽)）
- **若**名称 `this` **未**被遮蔽（见 [遮蔽](#54-遮蔽)），**则**允许经成员访问表达式直接访问其成员（见 [成员访问表达式](#352-成员访问表达式)）
  - **允许** this 参数访问其类型的私有成员，就像目标类型的成员一样
  - this 参数的行为由被调用方决定，与调用方无关

有关捕获：

- **若**捕获目标为值类型（见 [值类型](#23-值类型)）实例，**则**捕获时复制数据
- **若**捕获目标为引用类型（见 [引用类型](#24-引用类型)）实例，**则**捕获时复制引用
- 捕获发生在当前函数字面量所在表达式被求值时

有关语法糖：

- 有关数组参数展开语法糖，见 [数组类型构造器](#262-数组类型构造器)
- 有关函数定义语法糖，见 [函数定义语法糖](#71-函数定义语法糖)

例如：

```novasharp
// 定义：无参函数
constant GetAnswer(): integer(4) =
    () integer(4) =>
    {
        return 42;
    };

// 定义：多参函数
constant Add(a: integer(4), b: integer(4)): integer(4) =
    (a: integer(4), b: integer(4)) integer(4) =>
    {
        return a + b;
    };

// 定义：显式调用约定
constant CCallback(; CDeclaration): integer(4) =
    (; CDeclaration) integer(4) =>
    {
        return 0;
    };

// 示例：按值捕获
// 定义：函数 CaptureByValue（通过函数定义语法糖）
constant CaptureByValue()
{
    variable threshold: integer(4) = 10;

    constant IsAbove(value: integer(4)): boolean =
        (value: integer(4)) boolean =>
        {
            // threshold 是值类型，捕获时复制数据
            return value > threshold; // 参与比较的是一份 threshold 的副本
        };

    threshold = 99; // 不会修改 IsAbove 中的副本
    variable result: boolean = IsAbove(5); // result = false
}

// 定义：类 Counter（引用类型）
class Counter
{
    public Count: integer(4);
}

// 示例：按引用捕获
// 定义：函数 CaptureByReference（通过函数定义语法糖）
constant CaptureByReference()
{
    variable counter: Counter = Counter();
    counter.Count = 5;

    constant GetCount(): integer(4) =
        () integer(4) =>
        {
            // counter 是引用类型，捕获时复制引用
            return counter.Count; // 访问的是对 counter 的引用副本，该副本仍然指向 counter
        };

    counter.Count = 20; // 修改同一个实例的 Count 成员
    variable result: integer(4) = GetCount(); // result = 20
}

// 示例：this 参数
class Calculator
{
    private OffsetPointer: pointer integer(4);

    extension
    {
        // 定义：函数 CreateGetter
        public constant CreateGetter(this: Calculator): function() integer(4) =
            (this: Calculator) function() integer(4) =>
            {
                return () integer(4) => { return *(this.OffsetPointer); };
            };
    }

    // 非法：参数列表中出现两个 this
    // extension
    // {
    //     constant Bad: function(this: Calculator, this: Calculator) =
    //         (this: Calculator, this: Calculator) =>
    //         { }
    // }
    // 错误：this 在参数列表中最多出现一次
}

// 定义：函数 CreateGetterByInstance
public constant CreateGetterByInstance(instance: Calculator): function() integer(4) =
        (this: Calculator) function() integer(4) =>
        {
            // 调用者只负责传值
            // 调用者和被调用者的参数名称不同，不影响函数类型和调用行为
            // 被调用者依然可以正常以 this 参数的方式访问 Calculator 实例
            return () integer(4) => { return *(this.OffsetPointer); };
        };
```

#### 1.7.11 无穷值

**无穷值字面量**是 IEEE 754 正无穷大的字面量表示，其格式如下：

```ebnf
InfiniteLiteral = "infinite" .
```

有关类型：

- 无穷值字面量的类型**必须**为浮点类型（见 [基本类型](#22-基本类型)）
- 上述浮点类型**必须**由编译器根据语句上下文推断
- **若**推断失败，**则**编译器**必须**报错
- 无穷值字面量的值**必须**为 IEEE 754 正无穷大

有关取负：

- **允许**对无穷值字面量使用一元 `-`，以表示 IEEE 754 负无穷大（见 [取负表达式](#3104-取负表达式)）

有关比较：

- 无穷值的比较**必须**遵循 IEEE 754（见 [基本类型](#22-基本类型)）

例如：

```novasharp
// 合法：以无穷值字面量产生正无穷
variable upper: float(4) = infinite;

// 合法：以一元取负产生负无穷
variable lower: float(4) = -infinite;

// 合法：无穷参与比较
variable bigger: boolean = upper > lower; // true

// 非法：省略类型上下文导致推断失败
// variable unknown = infinite;
// 错误：无穷值字面量的类型必须由编译器根据语句上下文推断
```

#### 1.7.12 非法值

**非法值字面量**是 IEEE 754 非数的字面量表示，其格式如下：

```ebnf
IllegalLiteral = "illegal" .
```

有关类型：

- 非法值字面量的类型**必须**为浮点类型（见 [基本类型](#22-基本类型)）
- 上述浮点类型**必须**由编译器根据语句上下文推断
- **若**推断失败，**则**编译器**必须**报错
- 非法值字面量的值**必须**为 IEEE 754 非数

有关比较：

- **禁止**将非法值字面量用作相等表达式、不等表达式、大于表达式、小于表达式、大于等于表达式**或**小于等于表达式的操作数（见 [运算符重载](#3103-运算符重载)）
- 判定浮点值是否为非数**必须**经 `is` 表达式（见 [is 表达式](#39-is-表达式)）
- 非数**不得**与任何值相等，包括其自身（见 [基本类型](#22-基本类型)）

例如：

```novasharp
// 合法：以非法值字面量产生非数
variable ratio: float(4) = illegal;

// 合法：经 is 表达式判定非数
variable bad: boolean = ratio is illegal;

// 非法：将非法值字面量用作比较操作数
// variable never: boolean = ratio == illegal;
// 错误：禁止将非法值字面量用作比较表达式的操作数

// 非法：省略类型上下文导致推断失败
// variable unknown = illegal;
// 错误：非法值字面量的类型必须由编译器根据语句上下文推断
```

#### 1.7.13 未初始化

**未初始化字面量**是存储的未初始化表示，其格式如下：

```ebnf
UninitializedLiteral = "uninitialized" .
```

其中：

- **定义** `UninitializedLiteral` 为未初始化字面量
- **定义**未初始化值为内存原有的数据（见 [内存分配](#111-内存分配)）
- `uninitialized` **必须仅**作为存储定义的初始值（见 [变量](#43-变量)、[字段](#281-字段)、[堆分配](#45-堆分配)、[访问器](#282-访问器)）
- **判定**未初始化字面量在语法上为初始值

有关类型：

- 未初始化字面量的类型**必须**由编译器根据语句上下文推断
- **若**推断失败，**则**编译器**必须**报错

有关行为：

- 未初始化字面量**必须**产生未初始化值
- 未初始化字面量**不得**写入任何存储
- **当**存储以未初始化字面量作为初始值**时**，该存储**允许**在赋值之前被读取（见 [内存分配](#111-内存分配)）

> [!NOTE] 语法上是初始值，语义上是存储原有数据
> 未初始化字面量占据初始值的位置，并产生未初始化值；该值即内存原有的数据，且不写入任何存储，故不构成初始化。

例如：

```novasharp
// 合法：显式请求未初始化存储，并读取未初始化值
variable seed: integer(4) = uninitialized;
variable entropy: integer(4) = seed;

// 合法：赋值后调用
variable callback() = uninitialized;
callback = () => { };

// 非法：作为常量初始值
// constant bad: integer(4) = uninitialized;
// 错误：uninitialized 不得作为常量的初始值
```

### 1.8 语句终止

**语句终止符**是用于分隔语句的字符集合。

语句终止符由以下**任一**字符组成：

- 分号：`;`
- 后大括号：`}`

其中：

- **判定**分号为语句终止符，**当且仅当**满足如下**所有**条件：
  - **未**处于泛型上下文中
- **判定**后大括号为语句终止符，**当且仅当**满足如下**所有**条件：
  - 在同一行中，后大括号之后**必须**仅包含空白字符（见 [空白与行终止](#12-空白与行终止)）和（或）注释（见 [注释](#13-注释)）
  - 在源代码文本文件（见 [源代码文本文件](#11-源代码文本文件)）中，**不得**处于任何表达式或未完成语句的内部
  - 在源代码文本文件（见 [源代码文本文件](#11-源代码文本文件)）中，**不得**紧邻不完整的语句

有关适用：

- 语句终止符**必须**用于代码块（见 [代码块](#42-代码块)）内的语句
- 语句终止符**必须**用于类型体成员与扩展块成员

例如：

```novasharp
// 定义：类 Counter
class Counter
{
    // 合法：分号终止
    private Count: integer(4);

    extension
    {
        // 合法：后大括号终止，其后仅包含空白与注释
        public constant Value(): integer(4) { return Count; }
    }
}

// 非法：后大括号之后存在其它内容
// class Bad { } class Another { }
// 错误：后大括号之后仅可包含空白字符和（或）注释
```

### 1.9 语义映射表

**语义映射表**是 NovaSharp 中关键字与符号的语义对照表。

NovaSharp 中的部分关键字与符号拥有其专门的**语义**。它们按照下表映射：

| 项              | 语义                                            |
| --------------- | ----------------------------------------------- |
| `class`         | 类                                              |
| `structure`     | 结构                                            |
| `interface`     | 接口；约定                                      |
| `enumeration`   | 枚举；标识符-值映射                             |
| `variant`       | 变体；拥有多种形态的值                          |
| `union`         | 共同体；共用内存空间                            |
| `module`        | 模块                                            |
| `variable`      | 当前作用域内的变量                              |
| `constant`      | 常量                                            |
| `accessor`      | 访问器                                          |
| `allocate`      | 堆分配并构造                                    |
| `operator`      | 运算符                                          |
| `extension`     | 为类型追加成员的声明                            |
| `import`        | （将成员）导入（当前作用域）                    |
| `array`         | 数组                                            |
| `function`      | 函数                                            |
| `pointer`       | 指针                                            |
| `public`        | 公共的                                          |
| `private`       | 声明所在作用域内可见的                          |
| `protected`     | 声明所在作用域及其派生类型可见的                |
| `scoped`        | 可被指定目标访问的                              |
| `readonly`      | （内容确定后）只读的                            |
| `implicitable`  | 允许隐式                                        |
| `verbatim`      | 不进行任何优化                                  |
| `linkable`      | 符号对外可见的                                  |
| `abstract`      | 抽象类                                          |
| `virtual`       | 虚拟的，可被 `override` 的                      |
| `override`      | 覆写                                            |
| `sealed`        | 密封的，不允许被继承的                          |
| `aligned`       | 对齐                                            |
| `static`        | 静态的；与类型关联的；不依赖实例的              |
| `if`            | 如果                                            |
| `else`          | 否则                                            |
| `while`         | 当                                              |
| `do`            | 先执行，再……                                    |
| `for`           | 对于                                            |
| `in`            | 属于                                            |
| `match`         | 匹配                                            |
| `case`          | 情况                                            |
| `break`         | 打破                                            |
| `continue`      | 尝试从下一次/下一个的开头处继续（如果条件满足） |
| `return`        | 返回；携带值返回                                |
| `throw`         | 抛出一个值                                      |
| `trap`          | 拦截                                            |
| `catch`         | 尝试接住抛出的值                                |
| `finally`       | 最终块；控制流退出前执行的最后代码              |
| `manual`        | `allocate` 的后缀标记                           |
| `dispose`       | 销毁                                            |
| `this`          | 当前处理的                                      |
| `owner`         | 所有者；父                                      |
| `base`          | 基类成员访问                                    |
| `basic`         | 基本类型种类                                    |
| `ascii`         | ASCII 编码                                      |
| `utf8`          | UTF-8 编码                                      |
| `utf16`         | UTF-16 编码                                     |
| `utf32`         | UTF-32 编码                                     |
| `ucs2`          | UCS-2 编码                                      |
| `ucs4`          | UCS-4 编码                                      |
| `wildcard`      | 通配符                                          |
| `true`          | 真；条件成立                                    |
| `false`         | 假；条件不成立                                  |
| `illegal`       | 非数                                            |
| `infinite`      | 正无穷                                          |
| `uninitialized` | 未初始化的                                      |
| `is`            | 判定                                            |
| `when`          | 匹配分支的守卫条件                              |
| `Cast`          | 类型转换                                        |
| `integer`       | 整数类型                                        |
| `unsigned`      | 无符号整数类型前缀                              |
| `float`         | 浮点类型                                        |
| `boolean`       | 布尔类型                                        |
| `@`             | 原来的，原本的                                  |
| `:`             | 标记                                            |
| `&`             | 引用；按位与；引用标记                          |
| `*`             | 乘法；解引用                                    |
| `??`            | 空值合并；决策                                  |
| `^`             | 按位异或；按位取反                              |
| `..`            | 左闭右闭区间                                    |
| `..!`           | 左闭右开区间                                    |
| `+=`            | 加赋值                                          |
| `-=`            | 减赋值                                          |
| `*=`            | 乘赋值                                          |
| `/=`            | 除赋值                                          |
| `%=`            | 求余赋值                                        |
| `\|=`           | 按位或赋值                                      |
| `&=`            | 按位与赋值                                      |
| `^=`            | 按位异或赋值                                    |
| `<<=`           | 逻辑左移赋值                                    |
| `>>=`           | 逻辑右移赋值                                    |
| `#`             | 编译期执行前缀                                  |

## 2. 类型

### 2.1 类型构造语法

**类型构造语法**是构造类型的形式，其格式如下：

```ebnf
Type = ConstructedType | BasicType | Identifier | MonomorphizationExpression .
```

其中：

- **定义** `Type` 为类型
- 有关 `ConstructedType`，见 [类型构造器](#261-类型构造器)
- **定义** `BasicType` 为基本类型（见 [基本类型](#22-基本类型)）
- **定义** `Identifier` 为类型标识符（见 [标识符](#14-标识符)）
  - 类型标识符**必须**指向类型
- 有关 `MonomorphizationExpression`，见 [单态化表达式](#92-单态化表达式)

有关语法：

- 类型构造语法**必须**为前缀、右结合的
- 类型构造器的目标类型**必须**位于类型构造器之后（见 [类型构造器](#261-类型构造器)）

有关泛型：

- 泛型参数**不得**出现在类型中，**仅允许**出现在声明中（见 [泛型参数](#91-泛型参数)）
- **当**类型需要携带泛型实参**时**，泛型实参**必须**经单态化表达式携带（见 [单态化表达式](#92-单态化表达式)）

例如：

```novasharp
// 合法：基本类型
variable x: integer(4);

// 合法：构造类型
variable arr: array(5) integer(4);

// 合法：嵌套构造类型
variable table: array(3) array(4) boolean;

// 合法：函数类型
variable f: function(value: integer(4));

// 合法：带泛型实参的类型
variable box: Box<integer(4)>;

// 非法：泛型参数出现在类型中
// variable bad: <T> function(value: T) T;
// 错误：泛型参数仅允许出现在声明中
```

### 2.2 基本类型

**基本类型**是 NovaSharp 内置的基础数据类型，其格式如下：

```ebnf
BasicType = IntegerType
          | UnsignedIntegerType
          | FloatType
          | BooleanType .

IntegerType         = "integer" "(" IntegerLiteral ")" .
UnsignedIntegerType = "unsigned" IntegerType .
FloatType           = "float" "(" IntegerLiteral ")" .
BooleanType         = "boolean" .
```

其中：

- **定义** N 为 `IntegerLiteral` 的值
  - 有关 `IntegerLiteral`，见 [整数](#172-整数)
- **定义** `IntegerType` 为整数类型
  - 整数类型的 N **必须为** 1、2、4、8 或 16
  - **若**平台不支持某些值，**则**编译器**必须**模拟
- **定义** `unsigned` 为无符号类型前缀
- **定义** `UnsignedIntegerType` 为无符号整数类型
  - 无符号整数类型的 N **必须为** 1、2、4、8 或 16
  - **若**平台不支持某些值，**则**编译器**必须**模拟
- **定义** `FloatType` 为 IEEE 754 浮点类型
  - 浮点类型的 N **必须为** 4 或 8
  - **若**平台不支持某些值，**则**编译器**必须**模拟
- **定义** `BooleanType` 为布尔类型
- 基本类型的括号**不得**省略
  - **若**省略括号，**则**不被识别为基本类型

有关 N：

- N 的单位**必须为**字节
- 整数类型、无符号整数类型和浮点类型的内存大小为 N

有关浮点类型：

- 浮点类型**必须**遵循 IEEE 754 标准
- 浮点运算的精度**不得**高于运算数类型的精度

有关布尔类型：

- 布尔类型的内存大小**必须为** 1 字节

有关运算符重载：

- 语言内置重载**必须**覆盖整数类型和无符号整数类型的全部八个二元运算符和取负
  - 整数类型为 `integer(1)`、`integer(2)`、`integer(4)`、`integer(8)`、`integer(16)`
  - 无符号整数类型为 `unsigned integer(1)`、`unsigned integer(2)`、`unsigned integer(4)`、`unsigned integer(8)`、`unsigned integer(16)`
- 语言内置重载**必须**覆盖浮点类型的全部八个二元运算符和取负
  - 浮点类型为 `float(4)`、`float(8)`
- 语言内置重载**必须**覆盖布尔类型的相等运算符；**禁止**覆盖布尔类型的其余运算符
- 基本类型的算术语言内置重载的签名**必须为** `function(left: T, right: T) T`
- 基本类型的比较语言内置重载的签名**必须为** `function(left: T, right: T) boolean`
- 上述重载**必须**由编译器固有提供，**不得**以运算符定义书写（见 [运算符](#3101-运算符)）
- 上述重载**不得**由 Built-In Library 提供（见 [Built-In Library 完整内容](#152-built-in-library-完整内容)）

有关行为：

- 整数类型的溢出行为**必须为**回绕
- 整数类型的除法**必须**向零截断
- 整数类型的求余的符号**必须**跟随左操作数
- **当**整数类型的除法**或**求余的右操作数为 `0` **时**，**必须**产生 `DivideByZeroException` 运行时异常（见 [异常处理](#491-异常处理)）
- 逻辑左移和逻辑右移的计数**必须**按左操作数类型的位宽取模
- 浮点运算的舍入**必须**为就近偶数
- 浮点类型的比较**必须**遵循 IEEE 754，其中非数与任何值都不相等，包括其自身
- 浮点类型的除法**必须**遵循 IEEE 754，其中除数为 `0` 时得无穷或非数，**不得**产生 `DivideByZeroException`
- 整数类型和无符号整数类型的取负**必须**遵循回绕
- 浮点类型的取负**必须**遵循 IEEE 754，其中 `-infinite` 为负无穷

有关类型转换：

- 基本类型间的类型转换**必须为**数值转换
- 基本类型之间**不得**存在隐式转换（见 [核心设计哲学](#141-核心设计哲学)）
- **允许**基本类型之间**互相显式**转换
- **当**从浮点类型转换为整数类型**且**其值超出该整数类型的范围**时**，**必须**回绕
- **当**转换为布尔类型**时**，值为 `0` 的源值**必须**转换为 `false`，其余源值**必须**转换为 `true`
- **当**从布尔类型转换**时**，`false` **必须**转换为 `0`，`true` **必须**转换为 `1`

例如：

```novasharp
// 合法：整数类型
variable integer32: integer(4) = 42;

// 合法：无符号整数类型
variable uinteger8: unsigned integer(1) = 255;

// 合法：浮点类型
variable float64: float(8) = 3.14159;

// 合法：布尔类型
variable flag: boolean = true;

// 合法：空类型作为函数返回类型
variable DoNothing() = () => { };

// 合法：显式转换为浮点
variable i: integer(4) = 100;
variable f: float(8) = Cast<float(8)>(i);

// 合法：显式转换为布尔
variable zero: integer(4) = 0;
variable b: boolean = Cast<boolean>(zero); // false

// 非法：省略括号
// variable bad: integer = 42;
// 错误：不被识别为基本类型

// 非法：不支持的 N 值
// variable bad: integer(3) = 42;
// 错误：N 不合法

// 非法：float 不支持的 N 值
// variable bad: float(16) = 1.0;
// 错误：N 不合法

// 非法：整数隐式转换为浮点
// variable bad: float(4) = i;
// 错误：基本类型之间不得存在隐式转换

// 非法：整数隐式转换为布尔
// variable bad: boolean = zero;
// 错误：基本类型之间不得存在隐式转换
```

### 2.3 值类型

**值类型**是标识符直接持有实例本体的类型，由以下特征组成：

- 标识符直接持有实例的原始内存
- 赋值操作复制实例本体

其中：

- **定义**值类型为标识符直接持有实例本体的类型
- 值类型的标识符赋值操作**必须**复制实例本体
- 有关赋值，见 [赋值语句](#46-赋值语句)

### 2.4 引用类型

**引用类型**是标识符存储实例引用的类型，由以下特征组成：

- 标识符存储引用，引用指向实例本体
- 赋值操作复制引用，而非实例本体

其中：

- **定义**引用类型为标识符存储实例引用的类型
- 引用类型的标识符赋值操作**必须**复制引用
- 有关赋值，见 [赋值语句](#46-赋值语句)
- 更多，见 [引用](#25-引用)

### 2.5 引用

**引用**是对实例本体的间接访问机制（见 [引用类型](#24-引用类型)）。

其中：

- **定义**引用为隐式指针
- **定义**引用实例为引用所指向的实例
- 引用在内存布局上为指向实例本体的指针
- 引用在语法上被视为实例本体
- 引用的类型在语法上被视为实例本体的类型
- **允许**多个引用指向同一实例

有关引用类型：

- **当**引用引用类型实例**时**，引用直接指向实例本体

> [!NOTE] 不存在指向引用的引用
> 只有指向引用的指针（见 [指针类型构造器](#263-指针类型构造器)）

有关操作：

- 对引用的操作**必须**映射为对实例本体的操作
- 引用**不得**被显式解引用
- 有关赋值，见 [引用类型](#24-引用类型)、[赋值语句](#46-赋值语句)

例如：

```novasharp
// 定义：类 Counter
class Counter
{
    public Count: integer(4);
}

// 合法：标识符存储引用，引用指向实例本体
variable counter: Counter = Counter();

// 合法：多个引用指向同一实例
variable another: Counter = counter;

// 合法：对引用的操作映射为对实例本体的操作
another.Count = 5; // counter.Count 亦为 5

// 非法：显式解引用
// (*counter).Count = 5;
// 错误：引用不得被显式解引用
```

### 2.6 类型构造器

#### 2.6.1 类型构造器

**类型构造器**是构造复合类型的语法形式，用于将基本类型或已有类型扩展为新类型，其格式如下：

```ebnf
ConstructedType = TypeConstructor [ ConstructTargetType ] .

TypeConstructor = ArrayTypeConstructor
                | FunctionTypeConstructor
                | PointerTypeConstructor .

ConstructTargetType = BasicType | Type .
```

其中：

- **定义** `ConstructedType` 为构造后的复合类型
- **定义** `TypeConstructor` 为类型构造器
- **定义** `ConstructTargetType` 为类型构造器的目标类型
- **定义**空类型为省略 `ConstructTargetType` 时所得的类型
- **定义** `Type` 为任意类型（见 [类型构造语法](#21-类型构造语法)）

有关类型构造器：

- `TypeConstructor` **必须**为上列三个类型构造器之一
- 有关数组类型构造器，见 [数组类型构造器](#262-数组类型构造器)
- 有关函数类型构造器，见 [函数类型构造器](#264-函数类型构造器)
- 有关指针类型构造器，见 [指针类型构造器](#263-指针类型构造器)

有关目标类型：

- 数组类型构造器**必须**携带 `ConstructTargetType`（见 [数组类型构造器](#262-数组类型构造器)）
- 函数类型构造器与指针类型构造器**允许**省略 `ConstructTargetType`（见 [函数类型构造器](#264-函数类型构造器)、[指针类型构造器](#263-指针类型构造器)）
- 空类型**无**内存布局
- 空类型**无**书写形式
- 空类型**不得**作为变量类型（见 [变量](#43-变量)）
- 空类型**不得**作为字段类型（见 [字段](#281-字段)）
- 空类型**仅**用于函数返回、指针目标与变体状态载荷（见 [变体](#275-变体)）

有关访问器：

- 访问器（见 [访问器](#282-访问器)）**不得**作为类型构造器的目标类型

#### 2.6.2 数组类型构造器

**数组类型构造器**是构造数组类型的语法形式，数组类型是值类型（见 [值类型](#23-值类型)），用于表示固定长度的同类型元素序列，其格式如下：

```ebnf
ArrayTypeConstructor = "array(" Expression { "," Expression } ")" .
```

其中：

- **定义** `Expression` 为数组大小表达式（见 [表达式](#31-表达式)）
  - 数组大小表达式的类型**必须为**无符号整数类型**或**可隐式转换为无符号整数类型
- **定义** N 为数组大小表达式的值
- **定义** N 为数组大小

有关数组类型：

- **定义**元素类型为 `ConstructTargetType`（见 [类型构造器](#261-类型构造器)）
- 数组大小**必须**为编译期可确定的值，**但**以下情况除外：
  - 数组类型构造器出现在函数体中（见 [函数](#1710-函数)）
- 数组大小是编译期元数据
  - 编译期元数据**必须**在编译器的编译产物中被剔除

有关定长数组：

- 定长数组**必须**满足如下**所有**条件：
  - 数组大小为编译期可确定的非负整数
  - 数组大小在编译产物中被剔除（作为元数据）

有关变长数组：

- **定义**变长数组为数组大小非编译期可确定的数组类型
- 变长数组**仅**可出现在函数体内部
- **禁止**变长数组作为函数返回值
- **当**变长数组作为类型声明**时**，等价于由指针在前、长度在后组成的结构体
  - 上述等价结构的指针**必须**指向数组首元素
  - 上述等价结构的长度**必须**为数组大小表达式的返回值
- 变长数组**不得**作为类型比较的目标

> [!NOTE] 变长数组的用途
> 变长数组解决的是在运行期分配动态大小内存的问题；数组大小在编译期已知时，定长数组即可。

有关类型相等：

- **判定**数组类型 `F` 与数组类型 `L` 相等，**当且仅当**满足如下**所有**条件：
  - `F` 和 `L` 的数组大小相同
  - `F` 和 `L` 的元素类型相同

有关类型转换：

- **允许**数组类型**单向显式**转换为指针类型
  - 指针的目标类型**必须为**数组的元素类型
  - 指针指向数组的首元素
- **允许**指针类型**单向显式**转换为定长数组类型
  - 指针的目标类型**必须为**数组的元素类型
  - 转换后的数组**必须**引用指针所指向的连续元素
- **禁止**指针类型转换为变长数组类型
- **允许**定长数组之间**互相显式**转换
  - 转换不受数组大小限制
- **允许**变长数组之间**互相显式**转换
- **允许**变长数组**单向显式**转换为定长数组
- **当**指针类型转换为数组类型**时**，编译器**不得**校验数组大小，**并\*\***应当\*\*予以 Warning

有关语法糖：

- **定义**数组聚合语法糖为多维数组类型的简写形式
  - `array(X) array(Y) T` 等价于 `array(X, Y) T`
  - 该语法糖可递归应用
- **定义**数组参数展开语法糖为函数参数列表中数组类型的简写形式
  - 语法糖 `array(Name: Type) T` 等价于参数 `Name: Type`与 `pointer T`
    - `Type` **必须为**无符号整数类型（见 [基本类型](#22-基本类型)）
    - 展开顺序**必须为**先指针后长度
  - 上述语法糖**仅**适用于函数类型构造器（见 [函数类型构造器](#264-函数类型构造器)）与函数字面量（见 [函数](#1710-函数)）的参数列表
  - **当**数组为多维数组**时**，**仅允许**展开第一维
- 有关数组定义简写，见 [标识符定义简写](#15-标识符定义简写)

例如：

```novasharp
// 合法：基本数组
variable arr: array(5) integer(4);

// 合法：多维数组
variable matrix: array(3, 4) boolean;
// 等价于：array(3) array(4) boolean

// 合法：数组定义简写与数组参数展开语法糖叠加
// 数组定义简写展开为 message: array(length: unsigned integer(4)) unsigned integer(1)
constant LogNote(message[length: unsigned integer(4)]: unsigned integer(1))
{
}

// 合法：数组显式转指针
variable p: pointer integer(4) = Cast<pointer integer(4)>(arr);

// 合法：指针显式转定长数组
variable back: array(5) integer(4) = Cast<array(5) integer(4)>(p);

// 非法：数组大小为负
// variable bad: array(-1) integer(4);
// 错误：数组大小必须为非负整数
```

#### 2.6.3 指针类型构造器

**指针类型构造器**是构造指针类型的语法形式，指针类型是值类型（见 [值类型](#23-值类型)），用于表示对内存地址的引用，其格式如下：

```ebnf
PointerTypeConstructor = "pointer" .
```

有关指针类型：

- **定义**目标类型为 `ConstructTargetType`（见 [类型构造器](#261-类型构造器)）
- 指针类型的内存大小由平台决定

有关目标类型：

- 目标类型指示指针以何种类型访问所指向的内存地址

有关类型转换：

- **允许**不同目标类型的指针类型之间**互相显式**转换
  - 该转换只修改目标类型，不修改所指向的内存地址的值
- **当**指针类型之间显式转换**时**，编译器**应当**予以 Warning

有关解引用：

- **当**省略目标类型**时**，**不得**对该指针进行解引用

有关指针算术：

- 指针类型的语言内置重载**必须**覆盖加法与减法（见 [运算符重载](#3103-运算符重载)）
- 指针与整数的加法和减法的结果为指针类型
- 两个指针的减法的结果为元素个数
- 加减法的单位**必须为** `Type.SizeOf<T>()`（见 [编译器 API](#107-编译器-api)），其中 `T` 为目标类型
- **当**省略目标类型**时**，单位**必须为** 1 字节

例如：

```novasharp
// 合法：基本指针
variable p: pointer integer(4);

// 合法：省略目标类型的指针
variable raw: pointer;

// 合法：指针类型转换
variable pf: pointer float(4) = Cast<pointer float(4)>(p);

// 非法：省略目标类型的指针解引用
// variable pv: pointer;
// variable x: integer(4) = *pv;
// 错误：不得对省略目标类型的指针进行解引用
```

#### 2.6.4 函数类型构造器

**函数类型构造器**是构造函数类型的语法形式，函数类型是引用类型（见 [引用类型](#24-引用类型)），用于描述调用方的调用行为，其格式如下：

```ebnf
FunctionTypeConstructor = "function" [ "(" [ ParameterList ] [ ";" CallingConventionExpression ] ")" ] .

ParameterList = Parameters [ "," "wildcard" ] | "wildcard" .

CallingConventionExpression = Expression .
```

其中：

- **定义** `FunctionTypeConstructor` 为函数类型构造器
- 有关 `Parameters`，见 [参数](#72-参数)
- **定义** `ParameterList` 为函数类型构造器的参数列表
- **定义** `CallingConventionExpression` 为调用约定表达式
  - 调用约定表达式是表达式（见 [表达式](#31-表达式)）
- **定义** `wildcard` 为通配符标记，其**允许**匹配参数列表末尾的任意剩余实参
  - 通配符标记是关键字（见 [关键字](#16-关键字)）
  - `wildcard` **必须**仅作为参数列表的最后一项

> [!NOTE] 默认值表达式是调用方行为
> 仅函数类型构造器支持默认值表达式；函数字面量（见 [函数](#1710-函数)）不支持。

有关参数：

- **当** `wildcard` 存在**时**，其之前的部分为固定参数前缀
  - 编译器**必须**校验固定参数前缀对应的实参
  - 编译器**不得**校验 `wildcard` 匹配的剩余实参
- `wildcard` **允许**单独出现，也**允许**跟在 `Parameters` 之后
- `wildcard` **不得**出现在固定参数之前**或**中间
- 参数名**必须**出现，**但**参数名在所在上下文中无用**时**允许省略
  - 参数名需要为函数体绑定名称**时**，参数名**必须**出现（见 [函数定义语法糖](#71-函数定义语法糖)）
- 调用约定表达式**不得**携带参数名，**且**与参数**必须**以分号 `;` 分隔
  - **当**参数列表为空**且**调用约定存在**时**，分号**必须**出现
- 更多，见 [参数](#72-参数)

有关调用约定：

- 调用约定**必须**满足如下**所有**条件：
  - 返回值类型为 `CallingConvention`
  - **必须**可在编译期求值
- **当**省略调用约定**时**，调用约定默认为 `CallingConvention.PlatformDefault`
- `CallingConvention.PlatformDefault` **必须**表示目标平台的默认调用约定
- **定义** `CallingConvention` 为调用约定枚举
  - Built-In Library **必须**在全局作用域下定义调用约定枚举
  - 有关调用约定枚举的定义，见 [Built-In Library 完整内容](#152-built-in-library-完整内容)

有关返回值：

- **定义**函数类型构造器的返回值类型为 `ConstructTargetType`（见 [类型构造器](#261-类型构造器)）
  - 返回值类型**允许**省略
  - **当**省略返回值类型**时**，返回值类型**必须为**空类型
  - **当**省略返回值类型**时**，括号**不得**省略

有关类型相等：

- **判定**函数类型 `F` 与函数类型 `L` 相等，**当且仅当**满足如下**所有**条件：
  - `F` 和 `L` 的固定参数前缀参数数量、顺序和类型相等
  - `F` 和 `L` 的对应参数是否携带 `#` 约定相同
  - `F` 和 `L` 是否携带 `wildcard` 相同
  - `F` 和 `L` 的调用约定相同
  - `F` 和 `L` 的返回值类型相同
- 参数名的有无、默认值表达式与引用标记 `&` **不得**参与类型相等
- 编译期常量参数约定 `#` **必须**参与类型相等
- 推断出的函数类型**必须**保留参数名；类型相等**不得**因此改变

有关类型转换：

- 函数类型间的类型转换**必须仅**改变调用方的调用行为
- **允许**合法函数类型之间**互相显式**转换
  - 转换不受参数列表、调用约定和返回值类型限制
- **禁止**函数类型之间的隐式转换
- **当**函数类型之间显式转换**时**，编译器**应当**予以 Warning

有关语法糖：

- **定义**函数类型构造器括号省略语法糖为：**当**参数列表和调用约定可推断**且**未省略返回值类型**时**省略 `(...)` 部分
- 有关数组参数展开语法糖，见 [数组类型构造器](#262-数组类型构造器)
- 有关函数定义语法糖，见 [函数定义语法糖](#71-函数定义语法糖)

例如：

```novasharp
// 合法：无名参数的类型
variable Callback: function(integer(4));

// 合法：有名参数的类型
variable Named: function(value: integer(4));

// 合法：返回整数
variable Safe: function() integer(4);

// 合法：携带默认值的参数必须携带参数名
variable WithDefault: function(value: integer(4) = 0) integer(4);

// 合法：无名引用参数
variable WithRef: function(&integer(4));

// 合法：有名引用参数
variable NamedRef: function(value: &integer(4));

// 合法：无名编译期常量参数
variable CompileTime: function(#integer(4));

// 合法：有名编译期常量参数
variable NamedCompileTime: function(#value: integer(4));

// 非法：编译期常量参数与普通参数的类型不同
// variable Bad: function(integer(4)) = CompileTime;

// 定义：类 MyClass
// 合法：this 参数
variable WithThis: function(this: MyClass);

// 合法：wildcard 单独作为最后一项
variable AnyArgs: function(wildcard);

// 合法：wildcard 跟在固定参数之后
variable PrefixedAny: function(value: integer(4), wildcard);

// 合法：固定参数前缀与调用约定
variable PrefixedAnyC: function(value: integer(4), wildcard; CDeclaration);

// 合法：显式调用约定
variable Cdecl: function(value: integer(4); CDeclaration);

// 合法：空参数列表与调用约定
variable CdeclEmpty: function(; CDeclaration);

// 合法：将 function(wildcard) 类型转换为 function(boolean) 类型
variable Foo: function(value: boolean) = Cast<function(boolean)>(AnyArgs);
// 危险：该转换不校验目标签名

// 合法：推断出的函数类型保留参数名
// 假设：anotherFunction 为函数常量
variable foo = Cast<function(a: integer(4))>(anotherFunction);
// foo 的类型为 function(a: integer(4))

// 非法：省略参数类型标注
// variable Bad: function(value);
// 错误：函数类型构造器的参数类型必须出现

// 非法：无名参数携带默认值
// variable Bad: function(integer(4) = 0);
// 错误：默认值表达式不得在参数名省略时出现

// 非法：携带默认值表达式的参数后出现无默认值表达式的参数
// variable Bad: function(value: integer(4) = 0, flag: boolean) integer(4);
// 错误：在有默认值参数后发现意外的无默认值参数

// 非法：wildcard 不是最后一项
// variable Bad: function(wildcard, value: integer(4));
// 错误：wildcard 必须仅作为参数列表的最后一项

// 非法：wildcard 位于参数中间
// variable Bad: function(value: integer(4), wildcard, flag: boolean);
// 错误：wildcard 必须仅作为参数列表的最后一项
```

### 2.7 自定义类型

#### 2.7.1 类

**类**是引用类型（见 [引用类型](#24-引用类型)），无默认内存分配方式（见 [内存分配](#111-内存分配)），支持单继承、多接口实现、多态和方法重写，其格式如下：

```ebnf
ClassDeclaration = { Modifier } "class" Name [ GenericParameters ] [ BaseList ] Block .
```

其中：

- **定义** `ClassDeclaration` 为类声明
- **定义** `Modifier` 为修饰符（见 [修饰符](#81-修饰符)）
- **定义** `Name` 为类名（见 [标识符](#14-标识符)）
- 有关 `BaseList`，见 [继承列表](#277-继承列表)
- 有关 `GenericParameters`，见 [泛型参数](#91-泛型参数)
  - **当**被继承或被实现的目标携带泛型实参**时**，该目标**必须**为单态化表达式（见 [单态化表达式](#92-单态化表达式)）
- 有关 `Block`，见 [代码块](#42-代码块)

有关类声明：

- 修饰符列表**必须**位于 `class` 之前
- 类声明的修饰符列表**必须仅**包含：
  - 可访问性修饰符（见 [可访问性修饰符](#82-可访问性修饰符)）
  - `sealed` 修饰符（见 [sealed 修饰符](#812-sealed-修饰符)）
  - `abstract` 修饰符（见 [abstract 修饰符](#811-abstract-修饰符)）
  - `static` 修饰符（见 [static 修饰符](#816-static-修饰符)）
- 类声明体**必须**为声明序列体（见 [代码块](#42-代码块)）
- 类声明体**必须仅**直接包含：
  - 字段定义（见 [字段](#281-字段)）
  - 扩展声明（见 [扩展](#283-扩展)）
  - 模块声明，且该模块**仅**用于标识符整理（见 [模块](#61-模块)）
- 类声明体**不得**直接包含常量、访问器、运算符**或**方法
  - 上述成员**必须**位于扩展块内

有关成员：

- 类成员**必须仅**支持：
  - 可访问性修饰符（见 [可访问性修饰符](#82-可访问性修饰符)）
  - `virtual` 修饰符（仅方法，见 [virtual 修饰符](#813-virtual-修饰符)）
  - `override` 修饰符（仅方法，见 [override 修饰符](#814-override-修饰符)）
  - `static` 修饰符（见 [static 修饰符](#816-static-修饰符)）
  - 成员自身支持的其它修饰符
- 类声明体内**不得**定义变量（见 [变量](#43-变量)）

有关内存布局：

- 以下成员**不得**进入内存布局：
  - `static` 成员（见 [static 修饰符](#816-static-修饰符)）
  - 方法（见 [方法](#74-方法)）
  - 访问器（见 [访问器](#282-访问器)）
- 字段**必须**进入实例内存布局（见 [字段](#281-字段)）
- 类实例**必须**携带类型信息和虚表
- 有关全程序去虚化与元数据最小化，见 [编译优化总则](#1331-编译优化总则)

有关生命周期：

- 实例化时：
  1. 为实例分配内存
  2. 沿继承链从顶端向下初始化成员
  3. 调用构造函数
- 销毁时：
  1. 调用析构函数
  2. 回收内存

有关构造函数：

- **定义**构造函数为名为 `Construct`、返回值类型为空类型的方法
- **定义**静态构造函数为名为 `Construct`、返回值类型为空类型、参数列表为空**且**以 `static` 修饰的常量（见 [static 修饰符](#816-static-修饰符)）
- **当**基类构造函数参数列表非空**或**函数体非空**时**，构造函数**必须**于第一条语句调用基类构造函数
- **当**基类构造函数参数列表非空**或**函数体非空**时**，类**不得**省略构造函数
- 成员初始化**必须**跟随实例的内存分配方式，**不得**指定独立内存分配方式

有关析构函数：

- **定义**析构函数为名为 `Destruct`、返回值类型为空类型、参数列表为空的方法
- 析构函数**允许**抛出
- **当**析构函数抛出**时**，其**必须**终止执行，**且**其后的销毁指令**不得**执行（见 [throw 语句](#493-throw-语句)）
- **当**析构函数未完成**时**，其实例的堆存储**不得**被释放
- **当**实例为作用域存储期**时**，其存储**必须**随栈指针恢复而释放（见 [内存分配](#111-内存分配)）

有关特殊身份：

- 实例构造函数与析构函数**必须**为方法（见 [方法](#74-方法)）
- 实例构造函数与析构函数与普通方法的唯一区别为：在构造/析构时被自动调用
- **当**其所属类型可被构造**或**销毁**时**，实例构造函数与析构函数**必须**具有特殊身份；**否则**它们是普通方法

有关语法糖：

- **定义**默认构造函数语法糖为：**当**类未声明任何构造函数**且**不存在参数列表非空**或**函数体非空的基类构造函数**时**隐式创建具有如下**所有**特性的空构造函数：
  - 名称为 `Construct`
  - 返回值类型为空类型
  - `this` 参数的类型为该类
  - 参数列表为空，调用约定为 `CallingConvention.PlatformDefault`
- **定义**默认析构函数语法糖为当类未声明任何析构函数**且**该类支持析构函数**时**隐式创建具有如下**所有**特性的空析构函数：
  - 名称为 `Destruct`
  - 返回值类型为空类型
  - `this` 参数的类型为该类
  - 参数列表为空，调用约定为 `CallingConvention.PlatformDefault`

有关继承：

- 一个类**必须最多**继承一个类
- 继承目标**必须为**未声明 `sealed` 的类
- **定义**基类为被继承的类
- **定义** `base` 为访问基类成员的标识符
  - `base` 是关键字（见 [关键字](#16-关键字)）
  - **当** `base` 被遮蔽**时**，**允许**使用 `@base` 访问（见 [标识符](#14-标识符)）
  - **当**无歧义**时**，**允许**省略 `base`
- 沿继承链向上访问的基类成员基础可访问性**必须**大于等于 `protected`

有关继承列表：

- **当**包含接口**时**，**必须**实现目标接口（见 [接口](#273-接口)）
- **当**包含类**时**，**必须**继承目标类
- 实现非空接口**时**，类体内**必须**提供一个**或**多个扩展块，共同实现全部接口成员（见 [扩展](#283-扩展)）
- 继承列表**不得**包含当前类自身
- 泛型类被继承或实现**时\*\***必须\*\*经单态化表达式提供泛型实参（见 [单态化表达式](#92-单态化表达式)）

有关方法重写：

- 重写基类虚方法**必须**使用 `override` 修饰符（见 [override 修饰符](#814-override-修饰符)）
- 重写方法**必须**满足如下**所有**条件：
  - 沿继承链往上**不得**出现被密封的、重写同一虚方法的方法
  - 名称与被重写方法相同
  - 类型与被重写方法相同，**但**以下情况除外：
    - `this` 参数的目标类型**允许**协变替换
  - 行为限定修饰符均无、相同或更少
  - 行为激活修饰符均无、相同或更多
  - 优化修饰符均无或相同
  - 可访问性大于等于被重写方法
  - `this` 参数在参数列表中的出现位置相同

有关方法分派：

- **当**通过基类或接口类型的标识符调用虚方法**时**，**必须**执行该标识符所承载实例的实际类型的最具体重写方法
- **当**通过 `base` 访问成员**时**，**必须**执行基类中的实现，**不得**触发动态分派（见 [成员访问表达式](#352-成员访问表达式)）
- **当**调用非虚方法**时**，**必须**执行标识符声明类型中的方法

有关类型转换：

- 类的类型转换**必须**仅进行类型重解释，不改变实例内容
- **允许**基类与派生类之间**互相显式**转换
- **允许**派生类**单向隐式**转换为基类

有关 `Object` 类：

- **定义** `Object` 为特殊的抽象类
- 未声明继承的类**必须**隐式继承自 `Object`
- `Object` 的 `base` 标识符**必须**持有自身引用
- Built-In Library **必须**在全局作用域下定义 `Object` 类
- 有关 `Object` 类的定义，见 [Built-In Library 完整内容](#152-built-in-library-完整内容)

例如：

```novasharp
// 合法：抽象类
abstract class Animal
{
    extension
    {
        public virtual constant Speak(this: Animal)
        {

        }
    }
}

// 合法：继承与重写
class Cat: Animal
{
    extension
    {
        public override constant Speak(this: Cat)
        {
            // 合法：绕过分派，调用基类方法
            base.Speak();
        }
    }
}

// 合法：密封类
sealed class Ragdoll: Cat
{
    extension
    {
        public override constant Speak(this: Ragdoll)
        {

        }
    }
}

// 合法：隐式继承 Object
class Simple
{

}

// 定义：函数 Main
constant Main(): integer(4)
{
    // 合法：动态分派
    variable animal: Animal = Cat();
    animal.Speak(); // 执行 Cat.Speak

    return 0;
}

// 非法：继承密封类
// class Bad: Ragdoll { }
// 错误：不得继承 sealed 类

// 非法：未提供泛型实参
// class Bad: Box { }
// 错误：泛型类被继承时必须提供泛型实参

// 非法：重写方法类型不匹配
// class Bad: Animal
// {
//     extension
//     {
//         public override constant Speak: function(this: Bad) integer(4) { return 0; }
//     }
// }
// 错误：重写方法类型必须与被重写方法相同

// 非法：类声明体内定义变量
// class Bad
// {
//     public variable X: integer(4);
// }
// 错误：类声明体内不得定义变量，必须使用字段定义
```

#### 2.7.2 结构体

**结构体**是值类型（见 [值类型](#23-值类型)），无默认内存分配方式（见 [内存分配](#111-内存分配)），其格式如下：

```ebnf
StructureDeclaration = { Modifier } "structure" Name [ GenericParameters ] Block .
```

其中：

- **定义** `StructureDeclaration` 为结构体声明
- **定义** `Modifier` 为修饰符（见 [修饰符](#81-修饰符)）
- **定义** `Name` 为结构体名（见 [标识符](#14-标识符)）
- 有关 `GenericParameters`，见 [泛型参数](#91-泛型参数)
- 有关 `Block`，见 [代码块](#42-代码块)

有关结构体声明：

- 修饰符列表**必须**位于 `structure` 之前
- 结构体声明的修饰符列表**必须仅**包含：
  - 可访问性修饰符（见 [可访问性修饰符](#82-可访问性修饰符)）
  - `aligned(N)` 修饰符（见 [aligned(N) 修饰符](#815-alignedn-修饰符)）
- 结构体**不得**携带继承列表
- 结构体**不得**实现接口（见 [接口](#273-接口)）
- 结构体声明体**必须**为声明序列体（见 [代码块](#42-代码块)）
- 结构体声明体**必须仅**直接包含：
  - 字段定义（见 [字段](#281-字段)）
  - 扩展声明（见 [扩展](#283-扩展)）
  - 模块声明，且该模块**仅**用于标识符整理（见 [模块](#61-模块)）
- 结构体声明体**不得**直接包含常量、访问器、运算符**或**方法
  - 上述成员**必须**位于扩展块内

有关成员：

- 结构体成员**必须仅**支持：
  - 可访问性修饰符（见 [可访问性修饰符](#82-可访问性修饰符)）
  - `aligned(N)` 修饰符（见 [aligned(N) 修饰符](#815-alignedn-修饰符)）
  - `static` 修饰符（见 [static 修饰符](#816-static-修饰符)）
  - 成员自身支持的其它修饰符
- 结构体成员**不得**以 `virtual` 修饰（见 [virtual 修饰符](#813-virtual-修饰符)）
- 结构体声明体内**不得**定义变量（见 [变量](#43-变量)）

有关内存布局：

- 以下成员**不得**进入内存布局：
  - `static` 成员（见 [static 修饰符](#816-static-修饰符)）
  - 方法（见 [方法](#74-方法)）
  - 访问器（见 [访问器](#282-访问器)）
- 字段**必须**进入实例内存布局（见 [字段](#281-字段)）
- 结构体**不得**携带虚表**或**运行时类型标识
- 结构体内存**必须**严格按照成员定义顺序布局
- 结构体声明的 `aligned(N)` 仅改变字段的默认对齐与偏移计算，**不得**改变字段顺序
- 成员对齐**必须**遵循如下规则：
  - **当**结构体声明 `aligned(N)` **时**，全部字段默认按 N 字节对齐
  - **否则**默认按成员类型大小对齐
  - **当**字段声明 `aligned(M)` **时**，**必须**按 M 字节对齐，覆盖结构体的默认对齐
  - **当**结构体声明的 N 为 0 **时**，全部字段默认按 0 字节对齐，形成紧凑布局
- **定义**结构体大小为能容纳全部成员的最小大小
  - 上述大小**必须为**所有成员的非零对齐要求的倍数
- **定义**结构体中的数组为固定大小的内联数组
  - 数组元素**必须**分配连续内存空间

有关生命周期：

- 实例化时：
  1. 为实例分配内存
  2. 初始化成员
  3. 调用构造函数
- 销毁时：
  1. 调用析构函数
  2. 回收内存

有关成员初始化：

- **当**初始化**时**，**必须**计算成员的初始化表达式，**并**将成员赋值为各自的初始化值
- 编译器**必须**调整初始化顺序
  - **当**上述调整失败**时**，编译器**必须**报 Warning
- 成员初始化**必须**跟随实例的内存分配方式，**不得**指定独立内存分配方式

有关构造函数：

- **定义**构造函数为名为 `Construct`、返回值类型为空类型的方法

有关析构函数：

- **定义**析构函数为名为 `Destruct`、返回值类型为空类型、参数列表为空的方法
- 有关析构函数的行为，见 [类](#271-类)

有关语法糖：

- **定义**默认构造函数语法糖为：**当**结构体未声明任何构造函数**时**隐式创建具有如下**所有**特性的空构造函数：
  - 名称为 `Construct`
  - 返回值类型为空类型
  - `this` 参数的类型为该结构体
  - 参数列表为空，调用约定为 `CallingConvention.PlatformDefault`
- **定义**默认析构函数语法糖为当结构体未声明任何析构函数**时**隐式创建具有如下**所有**特性的空析构函数：
  - 名称为 `Destruct`
  - 返回值类型为空类型
  - `this` 参数的类型为该结构体
  - 参数列表为空，调用约定为 `CallingConvention.PlatformDefault`

例如：

```novasharp
// 合法：基本结构体
structure Vector2D
{
    public X: float(4) = 0;
    public Y: float(4) = 0;
}

// 合法：紧凑布局结构体
// 全部字段默认按 0 字节对齐
aligned(0) structure Compact
{
    public A: Vector2D;
    public B: Vector2D;
}

// 合法：对齐修饰
structure CEFHeader
{
    public Identifier[4]: integer(1);
    public Type: integer(1);
    public Arch: integer(2);
    public Offset: pointer integer(1);
    public aligned(4) Length: integer(4);
}

// 合法：泛型结构体
structure Box<T>
{
    public Value: T;
}

// 合法：值类型方法，this 参数必须为引用
structure Counter
{
    private _count: integer(4);

    extension
    {
        public constant Increment(this: &Counter)
        {
            this._count = this._count + 1;
        }
    }
}

// 非法：结构体继承
// structure Bad: Vector2D { }
// 错误：结构体不得携带继承列表

// 非法：结构体包含虚方法
// structure Bad
// {
//     extension
//     {
//         public virtual constant Foo: function(this: &Bad) { }
//     }
// }
// 错误：结构体成员不得以 virtual 修饰
```

#### 2.7.3 接口

**接口**是对扩展内容的 API 契约，必须仅被 `class` 实现，其格式如下：

```ebnf
InterfaceDeclaration = { Modifier } "interface" Name [ GenericParameters ] [ BaseList ] Block .
```

其中：

- **定义** `InterfaceDeclaration` 为接口声明
- **定义** `Modifier` 为修饰符（见 [修饰符](#81-修饰符)）
- **定义** `Name` 为接口名（见 [标识符](#14-标识符)）
- 有关 `BaseList`，见 [继承列表](#277-继承列表)
- 有关 `GenericParameters`，见 [泛型参数](#91-泛型参数)
  - **当**被继承的接口携带泛型实参**时**，该接口**必须**为单态化表达式（见 [单态化表达式](#92-单态化表达式)）
- 有关 `Block`，见 [代码块](#42-代码块)

有关接口声明：

- 修饰符列表**必须**位于 `interface` 之前
- 接口的修饰符列表**必须仅**包含可访问性修饰符（见 [可访问性修饰符](#82-可访问性修饰符)）
- 接口声明体**必须**为声明序列体（见 [代码块](#42-代码块)）
- 接口声明体**不得**包含扩展声明；接口成员直接声明为契约（见 [扩展](#283-扩展)）

有关成员：

- **定义**接口成员为实现契约，不产生运行时实体
- 接口声明体**必须仅**包含：
  - 常量定义（见 [常量](#44-常量)），**且**常量**不得**被初始化
  - 访问器定义（见 [访问器](#282-访问器)）
  - 运算符定义（见 [运算符](#3101-运算符)）
  - 模块声明，且该模块**仅**用于标识符整理，**且**其体内**不得**约定字段（见 [模块](#61-模块)）
- 接口成员**不得**为字段定义（见 [字段](#281-字段)）
- 接口成员**不得**以 `static` 修饰（见 [static 修饰符](#816-static-修饰符)）
- 接口成员**必须**显式声明 `public`（见 [public 修饰符](#83-public-修饰符)）
  - **当**省略基础可访问性修饰符**时**，编译器**必须**报错
  - 接口中的运算符契约除外；其基础可访问性**必须为** `public`，且**不得**携带可访问性修饰符
- 接口访问器**不得**携带 Backing Field（见 [访问器](#282-访问器)）

有关实现：

- 接口**不得**被创建实例
- 接口**必须仅**由 `class` 实现
- 实现接口的类**必须**在继承列表中列出该接口（见 [继承列表](#277-继承列表)）
- 实现接口的类**必须**在类型体内提供一个**或**多个扩展块（见 [扩展](#283-扩展)）
  - 该类全部类型体扩展块的成员**必须**共同实现接口的全部成员
  - 类体内扩展块之外的成员**不得**用于实现接口
  - **当**接口为空接口**时**，不要求扩展块
- 外部扩展**不得**实现接口（见 [扩展](#283-扩展)）
- 实现接口的成员**必须**满足如下**所有**条件：
  - 名称相同
  - 种类相同
  - 类型相同，**但**以下情况除外：
    - `this` 参数的目标类型**允许**协变替换
  - 行为限定修饰符均无、相同或更少
  - 行为激活修饰符均无、相同或更多
  - 优化修饰符均无或相同
  - 可访问性大于等于接口成员
  - 方法的 `this` 参数在参数列表中的出现位置相同
  - 访问器的成员相同或更多
  - 访问器的成员可访问性大于等于接口访问器成员

有关空接口：

- **定义**空接口为自身及全部被继承接口均无成员的接口
- 空接口的实现类**不得**因此被要求提供扩展块

有关继承列表：

- **当**包含接口**时**，继承该接口
  - 被继承接口的成员成为当前接口成员
  - 实现当前接口的类实例可被以被继承接口类型承载
- 继承列表**不得**包含当前接口自身
- 泛型接口被继承或实现**时\*\***必须\*\*经单态化表达式提供泛型实参（见 [单态化表达式](#92-单态化表达式)）

有关类型转换：

- 接口与类实例之间的类型转换**必须**仅进行类型重解释，不改变实例内容
- **允许**实现接口的类与接口之间**互相显式**转换
- **允许**实现接口的类**单向隐式**转换为接口
- **允许**存在继承关系的接口之间**互相显式**转换
- **允许**子接口**单向隐式**转换为父接口

例如：

```novasharp
// 合法：泛型接口
interface IValue<T>
{
    public constant Get(this: IValue<T>): T;
    public accessor Value: T { get; }
}

// 合法：继承接口
interface IArray<T>: IValue<pointer T>
{
    public constant Length(this: IArray<T>): integer(8);
}

// 定义：类 Box
// 合法：实现接口
class Box: IValue<integer(4)>
{
    public Data: integer(4);

    extension
    {
        public constant Get(this: Box): integer(4)
        {
            return Data;
        }

        public accessor Value: integer(4) => Data { get; }
    }
}

// 合法：接口类型承载
variable value: IValue<integer(4)> = Box();

// 合法：空接口不要求扩展块
interface Empty { }
class EmptyBox: Empty { }

// 非法：接口实例化
// variable bad: IValue<integer(4)> = IValue<integer(4)>();
// 错误：接口不得被创建实例

// 非法：结构体实现接口
// structure Bad: IValue<integer(4)> { }
// 错误：接口必须仅由 class 实现

// 非法：接口成员为字段
// interface Bad
// {
//     public Value: integer(4);
// }
// 错误：接口成员不得为字段

// 非法：接口成员以 static 修饰
// interface Bad
// {
//     public static constant Value: function() integer(4);
// }
// 错误：接口成员不得以 static 修饰

// 非法：接口成员被初始化
// interface Bad
// {
//     public constant Value: integer(4) = 0;
// }
// 错误：接口内的常量不得被初始化

// 非法：实现成员位于扩展块之外
// class Bad: IValue<integer(4)>
// {
//     public constant Get: function(this: Bad) integer(4) { return 0; }
// }
// 错误：接口成员必须在类型体扩展块中实现
```

#### 2.7.4 枚举

**枚举**是值类型（见 [值类型](#23-值类型)），提供标识符与底层类型值的映射，其格式如下：

```ebnf
EnumerationDeclaration = { Modifier } "enumeration" Name ":" BasicType "{" { EnumerationMemberDeclaration | ExtensionDeclaration } "}" .

EnumerationMemberDeclaration = Name "=" Expression ";" .
```

其中：

- **定义** `EnumerationDeclaration` 为枚举声明
- **定义** `EnumerationMemberDeclaration` 为枚举成员声明
- **定义** `Modifier` 为修饰符（见 [修饰符](#81-修饰符)）
- **定义** `Name` 为成员名（见 [标识符](#14-标识符)）
- **定义** `BasicType` 为底层类型
  - 底层类型**必须**为基本类型（见 [基本类型](#22-基本类型)）
- **定义** `Expression` 为成员值表达式（见 [表达式](#31-表达式)）
- 有关 `ExtensionDeclaration`，见 [扩展](#283-扩展)

有关枚举声明：

- 修饰符列表**必须**位于 `enumeration` 之前
- 修饰符列表**必须仅**包含可访问性修饰符（见 [可访问性修饰符](#82-可访问性修饰符)）
- 底层类型**不得**省略
- 枚举**不得**携带泛型参数（见 [泛型参数](#91-泛型参数)）
- 枚举的体**必须**为类型体（见 [代码块](#42-代码块)）
- 枚举的类型体**允许**包含扩展块（见 [扩展](#283-扩展)）
- 枚举**不得**实现接口（见 [接口](#273-接口)）

有关成员：

- 成员**必须**为无种类的成员定义
- 成员值表达式**不得**省略
- 成员值表达式**必须**为编译期常量（见 [编译期边界](#106-编译期边界)）
- 成员值**不得**重复
- 成员定义**必须**以语句终止符终止（见 [语句终止](#18-语句终止)）

有关内存布局：

- 枚举值的内存布局**必须**与其底层类型的值一致
- 枚举值**必须**直接存储其对应的底层类型的值

有关类型转换：

- **允许**底层类型值与对应枚举值之间**互相显式**转换
- **允许**枚举值**单向隐式**转换为其底层类型值

有关语法糖：

- **定义**枚举类型名省略语法糖为：**当**目标类型为枚举类型**且**目标类型由上下文给出**时**，将 `Type.Name` 写作 `Name`
- 目标类型**必须**由以下之一给出：
  - 显式类型标注的变量、常量、字段定义（见 [变量](#43-变量)、[常量](#44-常量)、[字段](#281-字段)）
  - 显式类型标注的堆分配定义（见 [堆分配](#45-堆分配)）
  - 赋值**或**复合赋值的目标（见 [赋值语句](#46-赋值语句)）
  - 函数、方法、运算符、函数字面量的参数（见 [参数](#72-参数)、[函数](#1710-函数)）
  - 函数、方法、运算符、函数字面量的返回类型（见 [return 语句](#492-return-语句)）
  - 参数默认值（见 [参数](#72-参数)）
  - `Cast<T>` 的目标类型（见 [类型转换表达式](#34-类型转换表达式)）
  - `??` 的右侧续体（见 [空值合并表达式](#31027-空值合并表达式)）
  - `match` 的匹配目标（见 [match 语句](#486-match-语句)）
  - 成员构造的成员值表达式（见 [成员构造表达式](#38-成员构造表达式)）
- `Name` **必须为** `Type` 的枚举成员
- 当前作用域中**不得**存在与 `Name` 同名的绑定
- 当前类型的成员属于当前作用域；`this` 的同名成员**必须**写完整形式
- **当**上述条件全部满足**时**，`Name` **必须**解析为成员访问（见 [成员访问表达式](#352-成员访问表达式)）
- **当**存在同名绑定**时**，**必须**写 `Type.Name`
- 其他位置**不得**使用 `Name`
- 在 `match` 的值相等模式中，目标类型**必须为**被匹配表达式的类型
- 完整形式**允许**使用

例如：

```novasharp
// 合法：基本枚举
enumeration Status: integer(4)
{
    Pending = 0;
    Running = 1;
    Completed = 2;

    extension
    {
        public constant IsDone(this: &Status): boolean
        {
            return this == Status.Completed;
        }
    }
}

// 定义：变量 current
// 合法：使用枚举类型名省略语法糖
// 此时 Status.Running 被省略为 Running
variable current: Status = Running;

// 合法：隐式转换
variable s: Status = Status.Running;
variable i: integer(4) = s;

// 合法：显式转换
variable another: Status = Cast<Status>(2);

// 非法：成员值重复
// enumeration Bad: integer(4)
// {
//     A = 1;
//     B = 1;
// }
// 错误：成员值不得重复

// 非法：省略底层类型
// enumeration Bad
// {
//     A = 1;
// }
// 错误：底层类型不得省略

// 非法：省略成员值
// enumeration Bad: integer(4)
// {
//     A;
// }
// 错误：成员值表达式不得省略

// 非法：枚举携带泛型参数
// enumeration Bad<T>: integer(4)
// {
//     A = 1;
// }
// 错误：枚举不得携带泛型参数
```

#### 2.7.5 变体

**变体**是值类型（见 [值类型](#23-值类型)），用于表示不同状态的值，无默认内存分配方式（见 [内存分配](#111-内存分配)），其格式如下：

```ebnf
VariantDeclaration = { Modifier } "variant" Name [ GenericParameters ] "{" { VariantMemberDeclaration | ExtensionDeclaration } "}" .

VariantMemberDeclaration = Name [ ":" Type ] ";" .
```

其中：

- **定义** `VariantDeclaration` 为变体声明
- **定义** `VariantMemberDeclaration` 为状态声明
- **定义** `Modifier` 为修饰符（见 [修饰符](#81-修饰符)）
- **定义** `Name` 为状态名（见 [标识符](#14-标识符)）
- **定义** `Type` 为载荷类型（见 [类型构造语法](#21-类型构造语法)）
- 有关 `GenericParameters`，见 [泛型参数](#91-泛型参数)

有关变体声明：

- 修饰符列表**必须**位于 `variant` 之前
- 修饰符列表**必须仅**包含可访问性修饰符（见 [可访问性修饰符](#82-可访问性修饰符)）
- 变体的体**必须**为类型体（见 [代码块](#42-代码块)）
- 变体的类型体**允许**包含扩展块（见 [扩展](#283-扩展)）
- 变体**不得**实现接口（见 [接口](#273-接口)）

有关状态：

- **定义**状态为变体的成员
- **定义**载荷为状态携带的值
- 状态**必须仅**包含零个或一个载荷
- **允许**状态省略 `:`，以表示无载荷
- **当**状态不携带载荷**时**，状态成员**必须**表现为该状态的变体实例
- **当**状态携带载荷**时**，状态**必须**经成员构造表达式构造（见 [成员构造表达式](#38-成员构造表达式)）

> [!NOTE] 无载荷状态与枚举成员的辨析
> 两者语法同形，均判定为成员访问表达式（见 [成员访问表达式](#352-成员访问表达式)）。枚举成员表示底层类型的值（见 [枚举](#274-枚举)）；无载荷状态表示该状态的变体实例。

有关内存布局：

- 变体方法**不得**进入内存布局
- **定义**状态空间为由所有状态构建的枚举，用于标识当前状态
  - 状态空间底层类型**必须为**足以容纳状态数量的最小整数类型
- **定义**载荷空间为由所有载荷类型构建的共同体（见 [共同体](#276-共同体)）
- 内存布局**必须为**状态空间在前、载荷空间在后
- 状态空间和载荷空间**必须**按各自大小对齐

有关生命周期：

- 变体实例化时**必须**确定其状态
- **当**对已实例化的变体赋予新状态**时**，**必须**修改状态空间和载荷空间的内容
  - **当**旧状态携带载荷**时**，**必须**在修改前销毁该载荷
  - 上述修改**不得**创建新变体实例

有关实例相等：

- **判定**变体实例 `F` 与变体实例 `L` 相等，**当且仅当**满足如下**所有**条件：
  - `F` 和 `L` 的类型相同
  - `F` 和 `L` 的状态相同
  - **若**状态携带载荷，**则** `F` 和 `L` 的载荷相同
- 载荷相同**必须**遵循载荷类型的相等语义（见 [基本类型](#22-基本类型)）

有关语法糖：

- **定义**变体类型名省略语法糖为：**当**目标类型为变体类型**且**目标类型由上下文给出**时**，将 `Type.Name` 写作 `Name`，将 `Type.Name(Expression)` 写作 `Name(Expression)`
- 目标类型**必须**由以下之一给出：
  - 显式类型标注的变量、常量、字段定义（见 [变量](#43-变量)、[常量](#44-常量)、[字段](#281-字段)）
  - 显式类型标注的堆分配定义（见 [堆分配](#45-堆分配)）
  - 赋值**或**复合赋值的目标（见 [赋值语句](#46-赋值语句)）
  - 函数、方法、运算符、函数字面量的参数（见 [参数](#72-参数)、[函数](#1710-函数)）
  - 函数、方法、运算符、函数字面量的返回类型（见 [return 语句](#492-return-语句)）
  - 参数默认值（见 [参数](#72-参数)）
  - `Cast<T>` 的目标类型（见 [类型转换表达式](#34-类型转换表达式)）
  - `??` 的右侧续体（见 [空值合并表达式](#31027-空值合并表达式)）
  - `is` 的左操作数（见 [is 表达式](#39-is-表达式)）
  - `match` 的匹配目标（见 [match 语句](#486-match-语句)）
  - 成员构造的成员值表达式（见 [成员构造表达式](#38-成员构造表达式)）
- 无载荷状态**必须**写作 `Name`；有载荷状态**必须**写作 `Name(Expression)`
- `Name` **必须为** `Type` 的状态
- 当前作用域中**不得**存在与 `Name` 同名的绑定
- 当前类型的成员属于当前作用域；`this` 的同名成员**必须**写完整形式
- **当**上述条件全部满足**时**，`Name` **必须**解析为成员访问；`Name(Expression)` **必须**解析为成员构造，**不得**解析为函数调用（见 [成员构造表达式](#38-成员构造表达式)）
- **当**存在同名绑定**或**同名函数**时**，**必须**写完整形式
- 其他位置**不得**使用短形式
- 在 `is` 表达式中，短形式的目标类型**必须为**左操作数的类型；在 `match` 中，目标类型**必须为**匹配目标的类型
- 完整形式**允许**使用

例如：

```novasharp
// 合法：基本变体
variant Status
{
    Idle;
    Loading: integer(4);
    Done;

    extension
    {
        public constant IsDone(this: &Status): boolean
        {
            return this == Status.Done;
        }
    }
}

// 合法：泛型变体
variant Outcome<TError>
{
    Ok;
    Error: TError;
}

// 合法：无载荷状态
variant Phase
{
    Idle;
    Active: integer(4);
}

// 定义：函数 Main
constant Main(): integer(4)
{
    // 合法：实例化并赋值
    variable s: Status = Status.Loading(50);

    // 合法：经成员访问表达式取值并赋值
    s = Status.Done;

    // 合法：实例化新值并赋值
    s = Status.Idle;

    // 合法：比较
    variable r1: Outcome<integer(4)> = Outcome<integer(4)>.Error(1);
    variable r2: Outcome<integer(4)> = Outcome<integer(4)>.Error(1);
    variable same: boolean = r1 == r2;

    return 0;
}

// 非法：未确定状态实例化
// variable bad: Status = Status;
// 错误：变体实例化时必须确定状态

// 非法：状态不存在
// variable bad: Status = Status.Unknown;
// 错误：Unknown 不是 Status 的状态

// 非法：载荷类型不匹配
// variable bad: Status = Status.Loading("text");
// 错误：Loading 的载荷类型必须为 integer(4)
```

#### 2.7.6 共同体

**共同体**是值类型（见 [值类型](#23-值类型)），用于以不同方式访问同一块内存，无默认内存分配方式（见 [内存分配](#111-内存分配)），其格式如下：

```ebnf
UnionDeclaration = { Modifier } "union" Name [ GenericParameters ] "{" { UnionMemberDeclaration | ExtensionDeclaration } "}" .

UnionMemberDeclaration = { Modifier } Name ":" Type ";" .
```

其中：

- **定义** `UnionDeclaration` 为共同体声明
- **定义** `UnionMemberDeclaration` 为共同体成员声明
- **定义** `Modifier` 为修饰符（见 [修饰符](#81-修饰符)）
- **定义** `Name` 为成员名（见 [标识符](#14-标识符)）
- **定义** `Type` 为成员的类型（见 [类型构造语法](#21-类型构造语法)）
- 有关 `GenericParameters`，见 [泛型参数](#91-泛型参数)

有关共同体声明：

- 修饰符列表**必须**位于 `union` 之前
- 修饰符列表**必须仅**包含可访问性修饰符（见 [可访问性修饰符](#82-可访问性修饰符)）
- 共同体的体**必须**为类型体（见 [代码块](#42-代码块)）
- 共同体的类型体**允许**包含扩展块（见 [扩展](#283-扩展)）
- 共同体**不得**实现接口（见 [接口](#273-接口)）

有关成员：

- 成员**必须**为无种类的成员定义
- 成员**必须仅**支持 `aligned(N)` 修饰符（见 [aligned(N) 修饰符](#815-alignedn-修饰符)）
- 修饰符列表**必须**位于成员名之前
- 成员**不得**携带初值
- 共同体**不得**包含访问器（见 [访问器](#282-访问器)）

有关构造：

- 共同体**必须**经成员构造表达式构造（见 [成员构造表达式](#38-成员构造表达式)）
- **定义**被构造成员为成员构造表达式指定的成员
- **定义**未被构造成员为成员构造表达式中未被指定的成员
- 被构造成员**必须**被初始化为成员值表达式的返回值
- 成员构造表达式**必须仅**初始化被构造成员，**不得**对未被构造成员执行初始化

有关内存布局：

- **定义**基础起始点为共同体实例的内存起始点
- 共同体成员**必须**以基础起始点为偏移基准
- **定义**成员偏移为成员相对于基础起始点的偏移
- 每个成员**必须**具有成员偏移：
  - 未声明 `aligned(N)` **时**，成员偏移**必须为** 0
  - **当**成员声明 `aligned(N)` **时**，成员偏移**必须为** N
- **定义**共同体大小为各成员的成员偏移与大小之和的最大值

有关访问：

- **当**读取共同体成员**时**，**必须**从该成员的成员偏移处开始，**并**按该成员的类型解释该内存
- **当**写入共同体成员**时**，**必须**从该成员的成员偏移处开始，**并**按该成员的类型写入
- 成员构造表达式中未被指定的成员**允许**被读取**并**写入

有关语法糖：

- **定义**共同体类型名省略语法糖为：**当**目标类型为共同体类型**且**目标类型由上下文给出**时**，将 `Type.Name(Expression)` 写作 `Name(Expression)`
- 目标类型**必须**由以下之一给出：
  - 显式类型标注的变量、常量、字段定义（见 [变量](#43-变量)、[常量](#44-常量)、[字段](#281-字段)）
  - 显式类型标注的堆分配定义（见 [堆分配](#45-堆分配)）
  - 赋值**或**复合赋值的目标（见 [赋值语句](#46-赋值语句)）
  - 函数、方法、运算符、函数字面量的参数（见 [参数](#72-参数)、[函数](#1710-函数)）
  - 函数、方法、运算符、函数字面量的返回类型（见 [return 语句](#492-return-语句)）
  - 参数默认值（见 [参数](#72-参数)）
  - `Cast<T>` 的目标类型（见 [类型转换表达式](#34-类型转换表达式)）
  - `??` 的右侧续体（见 [空值合并表达式](#31027-空值合并表达式)）
  - `match` 的匹配目标（见 [match 语句](#486-match-语句)）
  - 成员构造的成员值表达式（见 [成员构造表达式](#38-成员构造表达式)）
- `Name` **必须为** `Type` 的成员
- 当前作用域中**不得**存在与 `Name` 同名的绑定
- 当前类型的成员属于当前作用域；`this` 的同名成员**必须**写完整形式
- **当**上述条件全部满足**时**，`Name(Expression)` **必须**解析为成员构造，**不得**解析为函数调用（见 [成员构造表达式](#38-成员构造表达式)）
- **当**存在同名绑定**或**同名函数**时**，**必须**写完整形式
- 其他位置**不得**使用短形式
- 共同体成员的读取**不得**使用短形式；读取**必须**经实例的成员访问表达式进行（见 [成员访问表达式](#352-成员访问表达式)）
- 在 `match` 的值相等模式中，目标类型**必须为**被匹配表达式的类型
- 完整形式**允许**使用

例如：

```novasharp
// 定义：结构体 Color
structure Color
{
    public Value: unsigned integer(4);
}

// 合法：基本共同体
union Pixel
{
    RGBA: Color;
    Packed: unsigned integer(4);
    Channels[4]: integer(1);
}

// 合法：成员偏移
union AlignedBuffer
{
    Header: integer(1);
    aligned(8) Payload[64]: integer(1);
}

// 合法：共同体嵌入结构体
structure Frame
{
    public PixelData: Pixel;
    public Timestamp: integer(4);
}

// 非法：共同体成员携带初值
// union Bad
// {
//     Value: integer(4) = 0;
// }
// 错误：共同体成员不得携带初值

// 非法：共同体成员携带非 aligned 修饰符
// union Bad
// {
//     public Value: integer(4);
// }
// 错误：共同体成员必须仅支持 aligned(N) 修饰符
```

#### 2.7.7 继承列表

**继承列表**是被继承或被实现目标的列表，其格式如下：

```ebnf
BaseList = ":" ( Identifier | MonomorphizationExpression ) { "," ( Identifier | MonomorphizationExpression ) } .
```

其中：

- **定义** `BaseList` 为继承列表
- **定义** `Identifier` 为被继承或被实现的目标（见 [标识符](#14-标识符)）
- **定义** `MonomorphizationExpression` 为携带泛型实参的目标（见 [单态化表达式](#92-单态化表达式)）

有关继承列表：

- 继承列表**必须**以 `:` 起始
- 目标之间**必须**以逗号 `,` 分隔
- **当**继承列表出现在类声明中**时**，**允许**包含最多一个类与多个接口（见 [类](#271-类)）
- **当**继承列表出现在接口声明中**时**，**允许**仅包含接口（见 [接口](#273-接口)）
- 只有 class 的继承列表**允许**包含接口；接口的继承列表**不得**包含类
- 继承列表中的接口**必须**由 class 类型体内的扩展实现（见 [接口](#273-接口)、[扩展](#283-扩展)）
- 继承列表**不得**包含当前类型自身

例如：

```novasharp
// 定义：类 MyBaseClass
class MyBaseClass
{

}

// 定义：接口 MyInterface
interface MyInterface
{

}

// 合法：类继承一个类并实现一个接口
class MyClass: MyBaseClass, MyInterface
{

}

// 合法：接口继承接口
interface MyOtherInterface: MyInterface
{

}
```

### 2.8 成员

#### 2.8.1 字段

**字段**是类型声明体中的数据成员，其格式如下：

```ebnf
FieldDefinition = { Modifier } Name [ ":" Type ] [ "=" Expression | Block ] .
```

其中：

- **定义** `FieldDefinition` 为字段定义
- **定义** `Modifier` 为修饰符（见 [修饰符](#81-修饰符)）
- **定义** `Name` 为字段名（见 [标识符](#14-标识符)）
- **定义** `Type` 为字段类型（见 [类型构造语法](#21-类型构造语法)）
- **定义** `Expression` 为初始化表达式（见 [表达式](#31-表达式)）
- **定义** `Block` 为函数字段的体（见 [代码块](#42-代码块)）

有关字段定义：

- 修饰符列表**必须**位于字段名之前
- 字段定义**必须**以语句终止符终止（见 [语句终止](#18-语句终止)）
- 字段定义**必须仅**作为类**或**结构体的成员出现（见 [类](#271-类)、[结构体](#272-结构体)）
- 字段定义**不得**出现在接口声明体内（见 [接口](#273-接口)）
- 字段定义**不得**出现在共同体声明体内（见 [共同体](#276-共同体)）
- 类型声明体**不得**定义变量（见 [变量](#43-变量)）**或**堆分配标识符（见 [堆分配](#45-堆分配)）
- `:` 与 `=` **必须**至少出现一个
- 有关定义简写，见 [标识符定义简写](#15-标识符定义简写)

有关初始化：

- 字段不强制要求初始化
- `Expression` 的返回值类型**必须为**字段类型**或**可隐式转换为字段类型
- **当**出现 `=` **时**，字段**必须**被赋值为 `Expression` 的返回值
- **当**省略 `:` **时**，字段类型**必须**由 `=` 的返回值推断

有关内存布局：

- 字段**必须**进入实例内存布局（见 [类](#271-类)、[结构体](#272-结构体)）
- **当**出现 `static` **时**，字段**不得**进入实例内存布局（见 [static 修饰符](#816-static-修饰符)）

有关函数字段：

- **定义**函数字段为类型为函数类型（见 [函数类型构造器](#264-函数类型构造器)）的字段
- 函数字段**允许**使用函数简写；其 `Block` 仍为函数字段的体
- **当**出现 `Block` **时**，字段类型**必须**为函数类型
- 函数字段的调用**必须**经成员访问表达式进行（见 [成员访问表达式](#352-成员访问表达式)）
- 函数字段**不得**被判定为方法（见 [方法](#74-方法)）

例如：

```novasharp
// 定义：类 MyClass
class MyClass
{
    // 合法：未初始化的字段
    public Delegate: function();

    // 合法：带初始值的字段
    public Count: integer(4) = 0;

    // 合法：函数字段
    public Inc: function(value: integer(4)) integer(4) { }
}

// 非法：字段定义位于类与结构体之外
// public Bad: integer(4);
// 错误：字段定义必须仅作为类或结构体的成员出现

// 非法：接口中的字段
// interface Bad
// {
//     public Value: integer(4);
// }
// 错误：接口成员不得为字段

// 非法：共同体中使用字段
// union Bad
// {
//     public Value: integer(4)
// }
// 错误：共同体成员不得为字段
```

#### 2.8.2 访问器

**访问器**是封装读写行为的标识符种类，其格式如下：

```ebnf
AccessorDefinition        = { Modifier } "accessor" Name ":" Type [ "=>" Backing ] [ AccessorMembers ] .

AccessorMembers           = "{" [ AccessorMemberDefinition { ";" AccessorMemberDefinition } [ ";" ] ] "}" .

AccessorMemberDefinition  = { Modifier } ( "get" | "set" ) [ ":" Type ] [ "=" Expression ] .

Backing                   = Identifier .
```

其中：

- **定义** `AccessorDefinition` 为访问器定义
- **定义** `AccessorMembers` 为访问器成员列表
- **定义** `AccessorMemberDefinition` 为访问器成员定义
- **定义** `Backing` 为 Backing Field 的标识符
- **定义** `Modifier` 为修饰符（见 [修饰符](#81-修饰符)）
- **定义** `Name` 为访问器名（见 [标识符](#14-标识符)）
- **定义** `Type` 为目标类型（见 [类型构造语法](#21-类型构造语法)）
- **定义** `Expression` 为成员实现表达式（见 [表达式](#31-表达式)）
- **定义** `get` 与 `set` 为访问器成员名
  - 成员名是约定名，不占用关键字（见 [关键字](#16-关键字)）

有关访问器定义：

- 修饰符列表**必须**位于 `accessor` 之前
- 访问器定义**必须**以语句终止符终止（见 [语句终止](#18-语句终止)）
- 目标类型**必须**出现
- 访问器**不得**携带泛型参数（见 [泛型参数](#91-泛型参数)）
- **允许**访问器出现在扩展块、接口声明体**或**类型声明体与扩展块之外的作用域（见 [作用域](#51-作用域)）
- 访问器**不得**直接出现在 class 与 structure 的类型声明体内
- `=>` 与 `AccessorMembers` **必须**至少出现一个
- 有关定义简写，见 [标识符定义简写](#15-标识符定义简写)

有关成员：

- **定义** `get` 为读取成员
  - `get` 的参数列表**必须**为空，返回值类型**必须**为目标类型
- **定义** `set` 为写入成员
  - `set` 的参数列表**必须**为 `value: 目标类型`，返回值类型**必须**为空类型
- **当**访问器成员属于索引访问器**时**，`get` 的参数列表**必须**为索引参数，返回值类型**必须**为目标类型（见 [运算符](#3101-运算符)）
- **当**访问器成员属于索引访问器**时**，`set` 的参数列表**必须**为索引参数与 `value: 目标类型`，返回值类型**必须**为空类型
- 扩展块内的非 `static` 访问器成员**必须**显式书写 `this` 参数（见 [方法](#74-方法)）
- **当**访问器出现在类型声明体与扩展块之外**时**，其成员**不得**携带 `this` 参数
- **允许**仅提供 `get` 或仅提供 `set`
- **当**成员携带类型标注**时**，该标注**必须**与上述推导结果匹配，**否则**编译器**必须**报类型错误
- 访问器成员**不得**通过成员访问表达式访问（见 [成员访问表达式](#352-成员访问表达式)）
- 访问器的访问**必须**经访问器名进行（见 [成员访问表达式](#352-成员访问表达式)）
- 访问器成员**必须仅**支持可访问性修饰符（见 [可访问性修饰符](#82-可访问性修饰符)）
- 访问器成员的可访问性**必须**相对于访问器自身所在作用域（见 [作用域](#51-作用域)）
- **当**访问器成员无基础可访问性修饰符**时**，其可访问性**必须**与访问器相同
- 访问器成员的可访问性**不得**高于访问器的可访问性
- **当**访问器出现在扩展块内**时**，访问器成员是方法（见 [方法](#74-方法)）
- **当**访问器出现在接口声明体内**时**，其成员**不得**显式书写 `this` 参数；其 `this` 参数的类型**必须为**该接口类型（见 [接口](#273-接口)）
- **当**访问器出现在类型声明体与扩展块之外**时**，访问器成员是函数常量（见 [常量](#44-常量)）

有关 Backing Field：

- `Backing` **必须**解析为当前作用域内可访问的字段、变量**或**常量
- `Backing` 的类型**必须**等于目标类型
- **当** `Backing` 为常量**时**，访问器**必须**为只读访问器，**且**其成员列表**不得**包含 `set`
- **当** `Backing` 为局部变量**时**，访问器成员**必须**按引用访问该存储
  - 访问器**不得**逃出该局部变量的作用域（见 [内存分配](#111-内存分配)）
- **当**访问器成员包含 `set` **时**，`Backing` **必须**可写
- **当**访问器位于扩展块内**时**，`Backing` **必须**按成员访问的可访问性规则解析
- **当**访问器位于类型声明体与扩展块之外**时**，`Backing` **必须**从当前作用域解析

有关默认实现：

- **当**访问器携带 `Backing` **时**：
  - **当** `get` 未提供实现表达式**时**，其值**必须为**读取 `Backing`
  - **当** `set` 未提供实现表达式**时**，其值**必须为**写入 `Backing`
  - 未出现在成员列表中的成员**必须**按上述默认实现提供
- **当**访问器不携带 `Backing` **时**：
  - 每个访问器成员**必须**提供实现表达式
  - 成员的实现表达式是计算型实现，不读写隐式存储

有关接口：

- 接口声明体中的访问器**不得**携带 `Backing`（见 [接口](#273-接口)）
- 接口声明体中的访问器成员**不得**提供实现表达式
- 实现接口的类可在类型体扩展块中提供携带 `Backing` 的实现（见 [接口](#273-接口)、[扩展](#283-扩展)）

有关类型级访问器：

- **允许**以 `static` 修饰访问器（见 [static 修饰符](#816-static-修饰符)）
- 类型级访问器的成员**必须**为不含 `this` 参数的函数常量
- 类型级访问器的 `Backing` **必须**为同类型的 `static` 字段、全局变量**或**全局常量

例如：

```novasharp
// 定义：类 Counter
class Counter
{
    private _count: integer(4);

    extension
    {
        // 合法：字段型访问器，默认读写 _count
        public accessor Count: integer(4) => _count;

        // 合法：字段型访问器，set 私有
        public accessor ReadOnlyCount: integer(4) => _count { get; private set; }
    }
}

// 定义：类 AutoCounter
class AutoCounter
{
    private _count: integer(4) = 0;

    extension
    {
        // 合法：字段型访问器，默认读写
        public accessor Count: integer(4) => _count;
    }
}

// 定义：类 FixedCounter
class FixedCounter
{
    extension
    {
        private constant _count: integer(4) = 0;

        // 合法：常量 backing，自动只读
        public accessor Count: integer(4) => _count;
    }
}

// 定义：结构体 Vector3
structure Vector3
{
    public X: float(4);
    public Y: float(4);
    public Z: float(4);

    extension
    {
        // 合法：计算型访问器
        public accessor LengthSquared: float(4)
        {
            get = (this: &Vector3) float(4) => { return this.X * this.X + this.Y * this.Y + this.Z * this.Z; }
        }
    }
}

// 合法：类型外的字段型访问器
variable Global: integer(4);
accessor Hidden: integer(4) => Global;

// 定义：类 StaticCounter
class StaticCounter
{
    private static _count: integer(4);

    extension
    {
        // 合法：类型级访问器
        public static accessor Count: integer(4) => _count;
    }
}

// 非法：既无 Backing 又无成员
// accessor Bad: integer(4);
// 错误：访问器必须至少提供 Backing 或访问器成员

// 非法：计算型访问器成员没有实现
// accessor Bad: integer(4) { get; }
// 错误：无 Backing 的访问器成员必须提供实现表达式

// 非法：常量 backing 携带 set
// accessor Bad: integer(4) => _constValue { get; set; }
// 错误：常量 backing 的访问器不得包含 set

// 非法：访问器携带泛型参数
// accessor Bad<T>: T => _value;
// 错误：访问器不得携带泛型参数
```

#### 2.8.3 扩展

**扩展**是为类型追加成员的声明，其格式如下：

```ebnf
ExtensionDeclaration = "extension" [ "for" ExtensionTarget ] Block .

ExtensionTarget      = Type
                     | GenericTarget
                     | ArrayTarget .

GenericTarget        = Identifier "<" GenericParameterDefinition { ";" GenericParameterDefinition } ">" .

ArrayTarget          = "array" "(" TargetBinding { "," TargetBinding } ")" GenericParameterDefinition .

TargetBinding        = Name ":" Type .
```

其中：

- **定义** `ExtensionDeclaration` 为扩展
- **定义** `ExtensionTarget` 为扩展目标
- **定义** `Type` 为目标类型（见 [类型构造语法](#21-类型构造语法)）
- **定义** `ArrayTarget` 为数组目标
- **定义** `GenericTarget` 为泛型目标
- **定义** `TargetBinding` 为参数绑定
- **定义** `Name` 为绑定的名称（见 [标识符](#14-标识符)）
- 有关 `GenericParameterDefinition`，见 [泛型参数](#91-泛型参数)
- 有关 `Block`，见 [代码块](#42-代码块)

有关目标：

- **当**扩展出现在类型声明体内**时**，其目标**必须为**该类型，**且** `for` **不得**出现
- **当**扩展出现在类型声明体外**时**，其目标**必须**由 `for` 指定
- 扩展目标**必须**为类型、泛型目标**或**数组目标
- 泛型目标**必须**以标识符起始，其类型实参**必须**写作泛型参数（见 [泛型参数](#91-泛型参数)）
- 数组目标**必须**以 `array` 起始，其参数**必须**写作「名称: 类型」，其类型实参**必须**写作泛型参数（见 [泛型参数](#91-泛型参数)）
  - 绑定的名称**允许**在扩展体内使用
  - **当**扩展目标为数组目标**时**，绑定的名称**必须**为编译期常量，**且**绑定的类型**必须**为无符号整数类型（见 [数组类型构造器](#262-数组类型构造器)）
- 扩展目标中的泛型参数**允许**携带约束（见 [泛型参数](#91-泛型参数)）
  - **当**泛型参数受约束**时**，扩展**仅**对满足该约束的实例生效
- 类型实参中的未绑定标识符**必须**按泛型参数解释

有关成员：

- 扩展成员**不得**声明字段（见 [字段](#281-字段)）
- 扩展成员**允许**以已有字段、变量**或**常量作为 Backing Field（见 [访问器](#282-访问器)）
- 扩展成员的其它规则与类型内部的成员相同
- 扩展成员**必须**视作扩展目标类型的成员，**但**其 `private` 成员**必须仅**在扩展块内可见（见下文）
- **当**扩展成员与目标类型的已有成员**或**其它扩展的成员重名**时**，**必须**报错

有关接口：

- 只有 `class` 类型体内的扩展**允许**实现该 class 继承列表中的接口（见 [接口](#273-接口)）
- 实现接口的扩展成员**必须**位于 class 类型体内
- 外部扩展**不得**实现接口
- 同一 class 的类型体内**允许**出现多个扩展块；其成员**必须**共同满足接口的全部成员（见 [接口](#273-接口)）

有关可见性：

- 类型体外的扩展**必须**经 `import` 后才可见（见 [导入](#62-导入)）
- `private` 成员**仅**在该扩展块内可见

例如：

```novasharp
// 定义：结构体 Vector3
structure Vector3
{
    public X: float(4);
    public Y: float(4);
    public Z: float(4);

    // 合法：类型体内的扩展
    extension
    {
        public accessor Sum: float(4)
        {
            get = (this: &Vector3) float(4) => { return this.X + this.Y + this.Z; }
        }
    }
}

// 合法：外部扩展追加普通成员
extension for Vector3
{
    public constant DoubledSum(this: &Vector3): float(4)
    {
        return this.Sum * 2;
    }
}

// 合法：绑定数组的大小与元素类型
extension for array(length: unsigned integer(4)) T
{
    public accessor Length: unsigned integer(4)
    {
        get = (this: &array(length) T) unsigned integer(4) => { return length; }
    }
}

// 合法：泛型目标
extension for MyClass<T>
{
}

// 合法：泛型目标并加以约束
extension for MyType<T: IIterable>
{
}

// 非法：在扩展中声明字段
// extension for Vector3
// {
//     public W: float(4);
// }
// 错误：扩展成员不得声明字段

// 非法：与已有成员重名
// extension for Vector3
// {
//     public constant X: function(this: &Vector3) float(4) { return 0; }
// }
// 错误：扩展成员与已有成员重名
```

## 3. 表达式

### 3.1 表达式

**表达式**是一类带有返回值的语法形式，用于计算和求值，其格式如下：

```ebnf
Expression = ValueExpression
           | ParenthesisExpression
           | TypeConversionExpression
           | AddExpression
           | MinusExpression
           | MultiplyExpression
           | DivideExpression
           | RemainderExpression
           | LogicalNotExpression
           | LogicalAndExpression
           | LogicalOrExpression
           | EqualExpression
           | NotEqualExpression
           | GreaterExpression
           | LessExpression
           | GreaterEqualExpression
           | LessEqualExpression
           | BitwiseNotExpression
           | BitwiseAndExpression
           | BitwiseOrExpression
           | BitwiseXorExpression
           | LogicalRightShiftExpression
           | LogicalLeftShiftExpression
           | ReferenceExpression
           | DereferenceExpression
           | NegateExpression
           | FunctionCallExpression
           | ConstructionExpression
           | MemberConstructionExpression
           | IsExpression
           | AccessExpression
           | ConditionalExpression
           | NullCoalescingExpression
           | CompileTimeExpression .
```

其中：

- **定义** `Expression` 为表达式
- 有关 `ParenthesisExpression`，见 [括号表达式](#33-括号表达式)
- 有关 `TypeConversionExpression`，见 [类型转换表达式](#34-类型转换表达式)
- 有关 `ValueExpression`，见 [值表达式](#32-值表达式)
- 有关 `AddExpression`，见 [加法表达式](#31012-加法表达式)
- 有关 `MinusExpression`，见 [减法表达式](#31013-减法表达式)
- 有关 `MultiplyExpression`，见 [乘法表达式](#3109-乘法表达式)
- 有关 `DivideExpression`，见 [除法表达式](#31010-除法表达式)
- 有关 `RemainderExpression`，见 [求余表达式](#31011-求余表达式)
- 有关 `LogicalNotExpression`，见 [逻辑非表达式](#3105-逻辑非表达式)
- 有关 `LogicalAndExpression`，见 [逻辑和表达式](#31025-逻辑和表达式)
- 有关 `LogicalOrExpression`，见 [逻辑或表达式](#31026-逻辑或表达式)
- 有关 `EqualExpression`，见 [相等表达式](#31020-相等表达式)
- 有关 `NotEqualExpression`，见 [不等表达式](#31021-不等表达式)
- 有关 `GreaterExpression`，见 [大于表达式](#31017-大于表达式)
- 有关 `LessExpression`，见 [小于表达式](#31016-小于表达式)
- 有关 `GreaterEqualExpression`，见 [大于等于表达式](#31019-大于等于表达式)
- 有关 `LessEqualExpression`，见 [小于等于表达式](#31018-小于等于表达式)
- 有关 `BitwiseNotExpression`，见 [按位取反表达式](#3106-按位取反表达式)
- 有关 `BitwiseAndExpression`，见 [按位与表达式](#31022-按位与表达式)
- 有关 `BitwiseOrExpression`，见 [按位或表达式](#31024-按位或表达式)
- 有关 `BitwiseXorExpression`，见 [按位异或表达式](#31023-按位异或表达式)
- 有关 `LogicalRightShiftExpression`，见 [逻辑右移表达式](#31015-逻辑右移表达式)
- 有关 `LogicalLeftShiftExpression`，见 [逻辑左移表达式](#31014-逻辑左移表达式)
- 有关 `ReferenceExpression`，见 [引用表达式](#3107-引用表达式)
- 有关 `DereferenceExpression`，见 [解引用表达式](#3108-解引用表达式)
- 有关 `NegateExpression`，见 [取负表达式](#3104-取负表达式)
- 有关 `FunctionCallExpression`，见 [函数调用表达式](#36-函数调用表达式)
- 有关 `ConstructionExpression`，见 [构造表达式](#37-构造表达式)
- 有关 `MemberConstructionExpression`，见 [成员构造表达式](#38-成员构造表达式)
- 有关 `IsExpression`，见 [is 表达式](#39-is-表达式)
- 有关 `AccessExpression`，见 [访问表达式](#351-访问表达式)
- 有关 `ConditionalExpression`，见 [条件表达式](#31028-条件表达式)
- 有关 `NullCoalescingExpression`，见 [空值合并表达式](#31027-空值合并表达式)
- 有关 `CompileTimeExpression`，见 [编译期表达式](#103-编译期表达式)

有关结合次序：

- 有关各表达式之间的结合次序，见 [运算符优先级](#3102-运算符优先级)

有关求值顺序：

- 子表达式**必须**先于其所在表达式求值
- 同一表达式中的并列子表达式**必须**按书写顺序自左至右求值
  - 并列子表达式是同一表达式中互不嵌套的子表达式
- 逻辑和式、逻辑或式、空值合并式与条件表达式**必须**按各自页面规定的方式求值（见 [逻辑和表达式](#31025-逻辑和表达式)、[逻辑或表达式](#31026-逻辑或表达式)、[空值合并表达式](#31027-空值合并表达式)、[条件表达式](#31028-条件表达式)）

### 3.2 值表达式

**值表达式**是表示值的表达式，其语法如下：

```ebnf
ValueExpression = Identifier
                | Literal
                | MemberAccessExpression
                | PointerMemberAccessExpression
                | MonomorphizationExpression
                | IndexAccessExpression .
```

其中：

- **定义** `ValueExpression` 为值表达式
- 有关 `Identifier`，见 [标识符](#14-标识符)
  - `Identifier` **必须**已被定义**且**可访问
- 有关 `Literal`，见 [字面量](#171-字面量)
- 有关 `MemberAccessExpression`，见 [成员访问表达式](#352-成员访问表达式)
- 有关 `PointerMemberAccessExpression`，见 [指针成员访问表达式](#353-指针成员访问表达式)
- 有关 `MonomorphizationExpression`，见 [单态化表达式](#92-单态化表达式)
- 有关 `IndexAccessExpression`，见 [索引访问表达式](#354-索引访问表达式)

有关返回值：

- **若**为 `Identifier`，**则**返回该标识符的值
- **若**为 `Literal`，**则**返回其表示的值
- **若**为 `MemberAccessExpression`、`PointerMemberAccessExpression`**或** `MonomorphizationExpression`，**则**返回访问表达式的返回值（见 [访问表达式](#351-访问表达式)）
- **若**为 `IndexAccessExpression`，**则**返回其访问的内容（见 [索引访问表达式](#354-索引访问表达式)）

### 3.3 括号表达式

**括号表达式**是改变求值优先级的表达式，其语法如下：

```ebnf
ParenthesisExpression = "(" Expression ")" .
```

其中：

- **定义** `ParenthesisExpression` 为括号表达式
- 有关 `Expression`，见 [表达式](#31-表达式)

有关返回值：

- 将 `Expression` 的返回值作为括号表达式的返回值

### 3.4 类型转换表达式

**类型转换表达式**是以显式转换将值转换为目标类型的表达式，其格式如下：

```ebnf
TypeConversionExpression = "Cast" "<" Type ">" "(" Expression ")" .
```

其中：

- **定义** `Cast` 为类型转换表达式的引导符
- **定义** `Type` 为目标类型（见 [类型构造语法](#21-类型构造语法)）
- **定义** `Expression` 为被转换值（见 [表达式](#31-表达式)）

有关类型：

- 类型转换表达式的返回值类型**必须为** `Type`

有关解析：

- 解析**必须**优先选取接受被转换值的转换运算符（见 [运算符](#3101-运算符)）
- **当**不存在上述转换运算符**时**，解析**必须**按各类型页面的显式转换规则进行
- 被转换值的类型与 `Type` 之间**必须**存在显式转换
  - **否则**编译器**必须**报错

有关可用性：

- 显式转换**必须仅**经类型转换表达式进行（见 [核心设计哲学](#141-核心设计哲学)）
- **允许**携带 `implicitable` 的转换运算符在类型不匹配处被隐式调用（见 [implicitable 修饰符](#88-implicitable-修饰符)）
- 类型转换表达式**不得**被重载（见 [运算符重载](#3103-运算符重载)）

例如：

```novasharp
// 定义：函数 Main
constant Main(): integer(4)
{
    variable a: integer(4) = 5;

    // 合法：基本类型之间的显式转换
    variable b: integer(2) = Cast<integer(2)>(a);

    // 合法：布尔到数值的显式转换
    variable flag: boolean = true;
    variable n: integer(4) = Cast<integer(4)>(flag); // 1

    return 0;
}

// 定义：结构体 HSLColor
structure HSLColor
{
    // ...
}

// 定义：结构体 RGBColor
structure RGBColor
{
    extension
    {
        // 定义：转换运算符
        // 合法：转换目标类型与返回值类型一致
        operator RGBColor: function(from: HSLColor) RGBColor
        {
            // ...
        }
    }
}

// 合法：优先选取用户定义的转换运算符
variable hsl: HSLColor = HSLColor();
variable rgb: RGBColor = Cast<RGBColor>(hsl);
```

### 3.5 访问表达式

#### 3.5.1 访问表达式

**访问表达式**是描述对标识符或实例进行访问的表达式，其格式如下：

```ebnf
AccessExpression = MemberAccessExpression
                 | PointerMemberAccessExpression
                 | MonomorphizationExpression
                 | IndexAccessExpression .
```

其中：

- **定义** `AccessExpression` 为访问表达式
- **定义** `"."` 为成员访问运算符
- **定义** `"->"` 为指针成员访问运算符
- 有关 `MemberAccessExpression`，见 [成员访问表达式](#352-成员访问表达式)
- 有关 `PointerMemberAccessExpression`，见 [指针成员访问表达式](#353-指针成员访问表达式)
- 有关 `MonomorphizationExpression`，见 [单态化表达式](#92-单态化表达式)
- 有关 `IndexAccessExpression`，见 [索引访问表达式](#354-索引访问表达式)

#### 3.5.2 成员访问表达式

**成员访问表达式**是获取标识符、类型或实例的成员的表达式，其语法如下：

```ebnf
MemberAccessExpression = ( Identifier | Expression ) "." Name .
```

其中：

- **定义** `MemberAccessExpression` 为成员访问表达式
- **定义** `Identifier` 为访问源的标识符（见 [标识符](#14-标识符)）
- **定义** `Expression` 为访问源的表达式（见 [表达式](#31-表达式)）
- **定义** `"."` 为成员访问运算符
- **定义** `Name` 为成员名（见 [标识符](#14-标识符)）
  - 成员名**必须**指向访问源所属类型中的成员

有关类型：

- 访问源**必须**为标识符、类型**或**实例
- **定义**访问源所属类型为访问源所承载实例的类型
- **当**访问源为类型**时**，访问源所属类型**必须为**访问源自身
- 成员**必须**位于访问源所属类型**或**其继承链上
- **当**访问源为类型**时**，成员**必须**为 `static` 成员、枚举成员**或**变体无载荷状态（见 [static 修饰符](#816-static-修饰符)、[枚举](#274-枚举)、[变体](#275-变体)）
- **当**访问源**不为**类型**时**，成员**不得**为 `static` 成员（见 [static 修饰符](#816-static-修饰符)）

有关行为：

- **定义**成员访问为从访问源所属类型中解析并取得成员的行为
- 成员解析**必须**按如下顺序进行：
  1. 访问源所属类型的成员
  2. 访问源的基类成员（见 [类](#271-类)）
  3. 访问源实现的接口成员（见 [接口](#273-接口)）
- 方法的调用**必须**经成员访问表达式进行（见 [方法](#74-方法)）
- 函数字段的调用**必须**经成员访问表达式进行（见 [字段](#281-字段)）
- 访问器成员**不得**经成员访问表达式访问（见 [访问器](#282-访问器)）

有关返回值：

- **当**成员为字段**时**，将其值作为成员访问表达式的返回值
- **当**成员为常量**时**，将其值作为成员访问表达式的返回值
- **当**成员为访问器**时**，读取该访问器**并**将读取结果作为成员访问表达式的返回值（见 [访问器](#282-访问器)）

#### 3.5.3 指针成员访问表达式

**指针成员访问表达式**是获取标识符或实例所承载指针的目标实例的成员的表达式，其语法如下：

```ebnf
PointerMemberAccessExpression = ( Identifier | Expression ) "->" Name .
```

其中：

- **定义** `PointerMemberAccessExpression` 为指针成员访问表达式
- **定义** `Identifier` 为访问源的标识符（见 [标识符](#14-标识符)）
- **定义** `Expression` 为访问源的表达式（见 [表达式](#31-表达式)）
- **定义** `"->"` 为指针成员访问运算符
- **定义** `Name` 为成员名（见 [标识符](#14-标识符)）
  - 成员名**必须**指向指针的目标类型中的成员

有关类型：

- 访问源所承载实例的类型**必须**为指针类型（见 [指针类型构造器](#263-指针类型构造器)）
- 成员**必须**位于指针的目标类型**或**其继承链上
- 成员**不得**为 `static` 成员（见 [static 修饰符](#816-static-修饰符)）

有关行为：

- **定义**目标实例为访问源所承载实例的指针所指向的实例
- 指针成员访问表达式**必须**先解引用访问源**并**在目标实例上访问成员
- **当**省略目标类型**时**，**禁止**使用指针成员访问表达式（见 [指针类型构造器](#263-指针类型构造器)）
- 更多，见 [成员访问表达式](#352-成员访问表达式)

有关赋值：

- **当**指针成员访问表达式为赋值目标**时**，**必须**覆盖目标成员的存储

#### 3.5.4 索引访问表达式

**索引访问表达式**是通过索引获取标识符或实例的内容的表达式，其语法如下：

```ebnf
IndexAccessExpression = ( Identifier | Expression ) "[" Expression "]" .
```

其中：

- **定义** `IndexAccessExpression` 为索引访问表达式
- **定义** `Identifier` 为访问源的标识符（见 [标识符](#14-标识符)）
- **定义** `Expression` 为访问源的表达式（见 [表达式](#31-表达式)）
- **定义**第二个 `Expression` 为索引表达式（见 [表达式](#31-表达式)）
  - 索引表达式的返回值类型**必须**为无符号整数类型**或**可隐式转换为无符号整数类型

有关类型：

- 访问源所承载实例的类型**必须**为数组类型（见 [数组类型构造器](#262-数组类型构造器)）**或**携带索引访问器（见 [运算符](#3101-运算符)）
- **当**访问源所承载实例的类型**不为**数组类型**时**，该类型**必须**携带索引访问器（见 [运算符](#3101-运算符)）

有关行为：

- **当**访问源所承载实例的类型为数组类型**时**，**必须**执行内建索引访问，**并**将数组元素作为索引访问表达式的返回值（见 [数组类型构造器](#262-数组类型构造器)）
- **否则必须**将索引表达式的返回值代入索引访问器**并**执行（见 [运算符](#3101-运算符)）

有关返回值：

- **当**访问源所承载实例的类型为数组类型**时**，返回值类型**必须**为数组元素类型（见 [数组类型构造器](#262-数组类型构造器)）
- **当**访问源的类型携带索引访问器**时**，返回值类型**必须**为索引访问器的目标类型（见 [运算符](#3101-运算符)）

有关赋值：

- **当**索引访问表达式为赋值目标**且**访问源所承载实例的类型为数组类型**时**，赋值**必须**覆盖数组元素所占内存
- **当**索引访问表达式为赋值目标**且**访问源的类型携带索引访问器**时**，赋值**必须**调用该访问器的 `set`（见 [运算符](#3101-运算符)）

有关越界：

- **定义**越界为索引表达式的返回值不小于数组大小的情形（见 [数组类型构造器](#262-数组类型构造器)）
- 内建索引访问**必须**校验索引是否越界
  - **当**越界**时**，**必须**产生 `OutOfRangeException` 运行时异常（见 [异常处理](#491-异常处理)）
- **当**编译器判定索引必然越界**时**，编译器**必须**予以 Warning
- **当**编译器判定索引不会越界**时**，编译器**必须**移除越界校验，**但**以下情况除外：
  - 该索引位于 `verbatim` 块中（见 [verbatim 修饰符](#89-verbatim-修饰符)）

### 3.6 函数调用表达式

**函数调用表达式**是调用函数的表达式，其语法如下：

```ebnf
FunctionCallExpression = Expression "(" Arguments ")" .
```

其中：

- **定义** `FunctionCallExpression` 为函数调用表达式
- **定义** `Expression` 为被调用者表达式（见 [表达式](#31-表达式)）
  - 被调用者表达式的返回值类型**必须**为函数类型（见 [函数类型构造器](#264-函数类型构造器)）
  - **当**被调用者表达式为标识符**时**，该标识符**必须**指向一个可访问的函数**或**编译期函数（见 [标识符](#14-标识符)、[编译期边界](#106-编译期边界)）
  - **当**被调用者表达式为成员访问表达式**时**，**必须**经成员访问表达式调用函数（见 [成员访问表达式](#352-成员访问表达式)）
- 有关 `Arguments`，见 [实参](#73-实参)
- 有关 `FunctionLiteral`，见 [函数](#1710-函数)

有关重载：

- **当**被调用者表达式为标识符**且**其指向多个同名函数常量**时**，**必须**经重载决议选取被调用者（见 [重载决议](#75-重载决议)）

有关实参：

- **允许**省略实参，**当且仅当**使用函数标识符
- 更多，见 [实参](#73-实参)

有关返回值：

- 将函数的返回值作为函数调用表达式的返回值

例如：

```novasharp
// 定义：函数 Calculate
constant Calculate(a: integer(4), b: integer(4), c: integer(4) = 0): integer(4)
{
    return a + b + c;
}

// 定义：函数 Scale
constant Scale(value: &integer(4), factor: integer(4))
{
    value = value * factor;
}

// 定义：函数 Invoke
constant Invoke(callback: function())
{
    callback();
}

constant Main(): integer(4)
{
    // 合法：基本位置参数调用
    variable result: integer(4) = Calculate(1, 2, 3); // result = 6

    // 合法：省略默认参数
    variable partial: integer(4) = Calculate(1, 2); // c 使用默认值 0，result = 3

    // 合法：命名参数调用
    variable named: integer(4) = Calculate(a: 1, b: 2, c: 3);

    // 合法：命名参数乱序
    variable reordered: integer(4) = Calculate(c: 3, a: 1, b: 2);

    // 合法：混合调用，位置参数在前，命名参数在后
    variable mixed: integer(4) = Calculate(1, b: 2, c: 3);

    // 合法：引用参数调用
    variable value: integer(4) = 5;
    Scale(value, 3); // value 变为 15

    // 合法：函数字面量直接调用
    variable direct: integer(4) =
        (x: integer(4), y: integer(4)) integer(4) =>
        {
            return x * y;
        } (3, 4); // result = 12

    // 合法：无参调用
    Invoke(() => { });

    // 非法：命名参数后接位置参数
    // variable bad: integer(4) = Calculate(a: 1, 2, 3);
    // 错误：命名参数后的所有参数必须携带参数名

    // 定义：函数 PrintNothing
    constant PrintNothing()
    {
        return;
    }

    // 合法：经函数指针调用
    variable functionPrinter: pointer function() = &PrintNothing;
    (*functionPrinter)();

    // 非法：重复指定同一参数
    // variable bad: integer(4) = Calculate(1, a: 2, b: 3);
    // 错误：参数 a 被多次指定

    // 非法：省略无默认值的参数
    // variable bad: integer(4) = Calculate(1);
    // 错误：参数 b 无默认值且未被提供

    // 非法：调用非函数表达式
    // variable value: integer(4) = 1;
    // variable bad: integer(4) = value(1, 2);
    // 错误：被调用者表达式的返回值类型必须为函数类型

    return 0;
}
```

### 3.7 构造表达式

**构造表达式**是构造实例的表达式，其语法如下：

```ebnf
ConstructionExpression = ConstructedTypeName "(" Arguments ")" .

ConstructedTypeName = Type | MonomorphizationExpression .
```

其中：

- **定义** `ConstructionExpression` 为构造表达式
- **定义** `ConstructedTypeName` 为被构造类型名
- **定义** `Type` 为被构造类型（见 [类型构造语法](#21-类型构造语法)）
- **定义** `MonomorphizationExpression` 为携带泛型实参的被构造类型（见 [单态化表达式](#92-单态化表达式)）
- 有关 `Arguments`，见 [实参](#73-实参)

有关类型：

- 被构造类型**必须**为类（见 [类](#271-类)）**或**结构体（见 [结构体](#272-结构体)）
- 被构造类型**不得**为接口（见 [接口](#273-接口)）
- 被构造类型**不得**为枚举（见 [枚举](#274-枚举)）
- 变体（见 [变体](#275-变体)）和共同体（见 [共同体](#276-共同体)）**必须**经成员构造表达式构造（见 [成员构造表达式](#38-成员构造表达式)）
- 被构造类型**不得**为基本类型（见 [基本类型](#22-基本类型)）
- 被构造类型**不得**为类型构造器（见 [类型构造器](#261-类型构造器)）
- 被构造类型**必须**声明与 `Arguments` 匹配的构造函数（见 [类](#271-类)、[结构体](#272-结构体)）
- **允许**省略实参，**当且仅当**存在参数列表为空的构造函数

有关内存分配：

- 构造表达式**不得**指定内存分配方式（见 [内存分配](#111-内存分配)）
- **当**构造表达式位于定义或赋值的右侧**时**，实例**必须**被构造到该定义或赋值的目标存储中
  - 上述构造**不得**先构造中间实例，再覆盖目标存储
- **当**构造表达式不位于定义或赋值的右侧**时**，实例**必须**由编译器分配存储（见 [内存分配](#111-内存分配)）

有关行为：

- 以构造目标存储为 `this`、以 `Arguments` 为其余实参，调用构造函数
- 调用构造函数前，**必须**按被构造类型的生命周期完成成员初始化（见 [类](#271-类)、[结构体](#272-结构体)）

有关返回值：

- 构造表达式的返回值为构造完成的实例

例如：

```novasharp
// 定义：结构体 Point
structure Point
{
    public X: integer(4);
    public Y: integer(4);

    extension
    {
        public constant Construct(this: &Point, x: integer(4), y: integer(4))
        {
            this.X = x;
            this.Y = y;
        }
    }
}

// 定义：类 Cat
class Cat
{
    public Legs: integer(4);
}

// 定义：函数 Main
constant Main(): integer(4)
{
    // 合法：构造值类型实例
    variable origin: Point = Point(0, 0);

    // 合法：以默认构造函数构造引用类型实例
    variable cat: Cat = Cat();

    // 合法：构造结果覆盖目标存储
    origin = Point(1, 2);

    return 0;
}

// 非法：接口不可构造
// variable bad: IValue = IValue();
// 错误：被构造类型不得为接口

// 非法：实参不匹配
// variable bad: Point = Point(1);
// 错误：没有与实参匹配的构造函数

// 非法：构造表达式指定内存分配方式
// variable bad: Point = allocate Point(1, 2);
// 错误：构造表达式不得指定内存分配方式
```

### 3.8 成员构造表达式

**成员构造表达式**是以成员构造宿主实例的表达式，其语法如下：

```ebnf
MemberConstructionExpression = ConstructedTypeName "." Name "(" Expression ")" .
```

其中：

- **定义** `MemberConstructionExpression` 为成员构造表达式
- **定义** `ConstructedTypeName` 为被构造类型名（见 [构造表达式](#37-构造表达式)）
- **定义** `Name` 为成员名（见 [标识符](#14-标识符)）
- **定义** `Expression` 为成员值表达式（见 [表达式](#31-表达式)）

有关类型：

- 被构造类型**必须**为变体（见 [变体](#275-变体)）**或**共同体（见 [共同体](#276-共同体)）
- `Name` **必须**为被构造类型的成员
- **当**被构造类型为变体**时**，`Name` **必须**为携带载荷的状态（见 [变体](#275-变体)）
- `Expression` 的返回值类型**必须**等于该成员的类型**或**可隐式转换为该成员的类型

有关解析：

- **当**成员访问的访问源为类型**且**访问目标为携带值的成员**时**，**判定**其为成员构造表达式
- **当**成员访问的访问源为类型**且**访问目标为不携带值的成员**时**，**判定**其为成员访问表达式（见 [成员访问表达式](#352-成员访问表达式)）
- 成员构造表达式**不得**被解析为函数调用表达式（见 [函数调用表达式](#36-函数调用表达式)）

有关内存分配：

- 成员构造表达式**不得**指定内存分配方式（见 [内存分配](#111-内存分配)）
- **当**成员构造表达式位于定义或赋值的右侧**时**，实例**必须**被构造到该定义或赋值的目标存储中
  - 上述构造**不得**先构造中间实例，再覆盖目标存储
- **当**成员构造表达式不位于定义或赋值的右侧**时**，实例**必须**由编译器分配存储（见 [内存分配](#111-内存分配)）

有关行为：

- **当**被构造类型为变体**时**，上述成员**必须**成为实例的当前状态，**且**实例的载荷**必须**为 `Expression` 的返回值（见 [变体](#275-变体)）
- **当**被构造类型为共同体**时**，上述成员**必须**从实例内存起始点开始写入，**且**其余成员**不得**被初始化（见 [共同体](#276-共同体)）

有关返回值：

- 成员构造表达式的返回值为构造完成的实例

例如：

```novasharp
// 定义：结构体 Color
structure Color
{
    public R: unsigned integer(1);
    public G: unsigned integer(1);
    public B: unsigned integer(1);
    public A: unsigned integer(1);

    extension
    {
        public constant Construct(this: &Color, r: unsigned integer(1), g: unsigned integer(1), b: unsigned integer(1), a: unsigned integer(1))
        {
            this.R = r;
            this.G = g;
            this.B = b;
            this.A = a;
        }
    }
}

// 定义：共同体 Pixel
union Pixel
{
    RGBA: Color;
    Packed: unsigned integer(4);
    Channels[4]: integer(1);
}

// 定义：变体 Status
variant Status
{
    Idle;
    Loading: integer(4);
    Done;
}

// 定义：函数 Main
constant Main(): integer(4)
{
    // 合法：以共同体成员构造
    variable pixel: Pixel = Pixel.RGBA(Color(1, 2, 3, 4));

    // 合法：成员构造与堆分配组合
    allocate heapPixel: Pixel = Pixel.RGBA(Color(1, 2, 3, 4));
    dispose heapPixel;

    // 合法：以携带载荷的变体状态构造
    variable status: Status = Status.Loading(50);

    // 合法：无载荷状态表现为成员值，不经构造
    variable done: Status = Status.Done;

    return 0;
}

// 非法：无载荷状态经成员构造表达式构造
// variable bad: Status = Status.Done();
// 错误：Done 不携带载荷，不得经成员构造表达式构造

// 非法：实参类型与成员类型不匹配
// variable bad: Pixel = Pixel.RGBA(1);
// 错误：RGBA 的类型为 Color

// 非法：成员不存在
// variable bad: Pixel = Pixel.Unknown(Color(1, 2, 3, 4));
// 错误：Unknown 不是 Pixel 的成员
```

### 3.9 is 表达式

**is 表达式**是判定形态的表达式，其语法如下：

```ebnf
IsExpression = Expression "is" IsTarget .

IsTarget = Identifier | SpecialFloatTarget .

SpecialFloatTarget = IllegalLiteral | InfinityTarget .

InfinityTarget = [ "-" ] "infinite" .
```

其中：

- **定义** `IsExpression` 为 is 表达式
- **定义** `IsTarget` 为判定目标
- **定义** `Identifier` 为形态标识符（见 [标识符](#14-标识符)）
- **定义** `SpecialFloatTarget` 为特殊浮点判定目标
- **定义** `IllegalLiteral` 为非法值字面量（见 [非法值](#1712-非法值)）
- **定义** `InfinityTarget` 为无穷判定目标
- **定义** `Expression` 为左操作数（见 [表达式](#31-表达式)）

有关类型：

- `Identifier` **必须**指向类类型（见 [类](#271-类)）、接口（见 [接口](#273-接口)）**或**变体成员（见 [变体](#275-变体)）
- `IsExpression` 的返回值类型**必须为** `boolean`
- **当** `IsTarget` 为 `SpecialFloatTarget` **时**， `Expression` 的类型**必须**为浮点类型（见 [基本类型](#22-基本类型)）

有关判定：

- **当** `Identifier` 指向类类型**时**，**判定**其为真，**当且仅当**左操作数的运行期类型为该类类型**或**派生自该类类型
- **当** `Identifier` 指向接口**时**，**判定**其为真，**当且仅当**左操作数的运行期类型实现该接口
- **当** `Identifier` 指向变体成员**时**，**判定**其为真，**当且仅当**左操作数的当前状态为该成员
- **当** `SpecialFloatTarget` 为 `IllegalLiteral` **时**，**判定**其为真，**当且仅当**左操作数的值为 IEEE 754 非数
- **当** `SpecialFloatTarget` 为 `InfinityTarget` **时**，**判定**其为真，**当且仅当**左操作数的值为 IEEE 754 无穷，**且**符号与 `InfinityTarget` 一致
- **若**左操作数的静态类型与判定目标不可能成立，**则** `IsExpression` 的返回值为 `false`

有关可重载性：

- `is` **不得**被重载（见 [运算符重载](#3103-运算符重载)）
- `is` **不得**受运算符重载影响

例如：

```novasharp
// 定义：类 Animal
abstract class Animal
{
}

// 定义：类 Cat
class Cat: Animal
{
}

// 定义：接口 IComparable
interface IComparable
{
}

// 定义：变体 Status
variant Status
{
    Idle;
    Loading: integer(4);
    Done;
}

// 定义：函数 Main
constant Main(): integer(4)
{
    variable animal: Animal = Cat();

    // 合法：类类型判定
    variable isCat: boolean = animal is Cat; // true

    // 合法：接口判定
    variable comparable: boolean = animal is IComparable; // false

    // 合法：变体成员判定
    variable status: Status = Status.Loading(50);
    variable loading: boolean = status is Status.Loading; // true

    // 合法：非数判定
    variable ratio: float(4) = illegal;
    variable bad: boolean = ratio is illegal; // true

    // 合法：无穷判定
    variable upper: float(4) = infinite;
    variable positive: boolean = upper is infinite; // true
    variable negative: boolean = -infinite is -infinite; // true
    variable mixed: boolean = upper is -infinite; // false

    // 合法：静态上不可能成立，恒假
    variable impossible: boolean = 1 is Cat; // false

    return 0;
}

// 非法：判定目标不是类类型、接口或变体成员
// variable bad: boolean = 1 is integer(4);
// 错误：is 表达式的形态标识符必须指向类类型、接口或变体成员

// 非法：以非浮点类型判定非数
// variable bad: boolean = 1 is illegal;
// 错误：非法值字面量的左操作数类型必须为浮点类型
```

### 3.10 运算符

#### 3.10.1 运算符

**运算符**是为运算符提供运算行为的标识符种类，其格式如下：

```ebnf
OperatorDefinition = { Modifier } "operator" OperatorHead [ "=" Expression | Block | AccessorMembers ] .

OperatorHead      = OperatorShorthand | OperatorNotation [ ":" Type ] .

OperatorShorthand = OperatorSymbol "(" [ Parameters ] ")" [ ":" Type ] .

OperatorNotation  = OperatorSymbol | IndexerNotation | ConstructedTypeName .

OperatorSymbol = "+" | "-" | "*" | "/" | "%" | "==" | ">" | "<" | "??" .

IndexerNotation = "[" Parameters "]" .
```

其中：

- **定义** `OperatorDefinition` 为运算符定义
- **定义** `OperatorHead` 为运算符头部
- **定义** `OperatorShorthand` 为运算符简写
- **定义** `OperatorNotation` 为运算符记法
- **定义** `OperatorSymbol` 为运算符符号
- **定义** `IndexerNotation` 为索引记法
- **定义** `ConstructedTypeName` 为转换目标类型（见 [构造表达式](#37-构造表达式)）
- **定义** `Modifier` 为修饰符（见 [修饰符](#81-修饰符)）
- **定义** `Type` 为运算符类型（见 [类型构造语法](#21-类型构造语法)）
- **定义** `Expression` 为初始化表达式（见 [表达式](#31-表达式)）
- **定义** `Block` 为运算符的体（见 [代码块](#42-代码块)）
- 有关 `Parameters`，见 [参数](#72-参数)
- 有关 `AccessorMembers`，见 [访问器](#282-访问器)

有关运算符定义：

- 修饰符列表**必须**位于 `operator` 之前
- 运算符记法**必须**与 `operator` 相邻，**且**其间**不得**存在换行**或**注释
- 运算符符号**必须**以符号本身书写，**不得**加引号
- 运算符简写**允许**用于 `OperatorSymbol`
- **当**使用运算符简写**时**，其**必须**展开为 `OperatorNotation ":" "function(" Parameters ")" Type`
- **当**使用运算符简写且省略 `:` **时**，返回类型**必须**为空类型，**不得**推断
- `:` 与 `=` **必须**至少出现一个
- 运算符定义**必须**以语句终止符终止（见 [语句终止](#18-语句终止)）
- 除接口声明体中的契约运算符外，运算符定义**必须**声明在扩展块内（见 [扩展](#283-扩展)）
- **定义**运算符的基础可访问性为 `public`
- **禁止**运算符定义携带可访问性修饰符（见 [可访问性修饰符](#82-可访问性修饰符)）
- **当**运算符定义声明在扩展块内**时**，其参数**允许**访问扩展目标类型的私有成员
- 同一类型内**不得**重复定义同一运算符
  - **当**两个运算符定义具有**相同**的运算符记法和参数列表**时**，**判定**二者为同一运算符定义

有关类型：

- **当**出现 `:` **时**，运算符类型**必须为** `Type`
- **当**不使用运算符简写且省略 `:` **时**，运算符类型**必须**由 `=` 的返回值推断
- 运算符类型**必须**为函数类型（见 [函数类型构造器](#264-函数类型构造器)）
- **当**运算符记法不是索引记法**时**，运算符类型**必须**包含一个**或**两个参数
  - **当**包含两个参数**时**，**判定**其为二元运算符
    - 第一个参数**必须**接受左操作数
    - 第二个参数**必须**接受右操作数
  - **当**包含一个参数**时**，**判定**其为一元运算符
    - 该参数**必须**接受操作数
- 一元运算符**必须仅**为 `-`、`??` **或**转换运算符（见 [取负表达式](#3104-取负表达式)、[空值合并表达式](#31027-空值合并表达式)、[类型转换表达式](#34-类型转换表达式)）
- 运算符类型**不得**包含 `this` 参数（见 [方法](#74-方法)）
- 运算符类型的返回值类型**必须**为运算结果的类型，**但** `??` 运算符除外
- **当**运算符记法为索引记法**时**， `:` **必须**出现，**且**运算符类型**必须**以 `Parameters` 为参数列表、以 `Type` 为返回值类型
- **当**运算符记法为索引记法**时**，索引参数**允许**任意数量
- **当**运算符记法为转换目标类型**时**，运算符类型的返回值类型**必须**与转换目标类型相同
  - 参数**必须**接受被转换值

有关 `??` 决策运算符：

- `??` 运算符的运算符类型**必须**包含一个参数，**且**其返回值类型**必须为** `Result<TValue; TAlternative>`（见 [空值合并表达式](#31027-空值合并表达式)、[Built-In Library 完整内容](#152-built-in-library-完整内容)）
- 该参数**必须**接受左操作数
- `??` 表达式提供的右侧续体**不得**作为 `??` 运算符的参数
- `??` 运算符**不得**以普通一元运算符的形式调用

有关索引访问器：

- **定义**索引访问器为以索引记法声明的运算符（见 [索引访问表达式](#354-索引访问表达式)）
- 索引访问器**必须**出现在 class **或** structure 的扩展块内；接口声明体中的索引访问器为契约，直接声明
- 索引访问器的体**必须**为 `AccessorMembers`（见 [访问器](#282-访问器)）
- 索引访问器的访问器成员是方法，**且** `this` 参数**必须**显式书写（见 [方法](#74-方法)）
- 索引访问器**不得**以 `static` 修饰（见 [static 修饰符](#816-static-修饰符)）
- 索引访问器的 `get` 与 `set` **必须**提供初始化表达式（见 [访问器](#282-访问器)）

有关转换运算符：

- **定义**转换运算符为以转换目标类型声明的运算符
- 转换运算符**必须**经类型转换表达式调用（见 [类型转换表达式](#34-类型转换表达式)）
- **当**转换运算符携带 `implicitable` **时**，该转换**允许**被隐式调用（见 [implicitable 修饰符](#88-implicitable-修饰符)）

有关重载：

- **允许**多个具有同一运算符符号的运算符定义共存
- **允许**同一运算符符号定义一个一元运算符和一个二元运算符
- 同一运算符符号的运算符定义之间的参数类型**必须**互不相同
- 有关重载解析与分派，见 [运算符重载](#3103-运算符重载)

例如：

```novasharp
// 定义：结构体 Vector2
structure Vector2
{
    public X: float(4);
    public Y: float(4);

    extension
    {
        public constant Construct(this: &Vector2, x: float(4), y: float(4))
        {
            this.X = x;
            this.Y = y;
        }

        // 定义：加法重载
        // 合法：二元加法重载
        operator +(left: Vector2, right: Vector2): Vector2
        {
            return Vector2(left.X + right.X, left.Y + right.Y);
        }
    }
}

// 定义：结构体 Buffer
structure Buffer
{
    private Items[8]: integer(4);
    private Count: integer(4);

    extension
    {
        // 合法：索引访问器写在扩展块内
        operator [index: unsigned integer(4)]: integer(4)
        {
            get = (this: &Buffer, index: unsigned integer(4)) integer(4) => { return this.Items[index]; }
            set = (this: &Buffer, index: unsigned integer(4), value: integer(4)) => { this.Items[index] = value; }
        }

        // 合法：运算符也可以写在扩展块内
        operator ==(left: Buffer, right: Buffer): boolean
        {
            return left.Count == right.Count;
        }
    }
}

// 非法：参数数量不为一个或两个
// operator -: function(a: Vector2, b: Vector2, c: Vector2) Vector2 { }
// 错误：运算符类型必须包含一个或两个参数

// 非法：含 this 参数
// operator +: function(this: Vector2, right: Vector2) Vector2 { }
// 错误：运算符类型不得包含 this 参数

// 非法：符号不在可重载集合中
// operator &: function(left: Vector2, right: Vector2) Vector2 { }
// 错误：& 不可重载

// 非法：携带可访问性修饰符
// public operator +: function(left: Vector2, right: Vector2) Vector2 { }
// 错误：运算符定义不得携带可访问性修饰符

// 非法：在全局重复定义
// operator +: function(left: Vector2, right: Vector2) Vector2 { }
// 错误：运算符定义不得在全局重复

// 非法：索引访问器出现在类型声明体外
// operator [index: unsigned integer(4)]: integer(4) { get; set; }
// 错误：索引访问器必须出现在扩展块内
```

#### 3.10.2 运算符优先级

**运算符优先级**是表达式结合次序的规范。由以下优先级层次组成：

| 优先级     | 运算符                                                                                                                                                                                                                                              |
| ---------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| 1（最高）  | 括号（见 [括号表达式](#33-括号表达式)）、值表达式（见 [值表达式](#32-值表达式)）、编译期表达式（见 [编译期表达式](#103-编译期表达式)）、类型转换（见 [类型转换表达式](#34-类型转换表达式)）                                                         |
| 2          | 后缀：成员访问（见 [成员访问表达式](#352-成员访问表达式)）、指针成员访问（见 [指针成员访问表达式](#353-指针成员访问表达式)）、索引访问（见 [索引访问表达式](#354-索引访问表达式)）、单态化（见 [单态化表达式](#92-单态化表达式)）                   |
| 3          | 调用与构造：函数调用（见 [函数调用表达式](#36-函数调用表达式)）、构造（见 [构造表达式](#37-构造表达式)）、成员构造（见 [成员构造表达式](#38-成员构造表达式)）                                                                                       |
| 4          | 一元：取负（见 [取负表达式](#3104-取负表达式)）、逻辑非（见 [逻辑非表达式](#3105-逻辑非表达式)）、按位取反（见 [按位取反表达式](#3106-按位取反表达式)）、引用（见 [引用表达式](#3107-引用表达式)）、解引用（见 [解引用表达式](#3108-解引用表达式)） |
| 5          | 乘法（见 [乘法表达式](#3109-乘法表达式)）、除法（见 [除法表达式](#31010-除法表达式)）、求余（见 [求余表达式](#31011-求余表达式)）                                                                                                                   |
| 6          | 加法（见 [加法表达式](#31012-加法表达式)）、减法（见 [减法表达式](#31013-减法表达式)）                                                                                                                                                              |
| 7          | 逻辑左移（见 [逻辑左移表达式](#31014-逻辑左移表达式)）、逻辑右移（见 [逻辑右移表达式](#31015-逻辑右移表达式)）                                                                                                                                      |
| 8          | 小于（见 [小于表达式](#31016-小于表达式)）、大于（见 [大于表达式](#31017-大于表达式)）、小于等于（见 [小于等于表达式](#31018-小于等于表达式)）、大于等于（见 [大于等于表达式](#31019-大于等于表达式)）、`is`（见 [is 表达式](#39-is-表达式)）       |
| 9          | 相等（见 [相等表达式](#31020-相等表达式)）、不等（见 [不等表达式](#31021-不等表达式)）                                                                                                                                                              |
| 10         | 按位与（见 [按位与表达式](#31022-按位与表达式)）                                                                                                                                                                                                    |
| 11         | 按位异或（见 [按位异或表达式](#31023-按位异或表达式)）                                                                                                                                                                                              |
| 12         | 按位或（见 [按位或表达式](#31024-按位或表达式)）                                                                                                                                                                                                    |
| 13         | 逻辑和（见 [逻辑和表达式](#31025-逻辑和表达式)）                                                                                                                                                                                                    |
| 14         | 逻辑或（见 [逻辑或表达式](#31026-逻辑或表达式)）                                                                                                                                                                                                    |
| 15         | `??`（见 [空值合并表达式](#31027-空值合并表达式)）                                                                                                                                                                                                  |
| 16（最低） | `?:`（见 [条件表达式](#31028-条件表达式)）                                                                                                                                                                                                          |

其中：

- **定义**运算符优先级为表达式结合次序的规范
- **定义**优先级层次为上表的一行
- 相邻层次之间，较高优先级**必须**先结合
- 同一层次的运算符**必须**左结合
- **当**运算符为 `??` **或** `?:` **时**，其**必须**右结合
- **允许**括号表达式改变求值优先级（见 [括号表达式](#33-括号表达式)）

有关一元运算符：

- 后缀运算符**必须**先于一元运算符结合
- 一元运算符**必须**先于乘法运算符结合
- 一元运算符**必须**与其操作数先于任何二元运算符结合

有关同形运算符：

- **当** `&`、`*`、`^` **或** `-` 出现在操作数位置**时**，**判定**其为一元运算符
- **当** `&`、`*`、`^` **或** `-` 出现在操作数之后**时**，**判定**其为二元运算符
  - `&` 为按位与（见 [按位与表达式](#31022-按位与表达式)）**或**引用（见 [引用表达式](#3107-引用表达式)）
  - `*` 为乘法（见 [乘法表达式](#3109-乘法表达式)）**或**解引用（见 [解引用表达式](#3108-解引用表达式)）
  - `^` 为按位异或（见 [按位异或表达式](#31023-按位异或表达式)）**或**按位取反（见 [按位取反表达式](#3106-按位取反表达式)）
  - `-` 为减法（见 [减法表达式](#31013-减法表达式)）**或**取负（见 [取负表达式](#3104-取负表达式)）

例如：

```novasharp
// 定义：类 Cat
class Cat
{
}

// 定义：函数 Main
constant Main(): integer(4)
{
    // 合法：取负先于乘法
    variable a: integer(4) = -2 * 3; // -6

    // 合法：乘法先于加法
    variable b: integer(4) = 1 + 2 * 3; // 7

    // 合法：加法先于左移
    variable c: integer(4) = 1 + 2 << 3; // (1 + 2) << 3

    // 合法：is 先于相等
    variable d: boolean = 1 is Cat == false; // (1 is Cat) == false

    // 合法：括号改变求值优先级
    variable e: integer(4) = (1 + 2) * 3; // 9

    return 0;
}
```

有关求值顺序：

- 有关各子表达式之间的求值顺序，见 [表达式](#31-表达式)

#### 3.10.3 运算符重载

**运算符重载**是为运算符提供符合自定义类型的运算行为的机制。由以下重载组成：

| 重载         | 符号        | 要求方                                  |
| ------------ | ----------- | --------------------------------------- |
| 加法重载     | `+`         | [加法表达式](#31012-加法表达式)         |
| 减法重载     | `-`         | [减法表达式](#31013-减法表达式)         |
| 乘法重载     | `*`         | [乘法表达式](#3109-乘法表达式)          |
| 除法重载     | `/`         | [除法表达式](#31010-除法表达式)         |
| 求余重载     | `%`         | [求余表达式](#31011-求余表达式)         |
| 相等重载     | `==`        | [相等表达式](#31020-相等表达式)         |
| 大于重载     | `>`         | [大于表达式](#31017-大于表达式)         |
| 小于重载     | `<`         | [小于表达式](#31016-小于表达式)         |
| 取负重载     | `-`（一元） | [取负表达式](#3104-取负表达式)          |
| 索引访问器   | `[...]`     | [索引访问表达式](#354-索引访问表达式)   |
| 转换运算符   | 类型名      | [类型转换表达式](#34-类型转换表达式)    |
| 空值合并重载 | `??`        | [空值合并表达式](#31027-空值合并表达式) |

其中：

- **定义**运算符重载为：为运算符提供符合自定义类型的运算行为的机制
- **定义**某符号的重载为符号为该符号的运算符定义（见 [运算符](#3101-运算符)）
- 运算符重载**必须**以运算符定义声明（见 [运算符](#3101-运算符)）
- 运算符重载**必须**在编译期解析

有关可重载集合：

- 可重载的运算符**必须仅**为上表的十二个
- 一元重载**必须仅**为取负重载、`??` 重载**或**转换运算符
- 按位运算符（见 [按位与表达式](#31022-按位与表达式)）、逻辑运算符（见 [逻辑和表达式](#31025-逻辑和表达式)）和移位运算符（见 [逻辑左移表达式](#31014-逻辑左移表达式)）**不得**被重载
- 运算符符号**必须**与对应的重载一致

有关派生运算符：

- **定义** `!=` 为 `==` 的派生运算符
- **定义** `<=`、`>=` 为 `<`、`>` 的派生运算符
- 派生运算符**不得**被定义为运算符
- **当** `==` 的结果为 `false` **时**，`!=` **必须为** `true`；**否则** `!=` **必须为** `false`
- **当** `<` 的结果为 `true` **或** `==` 的结果为 `true` **时**，`<=` **必须为** `true`；**否则** `<=` **必须为** `false`
- **当** `>` 的结果为 `true` **或** `==` 的结果为 `true` **时**，`>=` **必须为** `true`；**否则** `>=` **必须为** `false`
- 上述形式**必须**遵循 IEEE 754，其中非数与任何值都不相等，包括其自身（见 [基本类型](#22-基本类型)）
  - `<=` **不得**以 `>` 的取反为定义
  - **当**操作数为非数**时**，`>` 的取反为 `true`，而 `<=` **必须为** `false`

有关分派：

- 运算符分派**必须**按重载决议进行（见 [重载决议](#75-重载决议)），其中被重载的名为运算符符号
- 分派**必须**按运算符定义的参数数量区分一元与二元（见 [运算符](#3101-运算符)）
- 上述分派**必须**在编译期完成

有关派生：

- 不等表达式（见 [不等表达式](#31021-不等表达式)）、大于等于表达式（见 [大于等于表达式](#31019-大于等于表达式)）和小于等于表达式（见 [小于等于表达式](#31018-小于等于表达式)）**不得**要求自己的重载
- 上述表达式**必须**以上表的重载代入自身的脱糖形式

有关语言内置重载：

- **定义**语言内置重载为由编译器固有提供的运算符重载
- **定义**用户定义重载为以运算符定义声明的运算符重载（见 [运算符](#3101-运算符)）
- 语言内置重载**必须**以编译器固有的方式提供，**不得**以运算符定义书写（见 [运算符](#3101-运算符)）
- 语言内置重载**不得**由 Built-In Library 提供（见 [Built-In Library 完整内容](#152-built-in-library-完整内容)）
- 语言内置重载的集合**必须**由各类型页面定义（见 [基本类型](#22-基本类型)、[变体](#275-变体)）
- 语言内置重载的行为**必须**由各类型页面定义（见 [基本类型](#22-基本类型)）
- 分派**必须**将语言内置重载和用户定义重载同等对待

例如：

```novasharp
// 定义：结构体 Vector2
structure Vector2
{
    public X: float(4);
    public Y: float(4);

    extension
    {
        public constant Construct(this: &Vector2, x: float(4), y: float(4))
        {
            this.X = x;
            this.Y = y;
        }

        // 定义：加法重载
        operator +(left: Vector2, right: Vector2): Vector2
        {
            return Vector2(left.X + right.X, left.Y + right.Y);
        }
    }
}

// 非法：运算符定义在扩展块之外
// operator +: function(left: Vector2, right: Vector2) Vector2 { return left; }
// 错误：运算符定义必须声明在扩展块内

// 定义：函数 Main
constant Main(): integer(4)
{
    variable a: Vector2 = Vector2(1, 2);
    variable b: Vector2 = Vector2(3, 4);

    // 合法：匹配加法重载
    variable c: Vector2 = a + b;

    // 非法：无匹配的加法重载
    // variable bad: Vector2 = a + 1;
    // 错误：没有符合左、右表达式类型的加法重载
}
```

#### 3.10.4 取负表达式

**取负表达式**是对操作数取算术负值的表达式，其语法如下：

```ebnf
NegateExpression = "-" Expression .
```

其中：

- **定义** `NegateExpression` 为取负表达式
- **定义** `Expression` 为操作数（见 [表达式](#31-表达式)）

有关类型：

- 操作数的类型**必须**存在取负重载（见 [运算符重载](#3103-运算符重载)）
- 取负表达式的返回值类型**必须**为取负重载的返回值类型

有关行为：

- 取负**必须**经取负重载分派（见 [运算符重载](#3103-运算符重载)）
- 上述分派**必须**在编译期完成
- 有关基本类型的取负行为，见 [基本类型](#22-基本类型)

例如：

```novasharp
// 定义：函数 Main
constant Main(): integer(4)
{
    // 合法：整数字面量取负
    variable negative: integer(4) = -5;

    // 合法：变量取负
    variable value: integer(4) = 7;
    variable flipped: integer(4) = -value; // -7

    // 合法：负无穷
    variable lower: float(4) = -infinite;

    // 非法：不存在取负重载
    // variable bad: boolean = -true;
    // 错误：操作数类型必须存在取负重载
}
```

#### 3.10.5 逻辑非表达式

**逻辑非表达式**是对一个布尔值进行取反的表达式，其语法如下：

```ebnf
LogicalNotExpression = "!" Expression .
```

其中：

- **定义** `LogicalNotExpression` 为逻辑非表达式
- `Expression` 的返回值类型**必须为** `boolean` **或**可隐式转换为 `boolean`（见 [基本类型](#22-基本类型)）
- 有关 `Expression`，见 [表达式](#31-表达式)

有关返回值：

- 逻辑非表达式的返回值类型**必须为** `boolean`
- **当** `Expression` 转换后的布尔值为 `true` **时**，**必须**返回 `false`
- **否则**，**必须**返回 `true`

#### 3.10.6 按位取反表达式

**按位取反表达式**是对一个值进行按位 NOT 操作的表达式，其语法如下：

```ebnf
BitwiseNotExpression = "^" Expression .
```

其中：

- **定义** `BitwiseNotExpression` 为按位取反表达式
- 有关 `Expression`，见 [表达式](#31-表达式)

有关类型：

- `Expression` 的返回值类型**必须为**整数类型、无符号整数类型**或**指针类型（见 [基本类型](#22-基本类型)、[指针类型构造器](#263-指针类型构造器)）
- **当**操作数为指针类型**时**，运算**必须**作用于指针本身

有关返回值：

- 对 `Expression` 的返回值进行按位取反操作，将结果作为返回值
- 返回值类型为 `Expression` 的返回值类型

#### 3.10.7 引用表达式

**引用表达式**是获取实例地址的表达式，其语法如下：

```ebnf
ReferenceExpression = "&" Expression .
```

其中：

- **定义** `ReferenceExpression` 为引用表达式
- `Expression` 的返回值**必须**可寻址
- **定义**可寻址为以下情形之一：
  - 标识符（见 [标识符](#14-标识符)）
  - 指针解引用（见 [解引用表达式](#3108-解引用表达式)）
  - 可寻址的成员访问，**且**其成员为字段（见 [字段](#281-字段)、[成员访问表达式](#352-成员访问表达式)）
  - 可寻址的内建索引访问（见 [索引访问表达式](#354-索引访问表达式)）
  - 上述情形之外的返回值**不得**被寻址
- 有关 `Expression`，见 [表达式](#31-表达式)

有关返回值：

- 获取 `Expression` 的返回值的内存地址，将该地址作为返回值
- 返回值类型为指针

例如：

```novasharp
// 定义：类 Point
class Point
{
    public X: integer(4);
}

// 合法：标识符可寻址
variable count: integer(4) = 0;
variable refCount: pointer integer(4) = &count;

// 合法：基可寻址的成员访问可寻址
variable pair: Point = Point();
variable refX: pointer integer(4) = &pair.X;

// 合法：基可寻址的索引访问可寻址
variable numbers[4]: integer(4) = { 1, 2, 3, 4 };
variable refElement: pointer integer(4) = &numbers[0];

// 非法：临时量不可寻址
// variable bad: pointer integer(4) = &(count + 1);
// 错误：引用表达式的返回值必须可寻址

// 非法：对临时量的成员取地址
// variable bad: pointer integer(4) = &Point().X;
// 错误：引用表达式的返回值必须可寻址
```

#### 3.10.8 解引用表达式

**解引用表达式**是获取指针所指向实例的表达式，其语法如下：

```ebnf
DereferenceExpression = "*" Expression .
```

其中：

- **定义** `DereferenceExpression` 为解引用表达式
- `Expression` 的返回值类型**必须**满足如下任一条件：
  - 是可被解引用的指针（见 [指针类型构造器](#263-指针类型构造器)）
  - 可隐式转换为可被解引用的指针
- 有关 `Expression`，见 [表达式](#31-表达式)

有关返回值：

- 获取位于 `Expression` 的返回值所指向的内存地址的实例，将该实例作为返回值

#### 3.10.9 乘法表达式

**乘法表达式**是对两个值进行求积的表达式，其语法如下：

```ebnf
MultiplyExpression = Expression "*" Expression .
```

其中：

- **定义** `MultiplyExpression` 为乘法表达式
- 有关 `Expression`，见 [表达式](#31-表达式)

有关行为：

- 存在符合左、右表达式类型的乘法重载（见 [运算符重载](#3103-运算符重载)）
- 以左侧表达式为第一个参数、右侧表达式为第二个参数，调用乘法重载

有关返回值：

- 将乘法重载的返回值作为乘法表达式的返回值

#### 3.10.10 除法表达式

**除法表达式**是对两个值进行求商的表达式，其语法如下：

```ebnf
DivideExpression = Expression "/" Expression .
```

其中：

- **定义** `DivideExpression` 为除法表达式
- 有关 `Expression`，见 [表达式](#31-表达式)

有关行为：

- 存在符合左、右表达式类型的除法重载（见 [运算符重载](#3103-运算符重载)）
- 以左侧表达式为第一个参数、右侧表达式为第二个参数，调用除法重载

有关返回值：

- 将除法重载的返回值作为除法表达式的返回值

#### 3.10.11 求余表达式

**求余表达式**是对两个值进行求余的表达式，其语法如下：

```ebnf
RemainderExpression = Expression "%" Expression .
```

其中：

- **定义** `RemainderExpression` 为求余表达式
- 有关 `Expression`，见 [表达式](#31-表达式)

有关行为：

- 存在符合左、右表达式类型的求余重载（见 [运算符重载](#3103-运算符重载)）
- 以左侧表达式为第一个参数、右侧表达式为第二个参数，调用求余重载

有关返回值：

- 将求余重载的返回值作为求余表达式的返回值

#### 3.10.12 加法表达式

**加法表达式**是对两个值进行求和的表达式，其语法如下：

```ebnf
AddExpression = Expression "+" Expression .
```

其中：

- **定义** `AddExpression` 为加法表达式
- 有关 `Expression`，见 [表达式](#31-表达式)

有关行为：

- 存在符合左、右表达式类型的加法重载（见 [运算符重载](#3103-运算符重载)）
- 以左侧表达式为第一个参数、右侧表达式为第二个参数，调用加法重载

有关返回值：

- 将加法重载的返回值作为加法表达式的返回值

#### 3.10.13 减法表达式

**减法表达式**是对两个值进行求差的表达式，其语法如下：

```ebnf
MinusExpression = Expression "-" Expression .
```

其中：

- **定义** `MinusExpression` 为减法表达式
- 有关 `Expression`，见 [表达式](#31-表达式)

有关行为：

- 存在符合左、右表达式类型的减法重载（见 [运算符重载](#3103-运算符重载)）
- 以左侧表达式为第一个参数、右侧表达式为第二个参数，调用减法重载

有关返回值：

- 将减法重载的返回值作为减法表达式的返回值

#### 3.10.14 逻辑左移表达式

**逻辑左移表达式**是对两个值进行逻辑左移操作的表达式，其语法如下：

```ebnf
LogicalLeftShiftExpression = Expression "<<" Expression .
```

其中：

- **定义** `LogicalLeftShiftExpression` 为逻辑左移表达式
- 第二个 `Expression` 的返回值类型**必须**符合如下**任一**条件：
  - 是无符号整数类型（见 [基本类型](#22-基本类型)）
  - 可隐式转换为无符号整数类型
- 有关 `Expression`，见 [表达式](#31-表达式)

有关类型：

- 两个 `Expression` 的返回值类型**必须为**整数类型、无符号整数类型**或**指针类型（见 [基本类型](#22-基本类型)、[指针类型构造器](#263-指针类型构造器)）
- **当**操作数为指针类型**时**，运算**必须**作用于指针本身

有关返回值：

- 对第一个 `Expression` 的返回值进行逻辑左移操作，左移位数为第二个 `Expression` 的返回值，将结果作为返回值
- 返回值类型为第一个 `Expression` 的返回值类型

#### 3.10.15 逻辑右移表达式

**逻辑右移表达式**是对两个值进行逻辑右移操作的表达式，其语法如下：

```ebnf
LogicalRightShiftExpression = Expression ">>" Expression .
```

其中：

- **定义** `LogicalRightShiftExpression` 为逻辑右移表达式
- 第二个 `Expression` 的返回值类型**必须**符合如下**任一**条件：
  - 是无符号整数类型（见 [基本类型](#22-基本类型)）
  - 可隐式转换为无符号整数类型
- 有关 `Expression`，见 [表达式](#31-表达式)

有关类型：

- 两个 `Expression` 的返回值类型**必须为**整数类型、无符号整数类型**或**指针类型（见 [基本类型](#22-基本类型)、[指针类型构造器](#263-指针类型构造器)）
- **当**操作数为指针类型**时**，运算**必须**作用于指针本身

有关返回值：

- 对第一个 `Expression` 的返回值进行逻辑右移操作，右移位数为第二个 `Expression` 的返回值，将结果作为返回值
- 返回值类型为第一个 `Expression` 的返回值类型

#### 3.10.16 小于表达式

**小于表达式**是对判断两个值是否小于的表达式，其语法如下：

```ebnf
LessExpression = Expression "<" Expression .
```

其中：

- **定义** `LessExpression` 为小于表达式
- 有关 `Expression`，见 [表达式](#31-表达式)

有关行为：

- 存在符合左、右表达式类型的小于重载（见 [运算符重载](#3103-运算符重载)）
- 以左侧表达式为第一个参数、右侧表达式为第二个参数，调用小于重载

有关返回值：

- 将小于重载的返回值作为小于表达式的返回值

#### 3.10.17 大于表达式

**大于表达式**是对判断两个值是否大于的表达式，其语法如下：

```ebnf
GreaterExpression = Expression ">" Expression .
```

其中：

- **定义** `GreaterExpression` 为大于表达式
- 有关 `Expression`，见 [表达式](#31-表达式)

有关行为：

- 存在符合左、右表达式类型的大于重载（见 [运算符重载](#3103-运算符重载)）
- 以左侧表达式为第一个参数、右侧表达式为第二个参数，调用大于重载

有关返回值：

- 将大于重载的返回值作为大于表达式的返回值

#### 3.10.18 小于等于表达式

**小于等于表达式**是对判断两个值是否小于等于的表达式，其语法如下：

```ebnf
LessEqualExpression = Expression "<=" Expression .
```

其中：

- **定义** `LessEqualExpression` 为小于等于表达式
- 有关 `Expression`，见 [表达式](#31-表达式)

有关行为：

- 存在符合左、右表达式类型的小于重载（见 [运算符重载](#3103-运算符重载)）
- 存在符合左、右表达式类型的相等重载（见 [运算符重载](#3103-运算符重载)）
- 以左侧表达式为第一个参数、右侧表达式为第二个参数，调用小于重载
- 以左侧表达式为第一个参数、右侧表达式为第二个参数，调用相等重载

有关返回值：

1. 将小于重载的返回值作为左值、相等重载的返回值作为右值代入逻辑或表达式（见 [逻辑或表达式](#31026-逻辑或表达式)）
2. 将逻辑或表达式的返回值作为小于等于表达式的返回值

#### 3.10.19 大于等于表达式

**大于等于表达式**是对判断两个值是否大于等于的表达式，其语法如下：

```ebnf
GreaterEqualExpression = Expression ">=" Expression .
```

其中：

- **定义** `GreaterEqualExpression` 为大于等于表达式
- 有关 `Expression`，见 [表达式](#31-表达式)

有关行为：

- 存在符合左、右表达式类型的大于重载（见 [运算符重载](#3103-运算符重载)）
- 存在符合左、右表达式类型的相等重载（见 [运算符重载](#3103-运算符重载)）
- 以左侧表达式为第一个参数、右侧表达式为第二个参数，调用大于重载
- 以左侧表达式为第一个参数、右侧表达式为第二个参数，调用相等重载

有关返回值：

1. 将大于重载的返回值作为左值、相等重载的返回值作为右值代入逻辑或表达式（见 [逻辑或表达式](#31026-逻辑或表达式)）
2. 将逻辑或表达式的返回值作为大于等于表达式的返回值

#### 3.10.20 相等表达式

**相等表达式**是对判断两个值是否相等的表达式，其语法如下：

```ebnf
EqualExpression = Expression "==" Expression .
```

其中：

- **定义** `EqualExpression` 为相等表达式
- 有关 `Expression`，见 [表达式](#31-表达式)

有关行为：

- 存在符合左、右表达式类型的相等重载（见 [运算符重载](#3103-运算符重载)）
- 以左侧表达式为第一个参数、右侧表达式为第二个参数，调用相等重载

有关返回值：

- 将相等重载的返回值作为相等表达式的返回值

#### 3.10.21 不等表达式

**不等表达式**是对判断两个值是否不等的表达式，其语法如下：

```ebnf
NotEqualExpression = Expression "!=" Expression .
```

其中：

- **定义** `NotEqualExpression` 为不等表达式
- 有关 `Expression`，见 [表达式](#31-表达式)

有关行为：

- 存在符合左、右表达式类型的相等重载（见 [运算符重载](#3103-运算符重载)）
- 以左侧表达式为第一个参数、右侧表达式为第二个参数，调用相等重载

有关返回值：

1. 将相等重载的返回值代入逻辑非表达式（见 [逻辑非表达式](#3105-逻辑非表达式)）
2. 将逻辑非表达式的返回值作为不等表达式的返回值

#### 3.10.22 按位与表达式

**按位与表达式**是对两个值进行按位 AND 操作的表达式，其语法如下：

```ebnf
BitwiseAndExpression = Expression "&" Expression .
```

其中：

- **定义** `BitwiseAndExpression` 为按位与表达式
- 两个 `Expression` 的返回值类型**必须**相同，**或**其中一方可隐式转换为另一方
- 有关 `Expression`，见 [表达式](#31-表达式)

有关类型：

- 两个 `Expression` 的返回值类型**必须为**整数类型、无符号整数类型**或**指针类型（见 [基本类型](#22-基本类型)、[指针类型构造器](#263-指针类型构造器)）
- **当**操作数为指针类型**时**，运算**必须**作用于指针本身

有关返回值：

- 对两个 `Expression` 的返回值进行按位与操作，将结果作为返回值
- 返回值类型为 `Expression` 的返回值类型

#### 3.10.23 按位异或表达式

**按位异或表达式**是对两个值进行按位 XOR 操作的表达式，其语法如下：

```ebnf
BitwiseXorExpression = Expression "^" Expression .
```

其中：

- **定义** `BitwiseXorExpression` 为按位异或表达式
- 两个 `Expression` 的返回值类型**必须**相同，**或**其中一方可隐式转换为另一方
- 有关 `Expression`，见 [表达式](#31-表达式)

有关类型：

- 两个 `Expression` 的返回值类型**必须为**整数类型、无符号整数类型**或**指针类型（见 [基本类型](#22-基本类型)、[指针类型构造器](#263-指针类型构造器)）
- **当**操作数为指针类型**时**，运算**必须**作用于指针本身

有关返回值：

- 对两个 `Expression` 的返回值进行按位异或操作，将结果作为返回值
- 返回值类型为 `Expression` 的返回值类型

#### 3.10.24 按位或表达式

**按位或表达式**是对两个值进行按位 OR 操作的表达式，其语法如下：

```ebnf
BitwiseOrExpression = Expression "|" Expression .
```

其中：

- **定义** `BitwiseOrExpression` 为按位或表达式
- 两个 `Expression` 的返回值类型**必须**相同，**或**其中一方可隐式转换为另一方
- 有关 `Expression`，见 [表达式](#31-表达式)

有关类型：

- 两个 `Expression` 的返回值类型**必须为**整数类型、无符号整数类型**或**指针类型（见 [基本类型](#22-基本类型)、[指针类型构造器](#263-指针类型构造器)）
- **当**操作数为指针类型**时**，运算**必须**作用于指针本身

有关返回值：

- 对两个 `Expression` 的返回值进行按位或操作，将结果作为返回值
- 返回值类型为 `Expression` 的返回值类型

#### 3.10.25 逻辑和表达式

**逻辑和表达式**是对两个布尔值进行 AND 操作的表达式，其语法如下：

```ebnf
LogicalAndExpression = Expression "&&" Expression .
```

其中：

- **定义** `LogicalAndExpression` 为逻辑和表达式
- 两个 `Expression` 的返回值类型**必须为** `boolean` **或**可隐式转换为 `boolean`（见 [基本类型](#22-基本类型)）
- 有关 `Expression`，见 [表达式](#31-表达式)

有关返回值：

- 逻辑和表达式的返回值类型**必须为** `boolean`
- **当**第一个 `Expression` 转换后的布尔值为 `false` **时**，**必须**直接返回 `false`，**禁止**对第二个 `Expression` 求值
- **否则**，**必须**将第二个 `Expression` 的返回值转换为 `boolean` 后返回

#### 3.10.26 逻辑或表达式

**逻辑或表达式**是对两个布尔值进行 OR 操作的表达式，其语法如下：

```ebnf
LogicalOrExpression = Expression "||" Expression .
```

其中：

- **定义** `LogicalOrExpression` 为逻辑或表达式
- 两个 `Expression` 的返回值类型**必须为** `boolean` **或**可隐式转换为 `boolean`（见 [基本类型](#22-基本类型)）
- 有关 `Expression`，见 [表达式](#31-表达式)

有关返回值：

- 逻辑或表达式的返回值类型**必须为** `boolean`
- **当**第一个 `Expression` 转换后的布尔值为 `true` **时**，**必须**直接返回 `true`，**禁止**对第二个 `Expression` 求值
- **否则**，**必须**将第二个 `Expression` 的返回值转换为 `boolean` 后返回

#### 3.10.27 空值合并表达式

**空值合并表达式**是以 `??` 对左操作数进行决策，并在决策为 `Alternative` 时执行右侧续体的表达式，其格式如下：

```ebnf
NullCoalescingExpression = Expression "??" CoalescingAlternative .

CoalescingAlternative = Expression
                      | "throw" [ Expression ]
                      | "return" [ Expression ] .
```

其中：

- **定义** `NullCoalescingExpression` 为空值合并表达式
- **定义**左操作数 `Expression` 为被决策值（见 [表达式](#31-表达式)）
- **定义** `CoalescingAlternative` 为右侧续体
- 有关 `Result`，见 [Built-In Library 完整内容](#152-built-in-library-完整内容)

有关左操作数：

- 左操作数的类型**必须**定义 `operator ??`（见 [运算符](#3101-运算符)）
- `operator ??` **必须**为一元决策操作，其返回值类型**必须为** `Result<TValue; TAlternative>`
- 左操作数**必须仅**求值一次

有关求值：

- **当**决策结果为 `Result.Value(v)` **时**，整个表达式**必须**取 `v`，**禁止**对 `CoalescingAlternative` 求值
- **当**决策结果为 `Result.Alternative(a)` **时**，**必须**按 `CoalescingAlternative` 的形式执行：
  - **当**其为 `Expression` **时**，**必须**惰性求值，**且**其类型**必须为** `TValue`
  - **当**其为 `throw` **时**，**必须**抛出 `a`；**当** `TAlternative` 为空类型**时**，该形式**必须**报错
  - **当**其为 `throw Expression` **时**，**必须**抛出该 `Expression`，`a` **不得**被使用
  - **当**其为 `return` **时**，**必须**从当前函数返回整个决策 `Result`；当前函数的返回值类型**必须**为该 `Result` 的类型
  - **当**其为 `return Expression` **时**，**必须**从当前函数返回该 `Expression`；其类型**必须**等于当前函数的返回值类型
- 空值合并表达式的返回值类型**必须为** `TValue`
- `throw` 形式**必须**遵守 [throw 语句](#493-throw-语句) 的位置限制
- `return` 形式**必须**遵守 [return 语句](#492-return-语句) 的位置限制

有关 `operator ??`：

- `Result<TValue; TAlternative>` 的 `operator ??` **必须**为恒等决策
- `Optional<T>` 的 `operator ??` **必须**把 `Value(v)` 映射为 `Result<T;>.Value(v)`，把 `Null` 映射为无载荷的 `Result<T;>.Alternative`
- 用户类型**允许**定义自己的 `operator ??`

有关空类型：

- `Result<; T>` 的 `Value` 为空类型；`Result<T;>` 的 `Alternative` 为空类型
- **当** `TAlternative` 为空类型**时**，`?? throw` **不得**出现；`?? throw Expression` 仍**允许**

有关可重载性：

- `??` **不得**按普通二元运算符重载
- `operator ??` 为左操作数类型的一元决策操作；`CoalescingAlternative` **不得**参与 `operator ??` 的选择

例如：

```novasharp
// Optional 的 ??：Value 取载荷；Null 取替代值
variable maybe: Optional<integer(4)> = Optional<integer(4)>.Null;
variable fallback: integer(4) = maybe ?? 0; // 0

// Optional.Null 没有载荷，裸 throw 非法
// variable bad = maybe ?? throw;

// 显式给出抛出值；必须在 trap 或 catch 中
constant OptionalThrow()
{
    trap
    {
        variable explicitThrow = maybe ?? throw MyException();
    }
    catch error: Exception
    {
        // ...
    }
}

// Result 的 ??：Value 取载荷；Alternative 交给右侧续体
// 假设已 import Platform.IO

constant read = StandardIO.ReadAs<integer(4)>;

constant ReadOrPass(): Result<integer(4); Exception>
{
    trap
    {
        // Alternative 时在 ?? 处 throw 其载荷
        variable a = read() ?? throw;

        // Alternative 时取 0，错误被丢弃
        variable b = read() ?? 0;

        // Alternative 时从当前函数返回整个 Result
        variable c = read() ?? return;
    }
    catch error: Exception
    {
        // ...
    }

    return Result<integer(4); Exception>.Value(0);
}
```

#### 3.10.28 条件表达式

**条件表达式**是根据条件在两个值之间选取的表达式，其语法如下：

```ebnf
ConditionalExpression = Expression "?" Expression ":" Expression .
```

其中：

- **定义** `ConditionalExpression` 为条件表达式
- **定义**第一个 `Expression` 为条件操作数
- **定义**第二个 `Expression` 为真值分支
- **定义**第三个 `Expression` 为假值分支

有关类型：

- 条件操作数的返回值类型**必须为** `boolean` **或**可隐式转换为 `boolean`（见 [基本类型](#22-基本类型)）
- 真值分支与假值分支的返回值类型**必须**相同，**或**其中一方可隐式转换为另一方
- **定义**条件表达式的返回值类型为两个分支的公共类型
  - **当**两个分支类型相同**时**，公共类型为该类型
  - **当**其中一方派生自另一方**时**，公共类型为被派生的那一方

有关行为：

- **当**条件操作数的返回值为 `true` **时**，条件表达式的返回值**必须为**真值分支的返回值
- **当**条件操作数的返回值为 `false` **时**，条件表达式的返回值**必须为**假值分支的返回值
- 真值分支与假值分支**不得**同时求值

有关可重载性：

- 条件表达式**不得**被重载（见 [运算符重载](#3103-运算符重载)）

例如：

```novasharp
// 定义：函数 Max
constant Max(a: integer(4), b: integer(4)): integer(4)
{
    return a > b ? a : b;
}

// 定义：函数 Main
constant Main(): integer(4)
{
    // 合法：求两者中的较大值
    variable larger: integer(4) = Max(1, 2); // 2

    // 合法：取符号
    variable sign: integer(4) = larger > 0 ? 1 : -1; // 1

    // 非法：条件操作数类型不为 boolean
    // variable bad: integer(4) = 1 ? 2 : 3;
    // 错误：条件操作数的返回值类型必须为 boolean

    // 非法：两个分支无公共类型
    // variable bad: integer(4) = true ? 1 : false;
    // 错误：真值分支与假值分支必须有公共类型

    return 0;
}
```

## 4. 语句

### 4.1 语句

**语句**是代码块中可独立出现的语法单位，其格式如下：

```ebnf
Statement = VariableDefinition
          | AllocateDefinition
          | OperatorDefinition
          | ConstantDefinition
          | FieldDefinition
          | AccessorDefinition
          | SetStatement
          | CompoundSetStatement
          | ImportStatement
          | ModuleDeclaration
          | ClassDeclaration
          | StructureDeclaration
          | InterfaceDeclaration
          | EnumerationDeclaration
          | VariantDeclaration
          | UnionDeclaration
          | ExtensionDeclaration
          | CompileTimeBlock
          | IfStatement
          | WhileStatement
          | DoWhileStatement
          | ForStatement
          | MatchStatement
          | BreakStatement
          | ContinueStatement
          | ReturnStatement
          | ThrowStatement
          | TrapStatement
          | DisposeStatement .
```

其中：

- **定义** `Statement` 为语句
- 有关 `VariableDefinition`，见 [变量](#43-变量)
- 有关 `AllocateDefinition`，见 [堆分配](#45-堆分配)
- 有关 `OperatorDefinition`，见 [运算符](#3101-运算符)
- 有关 `ConstantDefinition`，见 [常量](#44-常量)
- 有关 `FieldDefinition`，见 [字段](#281-字段)
- 有关 `AccessorDefinition`，见 [访问器](#282-访问器)
- 有关 `SetStatement`，见 [赋值语句](#46-赋值语句)
- 有关 `CompoundSetStatement`，见 [赋值语句](#46-赋值语句)
- 有关 `ImportStatement`，见 [导入](#62-导入)
- 有关 `ModuleDeclaration`，见 [模块](#61-模块)
- 有关 `ClassDeclaration`，见 [类](#271-类)
- 有关 `StructureDeclaration`，见 [结构体](#272-结构体)
- 有关 `InterfaceDeclaration`，见 [接口](#273-接口)
- 有关 `EnumerationDeclaration`，见 [枚举](#274-枚举)
- 有关 `VariantDeclaration`，见 [变体](#275-变体)
- 有关 `UnionDeclaration`，见 [共同体](#276-共同体)
- 有关 `ExtensionDeclaration`，见 [扩展](#283-扩展)
- 有关 `CompileTimeBlock`，见 [编译期块](#104-编译期块)
- `CompileTimeBlock` **允许**直接出现在文件顶层；该位置**不得**要求外层代码块
- 有关 `IfStatement`，见 [if 语句](#482-if-语句)
- 有关 `WhileStatement`，见 [while 语句](#483-while-语句)
- 有关 `DoWhileStatement`，见 [do while 语句](#484-do-while-语句)
- 有关 `ForStatement`，见 [for 语句](#485-for-语句)
- 有关 `MatchStatement`，见 [match 语句](#486-match-语句)
- 有关 `BreakStatement`，见 [break 语句](#487-break-语句)
- 有关 `ContinueStatement`，见 [continue 语句](#488-continue-语句)
- 有关 `ReturnStatement`，见 [return 语句](#492-return-语句)
- 有关 `ThrowStatement`，见 [throw 语句](#493-throw-语句)
- 有关 `TrapStatement`，见 [trap 语句](#494-trap-语句)
- 有关 `DisposeStatement`，见 [dispose 语句](#47-dispose-语句)

有关语句：

- 语句**必须**出现在代码块中（见 [代码块](#42-代码块)）
- 语句**必须**以语句终止符终止（见 [语句终止](#18-语句终止)）
- 成员枚举体中的成员定义**不得**被视为语句（见 [代码块](#42-代码块)）

### 4.2 代码块

**代码块**是包含语句序列的作用域，其格式如下：

```ebnf
Block = "{" { Statement | Block } "}" .
```

其中：

- **定义** `Statement` 为语句（见 [语句](#41-语句)）

有关体：

- **定义** `Block` 为声明序列体
- **定义**类型体为类、结构体、接口、枚举、变体、共同体的体以及扩展块的统称
- 类型体**必须**由声明序列构成
- 类型体成员**必须**以语句终止符终止（见 [语句终止](#18-语句终止)）
- 类与结构体的类型体**必须仅**直接包含字段定义、模块声明与扩展声明
  - 常量、访问器、运算符、方法与构造/析构函数**必须**位于扩展块内
- 接口声明体**不得**包含扩展声明；其成员直接声明为契约（见 [接口](#273-接口)）
- 枚举、变体与共同体的类型体**允许**包含扩展声明（见 [扩展](#283-扩展)）
  - 其状态、状态载荷**或**成员定义直接声明；其它成员**必须**位于扩展块内
- 成员枚举体**不得**使用
- 语句终止符（见 [语句终止](#18-语句终止)）**不得**用于语句之外

有关作用域：

- `Block` **必须**构成语句作用域（见 [作用域](#51-作用域)）
- `#{ ... }` 的 `Block` **不得**构成作用域（见 [编译期块](#104-编译期块)）

例如：

```novasharp
// 定义：函数 Main 的代码块
constant Main(): integer(4)
{
    variable a: integer(4) = 1;

    return 0;
}

// 非法：缺少匹配的终止字符
// {
//     variable b: integer(4) = 1;
// 错误：代码块未闭合

// 非法：缺少匹配的终止字符
// constant Main: function() integer(4)
// {
//     variable a: integer(4) = 1;
// 错误：代码块未闭合
```

### 4.3 变量

**变量**是在当前作用域内取得实例存储的标识符种类，其格式如下：

```ebnf
VariableDefinition = { Modifier } "variable" Name [ ":" Type ] [ "=" Expression ] .
```

其中：

- **定义** `VariableDefinition` 为变量定义
- **定义** `Modifier` 为修饰符（见 [修饰符](#81-修饰符)）
- **定义** `Name` 为变量名（见 [标识符](#14-标识符)）
- **定义** `Type` 为变量类型（见 [类型构造语法](#21-类型构造语法)）
- **定义** `Expression` 为初始值表达式（见 [表达式](#31-表达式)）

有关变量定义：

- 修饰符列表**必须**位于 `variable` 之前
- `:` 与 `=` **必须**至少出现一个
- 变量定义**必须**以语句终止符终止（见 [语句终止](#18-语句终止)）
- 变量定义**不得**出现在类型声明体内（见 [字段](#281-字段)）
- 有关定义简写，见 [标识符定义简写](#15-标识符定义简写)
- 有关默认可访问性，见 [可访问性修饰符](#82-可访问性修饰符)

有关初始化：

- 变量存储**必须**在初始化完成前取得
- `Expression` 的返回值类型**必须为**变量类型**或**可隐式转换为变量类型
- **当**出现 `=` **时**，变量存储**必须**被 `Expression` 的返回值覆盖
  - **定义**上述行为为变量的初始化
- **当**省略 `=` **时**，变量**必须**为未初始化变量（见 [内存分配](#111-内存分配)）
- **当**省略 `:` **时**，变量类型**必须**由 `=` 的返回值推断

有关类型：

- **当**出现 `:` **时**，变量类型**必须为** `Type`
- 变量类型**不得为**空类型（见 [类型构造器](#261-类型构造器)）

有关作用域：

- 变量的存储期**必须为**作用域存储期（见 [内存分配](#111-内存分配)）
- 变量的作用域**必须为**声明所在作用域
- **当**声明位于函数体内**时**，变量存储**必须**位于栈上
- **当**声明位于模块体**或**文件体**时**，变量存储**必须**位于全局数据区
- 有关堆存储期，见 [堆分配](#45-堆分配)

例如：

```novasharp
// 合法：定义变量
variable Count: integer(4) = 15;

// 合法：自动类型推断
variable AutoTypesCount = 15;

// 合法：未初始化的变量
variable value: integer(4);

// 非法：既无类型也无初始值
// variable bad;
// 错误：变量定义必须至少包含类型或初始值

// 非法：类型体内定义变量
// structure Bad
// {
//     public variable X: integer(4);
// }
// 错误：类型体内不得定义变量，必须使用字段定义
```

### 4.4 常量

**常量**是初始化后不可被赋值的标识符种类，其格式如下：

```ebnf
ConstantDefinition = { Modifier } "constant" Name [ GenericParameters ] [ ":" Type ] [ "=" Expression | Block ] .
```

其中：

- **定义** `ConstantDefinition` 为常量定义
- **定义** `Modifier` 为修饰符（见 [修饰符](#81-修饰符)）
- **定义** `Name` 为常量名（见 [标识符](#14-标识符)）
- **定义** `GenericParameters` 为泛型参数列表（见 [泛型参数](#91-泛型参数)）
- **定义** `Type` 为常量类型（见 [类型构造语法](#21-类型构造语法)）
- **定义** `Expression` 为初始化表达式（见 [表达式](#31-表达式)）
- **定义** `Block` 为函数常量的体（见 [代码块](#42-代码块)）

有关常量定义：

- 修饰符列表**必须**位于 `constant` 之前
- `=` 与 `Block` **必须**至多出现一个
- 常量定义**必须**以语句终止符终止（见 [语句终止](#18-语句终止)）
- `constant` **不得**与 `readonly`（见 [readonly 修饰符](#87-readonly-修饰符)）同时出现
- 有关定义简写，见 [标识符定义简写](#15-标识符定义简写)

有关初始化：

- **当**常量出现在接口声明体内**时**，常量**不得**被初始化（见 [接口](#273-接口)）
- **当**常量不出现在接口声明体内**且**不是未初始化的 linkable 函数常量**时**，常量**必须**被初始化，即 `=` 与 `Block` **必须**出现一个
- **当**非函数常量的初值在编译期可确定**时**，其**必须**编入只读段；**否则**由 Launcher 在运行期初始化，且其存储此后**不得**再被写入（见 [启动流程](#132-启动流程)）
- `uninitialized` **不得**作为常量的初始值（见 [未初始化](#1713-未初始化)）
- **当**省略 `:` **时**，常量类型**必须**由 `=` 的返回值推断
- **当** linkable 函数常量省略 `=` 与 `Block` **时**，`:` **必须**出现（见 [linkable 修饰符](#810-linkable-修饰符)）
- 常量**仅允许**通过初始化的方式被赋值（见 [赋值语句](#46-赋值语句)）
- `Expression` 的返回值类型**必须为**常量类型**或**可隐式转换为常量类型

有关泛型：

- 泛型参数**仅允许**出现在函数常量中（见 [泛型参数](#91-泛型参数)）

有关函数常量：

- **定义**函数常量为类型为函数类型（见 [函数类型构造器](#264-函数类型构造器)）的常量
- **当**出现 `Block` **时**，`Block` **必须**展开为 `= <函数字面量>`（见 [函数定义语法糖](#71-函数定义语法糖)）
- **定义**方法为参数列表中含有 `this` 参数的函数常量（见 [方法](#74-方法)）

有关访问：

- **允许**以 `static` 修饰（见 [static 修饰符](#816-static-修饰符)）

例如：

```novasharp
// 合法：定义常量
constant INT_MAX: integer(4) = 0xFFFF;

// 合法：自动类型推断
constant Flag = true;

// 合法：泛型函数常量
constant Echo<T>(value: T): T
{
    return value;
}

// 合法：脱糖的函数常量
constant Desugar() =
    () =>
    {

    }

// 定义：接口 IValue
interface IValue
{
    // 合法：接口内的常量不得初始化
    public constant Default: integer(4);
}

// 非法：常量缺少初始化
// constant Bad: integer(4);
// 错误：常量必须被初始化

// 非法：接口内的常量被初始化
// interface Bad
// {
//     public constant Value: integer(4) = 0;
// }
// 错误：接口内的常量不得被初始化
```

### 4.5 堆分配

**堆分配**是在堆上取得实例存储的标识符种类，其格式如下：

```ebnf
AllocateDefinition = { Modifier } "allocate" [ "(" Expression ")" ] [ "manual" ] Name [ ":" Type ] [ "=" Expression ] .
```

其中：

- **定义** `AllocateDefinition` 为堆分配定义
- **定义** `Modifier` 为修饰符（见 [修饰符](#81-修饰符)）
- **定义** `manual` 为后缀标记，用以指明该堆存储不受对象生命周期分析算法管辖（见 [NOLAA](#112-nolaa)）
- **定义** `Name` 为堆内存空间名（见 [标识符](#14-标识符)）
- **定义** `Type` 为堆内存空间容纳值的类型（见 [类型构造语法](#21-类型构造语法)）
- **定义** `Expression` 为初始值表达式（见 [表达式](#31-表达式)）

有关堆分配定义：

- 修饰符列表**必须**位于 `allocate` 之前
- `manual` **必须**位于 `allocate` 之后、`Name` 之前
- `:` 与 `=` **必须**至少出现一个
- 有关定义简写，见 [标识符定义简写](#15-标识符定义简写)
- 有关分配器表达式，见下文
- 堆分配定义**必须**以语句终止符终止（见 [语句终止](#18-语句终止)）
- 堆分配定义**不得**出现在类型声明体内（见 [字段](#281-字段)）
- 有关默认可访问性，见 [可访问性修饰符](#82-可访问性修饰符)

有关类型：

- **当**出现 `:` **时**，堆内存空间容纳值的类型**必须为** `Type`
- 堆内存空间容纳值的类型**不得为**空类型（见 [类型构造器](#261-类型构造器)）
- **当**省略 `:` **时**，堆内存空间容纳值的类型**必须**由 `=` 的返回值推断
- 堆存储的大小**必须**刚好可以容纳上述类型的值

有关分配器：

- **当**出现分配器表达式**时**，其类型**必须**为 `IAllocator`（见 [Built-In Library 完整内容](#152-built-in-library-完整内容)）
- 分配器表达式**必须**只求值一次
- **当**出现分配器表达式**时**，`manual` **必须**位于该表达式之后
- **当**省略分配器表达式**时**，**必须**使用全局 `DefaultAllocator`
- `DefaultAllocator` **必须**为全局常量，类型**必须**为 `IAllocator`
- **当** `DefaultAllocator` 不存在**时**，省略分配器表达式**必须**报错
- `DefaultAllocator` **必须**由开发者**或**平台提供
- `DefaultAllocator` **必须**在首次省略分配器的 `allocate` 前初始化
- 分配单位**必须**记录实际分配器，供 `dispose` 使用（见 [dispose 语句](#47-dispose-语句)）
- **当** `Allocate` 返回 `Value` **时**，`allocate` **必须**使用其指针
- **当** `Allocate` 返回 `Alternative` **时**，`allocate` **必须**产生 `AllocateFailedException` 运行时异常（见 [异常处理](#491-异常处理)）
- **当** `allocate` 产生 `AllocateFailedException` **时**，`Name` **不得**被绑定，初始化表达式**不得**执行

有关初始化：

- 堆存储**必须**在初始化完成前取得
- **当**出现 `=` **时**，堆存储**必须**被 `Expression` 的返回值覆盖
  - **定义**上述行为为堆分配标识符的初始化
- **当**省略 `=` **时**，堆存储**必须**为未初始化堆存储（见 [内存分配](#111-内存分配)）

有关作用域：

- 堆分配标识符的作用域**必须**与同位置的 `variable` 一致（见 [变量](#43-变量)）
- **当**作用域结束**时**，堆存储**不得**随之释放（见 [内存分配](#111-内存分配)）

有关生命周期：

- **当**省略 `manual` **时**，堆存储**必须**由对象生命周期分析算法判定释放（见 [NOLAA](#112-nolaa)）
- **当**出现 `manual` **时**，堆存储**必须**由开发者释放
- **允许**两种堆存储以 dispose 语句显式释放（见 [dispose 语句](#47-dispose-语句)）
- **当**堆存储被显式释放**时**，对象生命周期分析算法**不得**再次释放该存储（见 [NOLAA](#112-nolaa)）

例如：

```novasharp
// 定义：类 Node
class Node
{
    public Value: integer(4);
}

// 定义：函数 Main
constant Main(): integer(4)
{
    // 假设：DefaultAllocator 已由开发者提供

    // 合法：使用默认分配器
    allocate node: Node = Node();

    // 合法：显式分配器
    allocate(DefaultAllocator) other: Node = Node();

    // 合法：手动堆分配
    allocate manual raw: Node = Node();

    // 合法：值类型的堆分配
    allocate number: integer(4) = 42;

    // 合法：以 7 覆盖实例字段
    node.Value = 7;

    // 合法：以 43 覆盖堆存储
    number = 43;

    return 0;
}

// 非法：堆分配定义使用 &
// allocate bad: &integer(4) = 1;
// 错误：堆分配定义不得使用 &

// 非法：manual 位于名称之后
// allocate bad manual: integer(4) = 1;
// 错误：manual 必须位于 allocate 之后、名称之前
```

### 4.6 赋值语句

**赋值语句**是以目标值表达式覆盖赋值目标所占内存的语句，其格式如下：

```ebnf
SetStatement          = AssignmentTarget "=" Expression .

CompoundSetStatement  = AssignmentTarget ( "+=" | "-=" | "*=" | "/=" | "%=" | "&=" | "|=" | "^=" | "<<=" | ">>=" ) Expression .

AssignmentTarget      = Identifier
                      | IndexAccessExpression
                      | PointerMemberAccessExpression .
```

其中：

- **定义** `SetStatement` 为赋值语句
  - 赋值语句**必须仅**出现在函数体中（见 [函数](#1710-函数)）
- **定义** `CompoundSetStatement` 为复合赋值语句
  - 复合赋值语句**必须仅**出现在函数体中（见 [函数](#1710-函数)）
- **定义** `AssignmentTarget` 为赋值目标
- **定义** `Identifier` 为标识符形式的赋值目标（见 [标识符](#14-标识符)）
  - 上述标识符**必须**指向可访问的、在当前语句所在上下文中可被赋值的标识符
  - 上述标识符**必须**指向变量（见 [变量](#43-变量)）、堆分配标识符（见 [堆分配](#45-堆分配)）、字段（见 [字段](#281-字段)）**或**访问器（见 [访问器](#282-访问器)）
- **定义** `IndexAccessExpression` 为索引访问形式的赋值目标（见 [索引访问表达式](#354-索引访问表达式)）
- **定义** `PointerMemberAccessExpression` 为指针成员访问形式的赋值目标（见 [指针成员访问表达式](#353-指针成员访问表达式)）
- **定义** `Expression` 为目标值表达式（见 [表达式](#31-表达式)）

有关行为：

- 目标值表达式的返回值类型**必须为**赋值目标的类型**或**可隐式转换为赋值目标的类型
- 赋值**必须**以目标值表达式的返回值覆盖赋值目标所占的内存
  - **当**赋值目标的类型为值类型**时**，**必须**覆盖实例本体（见 [值类型](#23-值类型)）
  - **当**赋值目标的类型为引用类型**时**，**必须**覆盖引用（见 [引用类型](#24-引用类型)）
- **当**目标值表达式为构造表达式**时**，其**必须**被构造到赋值目标存储中（见 [构造表达式](#37-构造表达式)）

有关复合赋值：

- **定义**复合赋值语句为以目标当前值与目标值表达式运算、**并**以结果覆盖目标的语句
- 上述运算**必须**遵循目标类型的对应二元运算符（见 [运算符重载](#3103-运算符重载)）
- 赋值目标**必须**只被求值一次
- 复合赋值**不得**视为 `a = a op b` 的普通展开；其求值顺序由本节规定

有关求值顺序：

- 赋值目标的存储**必须**先于目标值表达式确定
- **当**语句为复合赋值语句**时**，赋值目标的当前值**必须**在目标值表达式求值之后读取

例如：

```novasharp
// 定义：类 Counter
class Counter
{
    public Count: integer(4);

    public Items[3]: integer(4);

    extension
    {
        public accessor Value: integer(4) => Count;

        operator [index: unsigned integer(4)]: integer(4)
        {
            get = (this: &Counter, index: unsigned integer(4)) integer(4) => { return this.Items[index]; }
            set = (this: &Counter, index: unsigned integer(4), value: integer(4)) => { this.Items[index] = value; }
        }
    }
}

// 定义：函数 Main
constant Main(): integer(4)
{
    // 定义：变量 value
    variable value: integer(4) = 0;

    // 合法：以 1 覆盖 value 所占内存
    value = 1;

    // 合法：复合赋值，目标只被求值一次
    value += 1;

    // 合法：以 5 覆盖数组元素所占内存
    variable numbers[3]: integer(4) = { 1, 2, 3 };
    numbers[0] = 5;

    // 合法：复合赋值作用于数组元素
    numbers[0] += 1;

    // 定义：实例 counter
    variable counter: Counter = Counter();

    // 合法：以 2 覆盖字段所占内存
    counter.Count = 2;

    // 合法：以 3 覆盖访问器所占内存
    counter.Value = 3;

    // 合法：以 6 覆盖索引访问器所占内存，调用其 set
    counter[0] = 6;

    // 定义：堆分配实例 node
    allocate node: Counter = Counter();

    // 合法：以 4 覆盖堆存储所占内存
    node.Count = 4;

    // 定义：常量 immutable
    constant immutable: integer(4) = 4;

    // 非法：不可为常量赋值
    // immutable = 5
    // 错误：immutable 在当前上下文中不可被赋值

    return 0;
}
```

### 4.7 dispose 语句

**dispose 语句**是销毁堆存储的语句，其格式如下：

```ebnf
DisposeStatement = "dispose" ( Identifier | PointerMemberAccessExpression ) .
```

其中：

- **定义** `DisposeStatement` 为 dispose 语句
  - dispose 语句**必须仅**出现在函数体中（见 [函数](#1710-函数)）
- **定义** `Identifier` 为销毁目标标识符（见 [标识符](#14-标识符)）
- **定义** `PointerMemberAccessExpression` 为指针成员访问形式的销毁目标（见 [指针成员访问表达式](#353-指针成员访问表达式)）
- 销毁目标**必须**指向堆分配单位（见 [堆分配](#45-堆分配)）
- 销毁目标**必须**可访问（见 [可访问性修饰符](#82-可访问性修饰符)）

有关目标：

- 销毁目标**必须**指向堆分配单位（见 [堆分配](#45-堆分配)、[NOLAA](#112-nolaa)）
- 销毁目标**不得**指向作用域存储期的实例（见 [内存分配](#111-内存分配)）
- 销毁目标**不得**为常量（见 [常量](#44-常量)）
- 上述判定**必须**由编译器执行（见 [NOLAA](#112-nolaa)）

有关行为：

- 按销毁目标的类型的生命周期销毁实例（见 [类](#271-类)、[结构体](#272-结构体)）
- 销毁**必须**先调用析构函数，再回收内存
  - **当**析构函数未完成**时**，回收**不得**执行（见 [类](#271-类)）
  - 回收**必须**由分配单位记录的 `IAllocator.Deallocate` 完成
  - **当** `Deallocate` 返回 `Alternative` **时**，**必须**产生 `DeallocateFailedException` 运行时异常（见 [异常处理](#491-异常处理)）
- 销毁**必须仅**释放销毁目标所指的分配单位
  - 销毁**不得**连带释放该实例所引用的其他分配单位
- **定义**上述行为为显式释放（见 [内存分配](#111-内存分配)）

有关生命周期：

- **当**销毁目标所指的分配单位由 `allocate` 分配**时**，对象生命周期分析算法**不得**在显式释放后再次释放其存储（见 [NOLAA](#112-nolaa)）
- **当**销毁目标所指的分配单位由 `allocate manual` 分配**时**，开发者**必须**以 dispose 语句释放其存储（见 [堆分配](#45-堆分配)）
- **当**销毁早于安全点**时**，对象生命周期分析算法**必须**发出 Early-Dispose Warning（见 [NOLAA](#112-nolaa)）

有关已销毁实例：

- 已被销毁的实例**不得**被读取**或**写入
- 已被销毁的实例**不得**被重复销毁
  - **当**上述要求被违反**时**，对象生命周期分析算法**必须**发出 Double-Dispose Warning（见 [NOLAA](#112-nolaa)）
- **当**上述情形无法被对象生命周期分析算法判定**时**，该情形为危险行为
  - 编译器**应当**予以 Warning

例如：

```novasharp
// 定义：类 Token
class Token
{
    public Value: integer(4);
}

// 定义：函数 Make
constant Make(): Token
{
    // 合法：token 经返回值逃逸，本函数内不存在安全点，NOLAA 不插入 dispose
    allocate token: Token = Token();

    return token;
}

// 定义：函数 Main
constant Main(): integer(4)
{
    // 合法：销毁自动堆存储
    allocate token: Token = Token();
    dispose token;

    // 合法：销毁手动堆存储
    allocate manual raw: Token = Token();
    dispose raw;

    // 合法：变量指向堆分配单位，可被销毁
    variable made: Token = Make();
    dispose made;

    return 0;
}

// 非法：销毁指向作用域存储期的实例
// variable local: integer(4) = 1;
// dispose local;
// 错误：销毁目标必须指向堆分配单位

// 危险：销毁后再次访问
// allocate token: Token = Token();
// dispose token;
// token.Value = 1;
```

### 4.8 逻辑控制流

#### 4.8.1 逻辑控制流名称

**逻辑控制流名称**是用于标识逻辑控制流语句的名称（见 [标识符](#14-标识符)），其格式如下：

```ebnf
LogicalControlFlowName = ":" Name .
```

其中：

- **定义** `LogicalControlFlowName` 为逻辑控制流名称
  - 逻辑控制流名称**仅允许**：
    - while 语句（见 [while 语句](#483-while-语句)）
    - do while 语句（见 [do while 语句](#484-do-while-语句)）
    - for 语句（见 [for 语句](#485-for-语句)）
    - match 语句（见 [match 语句](#486-match-语句)）
- **定义** `Name` 为名称（见 [标识符](#14-标识符)）

有关出现位置：

- 逻辑控制流名称**必须**位于所属语句的头部与 `Block` 之间：
  - while 语句：条件表达式之后、`Block` 之前
  - do while 语句：`do` 之后、`Block` 之前
  - for 语句：遍历目标之后、`Block` 之前
  - match 语句：被匹配表达式之后、`{` 之前

有关唯一性：

- 同一作用域内**不得**出现同名的逻辑控制流名称
- 内层逻辑控制流名称**允许**与外层同名，**并**遮蔽外层名称

有关作用域：

- 逻辑控制流名称的作用域**必须为**：
  - 支持的逻辑控制流的所有 `Block` 内部

有关引用：

- **当** `break` 语句**或** `continue` 语句携带名称**时**，该名称**必须**解析为最内层同名的逻辑控制流名称
- 有关 `break` 语句与 `continue` 语句对逻辑控制流名称的引用，见 [break 语句](#487-break-语句)、[continue 语句](#488-continue-语句)

#### 4.8.2 if 语句

**if 语句**是根据条件选择执行代码块的逻辑控制流语句，其格式如下：

```ebnf
IfStatement = "if" Expression Block { "else" "if" Expression Block } [ "else" Block ] .
```

其中：

- **定义** `IfStatement` 为 if 语句
  - if 语句**必须**出现在函数体中
- **定义** `Expression` 为条件表达式
  - 条件表达式返回值类型**必须为** `boolean` **或**可隐式转换为 `boolean`
  - 条件表达式**不得**访问 `Block` 中定义的标识符
- 有关 `Block`，见 [代码块](#42-代码块)

> [!NOTE] NovaSharp vs. C/C++
> 和 C/C++ 不同，NovaSharp 的条件表达式**不要求**括号，但分支**必须**使用大括号。

有关行为：

1. **执行**条件表达式，**若**值为 `true`，**则**：
   1. 执行对应 `Block`
   2. 退出控制流
2. **否则若**后面存在 `else if`，**则**：
   1. **执行**该 `else if` 的条件表达式，**若**值为 `true`，**则**：
      1. 执行对应 `Block`
      2. 退出控制流
   2. **否则**继续步骤 2
3. **否则若**存在 `else`，**则**执行对应 `Block`
4. 退出控制流

例如：

```novasharp
// 定义：函数 Main
constant Main(): integer(4)
{
    // 合法：基本 if
    if true { }

    // 合法：else if 链
    if false { }
    else if true { }
    else { }

    // 非法：条件不为 boolean，且不存在可用的隐式转换
    // if 1 { }
    // 错误：条件表达式返回值类型必须为 boolean 或可隐式转换为 boolean

    {
        // 合法：在函数体内的代码块内，依然属于在函数体内
        if true { }
    }

    // 非法：条件表达式访问 Block 内标识符
    // if x
    // {
    //     variable x: integer(4) = 1;
    // }
    // 错误：未定义的标识符 x；条件表达式不得访问 Block 中定义的标识符

    // 非法：条件表达式返回值类型必须为 boolean
    // if "text" { }
    // 错误：类型不匹配
}

// 非法：函数体外的 if 语句
// if true { }
// 错误：意外的 if 语句
```

#### 4.8.3 while 语句

**while 语句**是根据条件选择是否继续执行代码块的逻辑控制流语句，其格式如下：

```ebnf
WhileStatement = "while" Expression [ ":" Name ] Block .
```

其中：

- **定义** `WhileStatement` 为 while 语句
  - while 语句**必须**出现在函数体中
- **定义** `Expression` 为条件表达式
  - 条件表达式返回值类型**必须为** `boolean` **或**可隐式转换为 `boolean`
  - **禁止**条件表达式访问 `Block` 中定义的标识符
- **定义** `Name` 为逻辑控制流名称（见 [逻辑控制流名称](#481-逻辑控制流名称)）
- 有关 `Block`，见 [代码块](#42-代码块)

> [!NOTE] NovaSharp vs. C/C++
> 和 C/C++ 不同，NovaSharp 的条件表达式**不要求**括号，但循环体**必须**使用大括号。

有关行为：

1. **执行**条件表达式，**若**值为 `true`，**则**：
   1. 执行 `Block`
   2. 继续步骤 1
2. 退出控制流

例如：

```novasharp
// 定义：函数 Main
constant Main(): integer(4)
{
    // 合法：基本 while
    while true { }

    // 合法：带逻辑控制流名称
    while false : Loop { }

    // 非法：条件不为 boolean，且不存在可用的隐式转换
    // while 1 { }
    // 错误：条件表达式返回值类型必须为 boolean 或可隐式转换为 boolean

    {
        // 合法：在函数体内的代码块内，依然属于在函数体内
        while true { }
    }

    // 非法：条件表达式访问 Block 内标识符
    // while x
    // {
    //     variable x: integer(4) = 1;
    // }
    // 错误：未定义的标识符 x；条件表达式不得访问 Block 中定义的标识符
}

// 非法：函数体外的 while 语句
// while true { }
// 错误：意外的 while 语句
```

#### 4.8.4 do while 语句

**do while 语句**是根据条件选择是否继续执行代码块的逻辑控制流语句，其格式如下：

```ebnf
DoWhileStatement = "do" [ ":" Name ] Block "while" Expression .
```

其中：

- **定义** `DoWhileStatement` 为 do while 语句
  - do while 语句**必须**出现在函数体中
- **定义** `Expression` 为条件表达式
  - 条件表达式返回值类型**必须为** `boolean` **或**可隐式转换为 `boolean`
  - **允许**条件表达式访问 `Block` 中定义的标识符
- `Block` 的作用域**必须**包含条件表达式
- **定义** `Name` 为逻辑控制流名称（见 [逻辑控制流名称](#481-逻辑控制流名称)）
- 有关 `Block`，见 [代码块](#42-代码块)

> [!NOTE] NovaSharp vs. C/C++
> 和 C/C++ 不同，NovaSharp 的条件表达式**不要求**括号，但循环体**必须**使用大括号。

有关行为：

1. 执行 `Block`
2. **执行**条件表达式，**若**值为 `true`，**则**继续步骤 1
3. 退出控制流

例如：

```novasharp
// 定义：函数 Main
constant Main(): integer(4)
{
    // 合法：基本 do while
    do { } while true;

    // 合法：条件访问 Block 内标识符
    do { variable x: integer(4) = 1; } while x == 1;

    {
        // 合法：在函数体内的代码块内，依然属于在函数体内
        do { } while true;
    }
}

// 非法：函数体外的 do while 语句
// do { } while true;
// 错误：意外的 do while 语句
```

#### 4.8.5 for 语句

**for 语句**是遍历数组或可迭代对象并执行代码块的逻辑控制流语句，其格式如下：

```ebnf
ForStatement = "for" [ "&" ] Name ":" Type "in" TraverseTarget [ ":" Name ] Block .

TraverseTarget = Expression | Range .

Range = Expression [ ".." Expression ] ( ".." | "..!" ) Expression .
```

其中：

- **定义** `ForStatement` 为 for 语句
  - for 语句**必须**出现在函数体中
- **定义** `Type` 为迭代变量类型
- **定义** `&` 为引用标记
- **定义**首个 `Name` 为迭代变量名
  - **当**使用引用标记时，**判定**该迭代变量为引用变量
- **定义** `TraverseTarget` 为遍历目标
- **定义** `Range` 为区间
- **定义** `..!` 为左闭右开区间的区间记法
- `..!` **必须**按最大吞噬识别为单一记号
- **定义**区间的首个 `Expression` 为起始值表达式
- **当**区间携带步长**时**，**定义**其第二个 `Expression` 为步长表达式
- **定义**区间的最后一个 `Expression` 为终止值表达式
- **定义**第二个 `Name` 为逻辑控制流名称（见 [逻辑控制流名称](#481-逻辑控制流名称)）
- 有关 `Block`，见 [代码块](#42-代码块)
- 迭代变量的类型**允许**使用 [标识符定义简写](#15-标识符定义简写)

有关遍历目标：

- 遍历目标**必须**为以下之一：
  - 数组类型表达式（见 [数组类型构造器](#262-数组类型构造器)）
  - 可隐式转换为数组类型的表达式
  - 实现了 `IIterator` 接口的类实例表达式（见 [类](#271-类)）
  - 实现了 `IIterable` 接口的类实例表达式（见 [类](#271-类)）
  - 区间
- **当**遍历目标同时满足多个条件时，**必须**按上述顺序匹配

有关数组遍历：

- **当**迭代变量为引用变量时，**必须**引用数组元素
- **否则**迭代变量**必须**为数组元素的拷贝

有关迭代器遍历：

- 遍历实现 `IIterator` 接口的实例时，**必须**按如下顺序执行：
  1. 调用 `Next()` 方法，取得返回值
  2. **若**返回值的状态为 `Value`，**则**将其载荷赋给迭代变量，执行 `Block`，继续步骤 1
  3. **若**返回值的状态为 `Null`，**则**退出控制流
- 载荷的类型**必须**为迭代变量类型**或**可隐式转换为迭代变量类型
- `IIterator` 是 Built-In Library 在全局作用域下定义的接口
- 有关 `IIterator` 的定义，见 [Built-In Library 完整内容](#152-built-in-library-完整内容)

有关可迭代对象遍历：

- 遍历实现 `IIterable` 接口的实例时，**必须**先获取其 `Iterator` 访问器，再按迭代器遍历规则执行
- `IIterable` 是 Built-In Library 在全局作用域下定义的接口
- 有关 `IIterable` 的定义，见 [Built-In Library 完整内容](#152-built-in-library-完整内容)

有关区间：

- **定义**左闭右闭区间为含起始值与终止值的区间
- **定义**左闭右开区间为含起始值、不含终止值的区间
- **当**区间记法为 `..` **时**，区间**必须**为左闭右闭区间
- **当**区间记法为 `..!` **时**，区间**必须**为左闭右开区间
- **当**省略步长时：
  - **若**起始值表达式的返回值 $\le$ 终止值表达式的返回值，**则**默认步长为 1
  - **否则**默认步长为 -1

有关区间遍历：

1. 迭代变量**必须**赋值为起始值表达式的返回值
2. **若**迭代变量满足遍历条件（见「有关遍历条件」），**则**：
   1. 执行 `Block`
   2. 迭代变量增加步长表达式的返回值
   3. 继续步骤 2
3. 退出控制流

有关遍历条件：

- **当**区间为左闭右闭区间**时**，**判定**迭代变量满足遍历条件，**当且仅当**：步长表达式的返回值 $>$ 0 **且**迭代变量 $\le$ 终止值表达式的返回值，**或**步长表达式的返回值 $<$ 0 **且**迭代变量 $\ge$ 终止值表达式的返回值
- **当**区间为左闭右开区间**时**，**判定**迭代变量满足遍历条件，**当且仅当**：步长表达式的返回值 $>$ 0 **且**迭代变量 $<$ 终止值表达式的返回值，**或**步长表达式的返回值 $<$ 0 **且**迭代变量 $>$ 终止值表达式的返回值
- 步长表达式实时计算，**允许**编译器优化
- 终止值实时计算，**允许**编译器优化

例如：

```novasharp
constant Main(): integer(4)
{
    // 合法：遍历数组（拷贝）
    variable numbers[5]: integer(4) = { 10, 20, 30, 40, 50 };
    for i: integer(4) in numbers { }

    // 合法：遍历数组（引用）
    for &ref: integer(4) in numbers
    {
        ref = 0; // 修改原数组元素
    }

    // 合法：遍历可迭代对象（假设 LinkedList 实现了 IIterable<integer(4)>）
    // for value: integer(4) in list { }

    // 合法：基本区间
    for i: integer(4) in 0..5 { } // 0, 1, 2, 3, 4, 5

    // 合法：左闭右开区间
    for i: integer(4) in 0..!5 { } // 0, 1, 2, 3, 4

    // 合法：左闭右开区间（逆向）
    for i: integer(4) in 5..!0 { } // 5, 4, 3, 2, 1

    // 合法：以区间展开所得的数组为遍历目标，进入时求值一次并固定
    for i: integer(4) in {[0..!5]} { } // 0, 1, 2, 3, 4

    // 合法：带步长区间
    for i: integer(4) in 0..2..10 { } // 0, 2, 4, 6, 8, 10

    // 合法：反向区间
    for i: integer(4) in 10..-2..0 { } // 10, 8, 6, 4, 2, 0

    {
        // 合法：在函数体内的代码块内，依然属于在函数体内
        for i: integer(4) in 0..5 { }
    }

    // 非法：区间类型不匹配
    // for i: integer(4) in 0.."text" { }
    // 错误：区间表达式类型必须一致

    // 非法：迭代变量访问外部
    // for i: integer(4) in numbers { }
    // variable x: integer(4) = i;
    // 错误：迭代变量不得在外部访问
}

// 非法：函数体外的 for 语句
// for i: integer(4) in 0..5 { }
// 错误：意外的 for 语句
```

#### 4.8.6 match 语句

**match 语句**是根据模式选择执行代码块的逻辑控制流语句，其格式如下：

```ebnf
MatchStatement  = "match" Expression [ ":" Name ] "{" { MatchCase } "}" .

MatchCase       = "case" ( Pattern [ Guard ] | Guard ) Block .

Pattern            = EqualPattern
                   | ComparisonPattern
                   | IsPattern
                   | WildcardPattern .

EqualPattern       = Expression .
ComparisonPattern  = ComparisonOperator Expression .
ComparisonOperator = "!=" | ">" | "<" | ">=" | "<=" .
IsPattern          = "is" [ Name ":" ] IsTarget .
WildcardPattern    = "wildcard" .

Guard           = "when" Expression .
```

其中：

- **定义** `MatchStatement` 为 match 语句
  - match 语句**必须**出现在函数体中
- **定义** match 语句的 `Expression` 为被匹配表达式
- **定义** match 语句的 `Name` 为逻辑控制流名称（见 [逻辑控制流名称](#481-逻辑控制流名称)）
- **定义** `MatchCase` 为匹配分支
- **定义** `Pattern` 为模式
- **定义** `Guard` 为守卫条件
- **定义** `EqualPattern` 为值相等模式
- **定义** `ComparisonPattern` 为比较模式
- **定义** `ComparisonOperator` 为比较运算符
- **定义** `IsPattern` 为 is 模式
- 有关 `IsTarget`，见 [is 表达式](#39-is-表达式)
- **定义** is 模式的 `Name` 为绑定名
- **定义** `WildcardPattern` 为通配模式
- 有关 `Block`，见 [代码块](#42-代码块)

有关模式：

- 值相等模式**必须**将被匹配表达式返回值作为左值、模式表达式返回值作为右值代入相等表达式（见 [相等表达式](#31020-相等表达式)）
  - **若**返回 `true`，**则**匹配成功
  - **若**无对应重载或返回 `false`，**则**匹配失败
  - 无对应重载的判定**必须**在编译期进行
- 比较模式**必须**将被匹配表达式返回值作为左操作数、模式表达式返回值作为右操作数代入 `ComparisonOperator` 对应的比较表达式
  - **若**返回 `true`，**则**匹配成功
  - **若**无对应重载**或**返回 `false`，**则**匹配失败
  - 无对应重载的判定**必须**在编译期进行
- `is` 模式**必须**将被匹配表达式返回值代入 `is` 表达式（见 [is 表达式](#39-is-表达式)）
  - **若**返回 `true`，**则**匹配成功
  - 判定目标**必须**指向类类型（见 [类](#271-类)）、接口（见 [接口](#273-接口)）**或**变体成员（见 [变体](#275-变体)）
  - **当**判定目标指向类类型**或**接口**时**，**若**模式携带 `Name`，**则**立即将收窄为目标类型的值赋给该标识符
  - **当**判定目标指向携带载荷的变体成员**时**，**若**模式携带 `Name`，**则**立即将载荷值赋给该标识符
  - **当**判定目标指向不携带载荷的变体成员**时**，**禁止**模式携带 `Name`
  - 模式绑定的类型**允许**使用 [标识符定义简写](#15-标识符定义简写)
  - **当**判定目标为非法值字面量**时**，**禁止**模式携带 `Name`
- 通配模式**必须**总是匹配成功

有关守卫条件：

- 守卫条件表达式返回值类型**必须为** `boolean` **或**可隐式转换为 `boolean`
- 守卫条件**必须**在模式匹配成功后计算
- **若**守卫条件返回 `false`，**则**视为当前分支不通过

有关行为：

1. 计算被匹配表达式，设返回值为 `V`
2. 按顺序尝试匹配分支，**若**当前分支模式匹配成功，**则**：
   1. **若**存在守卫条件且返回 `false`，**则**尝试下一个分支
   2. 执行当前分支 `Block`
   3. **若**执行到 continue，**则**退出 block，执行步骤 2
   4. 退出控制流
3. 退出控制流

有关 continue：

**当** match 语句的 `Block` 中执行到目标为当前 match 语句的 continue 语句（见 [continue 语句](#488-continue-语句)）时：

1.  不再继续执行当前 `Block`
2.  继续按顺序匹配下一个分支

> [!NOTE] NovaSharp vs. C/C++
> 上述行为**不是** fall-through。

有关编译期的其它行为：

- 编译器**必须**对 match 语句进行穷尽性检查
  - **若**未通过，**则**编译器**必须** Warning

例如：

```novasharp
// 定义：类 Animal
abstract class Animal
{
}

// 定义：类 Cat
class Cat: Animal
{
}

// 定义：变体 Option
variant Option
{
    Some: integer(4);
    None;
}

// 定义：函数 Main
constant Main(): integer(4)
{
    // 合法：值相等模式
    variable x: integer(4) = 5;
    match x
    {
        case 1 { }
        case 5 { }
        case wildcard { }
    }

    // 合法：is 模式，类类型判定并收窄
    variable animal: Animal = Cat();
    match animal
    {
        case is cat:Cat { } // cat 为收窄为 Cat 后的值
        case wildcard { }
    }

    // 合法：is 模式，变体成员判定并绑定载荷
    variable opt: Option = Option.Some(42);
    match opt
    {
        case is value:Option.Some { } // value = 42
        case is Option.None { }
    }

    // 合法：is 模式，非数判定
    variable ratio: float(4) = illegal;
    match ratio
    {
        case is illegal { }
        case wildcard { }
    }

    // 合法：比较模式
    match x
    {
        case > 3 { }
        case < 0 { }
        case wildcard { }
    }

    // 合法：绑定之后的守卫条件
    match opt
    {
        case is v:Option.Some when v > 3 { }
        case is Option.Some { }
        case is Option.None { }
    }

    {
        // 合法：在函数体内的代码块内，依然属于在函数体内
        // 合法：静态上不可能成立，恒假
        match x
        {
            case is cat:Cat { } // 恒假：integer(4) 与 Cat 的判定不可能成立
            case wildcard { }
        }
    }

    return 0;
}

// 非法：判定目标不是类类型、接口或变体成员
// match opt { case is i:Option { } }
// 错误：is 模式的判定目标必须指向类类型、接口或变体成员

// 非法：不携带载荷的变体成员携带绑定
// match opt { case is value:Option.None { } }
// 错误：判定目标指向不携带载荷的变体成员时，禁止模式携带 Name

// 非法：函数体外的 match 语句
// match 1 { }
// 错误：意外的 match 语句
```

#### 4.8.7 break 语句

**break 语句**是退出控制流的逻辑控制流语句，其格式如下：

```ebnf
BreakStatement = "break" [ Name ] .
```

其中：

- **定义** `BreakStatement` 为 break 语句
  - break 语句**必须**出现在逻辑控制流中
- **定义** `Name` 为逻辑控制流名称（见 [逻辑控制流名称](#481-逻辑控制流名称)）
  - 逻辑控制流名称**必须**指向已定义的逻辑控制流（见 [逻辑控制流名称](#481-逻辑控制流名称)）

有关行为：

- **当**未给定逻辑控制流名称**时**，**必须**退出满足如下**所有**条件的逻辑控制流：
  - 支持逻辑控制流名称（见 [逻辑控制流名称](#481-逻辑控制流名称)）
  - 位于最内侧
- **当**给定逻辑控制流名称**时**，**必须**退出对应的逻辑控制流

例如：

```novasharp
// 定义：函数 Main
constant Main(): integer(4)
{
    while true : Outer
    {
        while true : Inner
        {
            // 合法：退出外部循环
            break Outer
        }
    }

    for i: integer(4) in 1..10
    {
        if i > 5
        {
            // 合法：退出 for 循环
            break;
        }
    }

    if 1 + 1 == 2
    {
        // 非法：没有可被 break 的逻辑控制流语句
        // break;
        // 错误：意外的 break
    }

    return 0;
}
```

#### 4.8.8 continue 语句

**continue 语句**是继续控制流的逻辑控制流语句，其格式如下：

```ebnf
ContinueStatement = "continue" [ Name ] .
```

其中：

- **定义** `ContinueStatement` 为 continue 语句
  - continue 语句**必须**出现在逻辑控制流中
- **定义** `Name` 为逻辑控制流名称（见 [逻辑控制流名称](#481-逻辑控制流名称)）
  - 逻辑控制流名称**必须**指向已定义的逻辑控制流（见 [逻辑控制流名称](#481-逻辑控制流名称)）

有关行为：

- **当**未给定逻辑控制流名称**时**，**必须**触发满足如下**所有**条件的逻辑控制流的 continue 行为：
  - 支持逻辑控制流名称（见 [逻辑控制流名称](#481-逻辑控制流名称)）
  - 位于最内侧
- **当**给定逻辑控制流名称**时**，**必须**触发对应的逻辑控制流的 continue 行为
- **当**逻辑控制流无特殊 continue 行为**时**，其**必须**执行默认 continue 行为

有关默认 continue 行为：

1. 退出当前 `Block`，继续控制流

例如：

```novasharp
// 定义：函数 Main
constant Main(): integer(4)
{
    for i: integer(4) in 1..10 : Outer
    {
        while true : Inner
        {
            // 合法：退出内部循环，继续外部循环
            continue Outer
        }
    }

    match 2
    {
        case > 1
        {
            // 合法：退出当前 case 并尝试继续向下匹配
            continue;
        }
        case 1
        {
            // 该 Block 不会执行：2 == 1 不成立
            // 注意：NovaSharp 不会 fall-through
        }
        case wildcard
        {
            // 该 Block 会被执行：模式匹配通过
        }
    }

    if 1 + 1 == 2
    {
        // 非法：没有可被 continue 的逻辑控制流语句
        // continue;
        // 错误：意外的 continue
    }

    return 0;
}
```

### 4.9 控制流

#### 4.9.1 异常处理

**异常处理**是程序处理错误和意外情况的方式。

**允许**借助 `throw` 语句（见 [throw 语句](#493-throw-语句)）与 `trap` 语句（见 [trap 语句](#494-trap-语句)）进行异常处理。

要求 Built-In Library **必须**在全局作用域下定义 `Exception`、`NotImplementedException`、`DivideByZeroException`、`OutOfRangeException`、`AllocateFailedException` 和 `DeallocateFailedException` 类（见 [Built-In Library 完整内容](#152-built-in-library-完整内容)）。

其中：

- **定义** `Exception` 为异常基类
- **定义** `NotImplementedException` 为未实现异常
- **定义** `DivideByZeroException` 为除 0 异常
- **定义** `OutOfRangeException` 为越界异常
- **定义** `AllocateFailedException` 为分配失败异常
- **定义** `DeallocateFailedException` 为释放失败异常
- **定义**运行时异常为语言规定的、在运行期因操作失败而自动产生的异常值
- **定义**词法 `trap` 为 `TrapBody` 在词法上包含产生运行时异常的表达式的 `trap` 语句
- 有关运行时异常的来源，见 [基本类型](#22-基本类型)、[索引访问表达式](#354-索引访问表达式)、[堆分配](#45-堆分配)、[dispose 语句](#47-dispose-语句)

有关运行时异常：

- 运行时异常**仅**包括 `DivideByZeroException`、`OutOfRangeException`、`AllocateFailedException` 与 `DeallocateFailedException`
- **当**产生运行时异常的表达式不在任何词法 `trap` 内**时**，程序**必须**终止
- **当**产生运行时异常的表达式在词法 `trap` 内**时**，该运行时异常**必须**由最近的、能匹配的词法 `trap` 拦截
  - 匹配规则与 `throw` 相同（见 [trap 语句](#494-trap-语句)）
  - **当**词法 `trap` 链中不存在匹配的 `catch` **时**，程序**必须**终止
  - 运行时异常所经过的 `trap` 的 `finally` **必须**按 [trap 语句](#494-trap-语句) 执行
- 运行时异常与词法 `trap` 的对应关系**必须**在编译期确定
  - 该确定**不得**依赖调用栈**或**内联等实现细节

#### 4.9.2 return 语句

**return 语句**是通过传递返回值直接退出函数的语句，其格式如下：

```ebnf
ReturnStatement = "return" [ Expression ] .
```

其中：

- **定义** `ReturnStatement` 为 return 语句
  - return 语句**必须仅**出现在函数体中（见 [函数](#1710-函数)）
- **定义** `Expression` 为返回值表达式（见 [表达式](#31-表达式)）
  - 返回值表达式的返回值类型**必须为**所在函数的返回值类型**或**可隐式转换为所在函数的返回值类型
  - **当** return 语句出现在返回值类型为空类型（见 [类型构造器](#261-类型构造器)）的函数中**时**，**允许**省略返回值表达式

有关行为：

- **必须**将返回值表达式的返回值作为函数的返回值，并以返回值退出函数
- **定义**上述行为为 return 语句的行为
- **当**返回值类型为引用类型**时**，实例本体**必须**被构造到调用方提供的存储中
- **当**返回值表达式为标识符**且**该标识符的存储为实例本体**时**，编译器**必须**将该实例构造到调用方提供的存储中
  - **若**上述构造无法被确定，**则**编译器**必须**报错

> [!NOTE] 引用类型的返回实例由调用方提供的存储承载
> 被调用方不拥有该实例的存储，因此 `return MyClass();` 不会让实例落在本帧的作用域存储期里——它从一开始就构造在调用方的存储中。
> `variable a = MyClass(); return a;` 依赖编译器把 `a` 的存储消除到该存储中；消除成立时，交回调用方的不是指向本帧的引用，而是调用方自己存储中的那个实例。

有关控制流：

- 返回值类型不为空类型的函数**必须**在所有路径上以 return 语句终止，**或**以未被本函数内任何 `trap` 拦截的 `throw` 语句终止
- **允许**返回值类型为空类型的函数在所有控制流路径上不以 return 语句终止
- 上述判定**必须**由编译器执行，**且**判定**必须**与具体控制流结构无关
- 有关 `??` 的 `return` 续体，见 [空值合并表达式](#31027-空值合并表达式)

例如：

```novasharp
constant ReturnNumber(): integer(4)
{
    // 合法：类型相同
    return 14;
}

// 定义：枚举 Status
enumeration Status: unsigned integer(2) { Idle; Running; }

constant ReturnShort(): unsigned integer(2)
{
    // 合法：枚举值可单向隐式转换为其底层类型值（见 [枚举](#274-枚举)）
    return Status.Running;
}

constant ReturnEmpty()
{
    // 合法：返回值类型为空类型时省略返回值表达式
    return;
}

// 示例：泛型
constant Echo<T>(value: T): T
{
    // 合法：类型相同
    return value;
}

// 非法：存在不以 return 语句终止的控制流路径
// constant Bad: function(flag: boolean) integer(4)
// {
//     if (flag)
//     {
//         return 1;
//     }
// }
// 错误：返回值类型不为空类型的函数必须在所有控制流路径上以 return 语句终止

// 非法：return 语句只能出现在函数体内部
// return 0;
// 错误：意外的 return 语句
```

#### 4.9.3 throw 语句

**throw 语句**是在 `trap` 或 `catch` 中抛出一个值、交由 `trap` 拦截的本地控制流语句，其格式如下：

```ebnf
ThrowStatement = "throw" Expression .
```

其中：

- **定义** `ThrowStatement` 为 throw 语句
  - throw 语句**必须仅**出现在 `trap` 块**或** `catch` 块中（见 [trap 语句](#494-trap-语句)）
- **定义** `Expression` 为抛出值表达式（见 [表达式](#31-表达式)）

有关行为：

- **必须**求值抛出值表达式，**并**将结果作为抛出值
- 抛出值**必须**交由最近的、能够拦截它的 `trap` 处理
- **当**抛出值不被任何 `trap` 拦截**时**，程序**必须**终止

有关类型：

- 抛出值**允许**为任意类型
- `trap` 的拦截条件**必须**按抛出值的类型匹配（见 [trap 语句](#494-trap-语句)）
- `throw` 语句**不是**运行时异常的产生方式；运行时异常由语言在运行期自动产生（见 [异常处理](#491-异常处理)）

例如：

```novasharp
// 合法：throw 在 trap 块内
constant Handle()
{
    trap
    {
        throw OutOfRangeException();
    }
    catch error: OutOfRangeException
    {
        // 拦截
    }
}

// 合法：throw 在 catch 块内，交由外层 trap
constant Nested()
{
    trap
    {
        trap
        {
            variable value: integer(4) = 1;
            throw value;
        }
        catch error: integer(4)
        {
            throw OutOfRangeException();
        }
    }
    catch error: Exception
    {
        // 拦截内层 catch 抛出的异常
    }
}

// 非法：throw 不在 trap 或 catch 块内
// throw 1;
// 错误：throw 语句必须仅出现在 trap 块或 catch 块中
```

#### 4.9.4 trap 语句

**trap 语句**是拦截本块及内层 `trap` 中产生的抛出值的本地控制流语句，其格式如下：

```ebnf
TrapStatement  = "trap" TrapBody { "catch" CatchCondition CatchBlock } [ "finally" FinallyBlock ] .

TrapBody       = Block .
CatchBlock     = Block .
FinallyBlock   = Block .
CatchCondition = [ Name ":" ] Type
               | "wildcard" .
```

其中：

- **定义** `TrapStatement` 为 trap 语句
  - trap 语句**必须仅**出现在函数体中（见 [函数](#1710-函数)）
- **定义** `TrapBody` 为语句体
- **定义** `CatchBlock` 为拦截块
- **定义** `FinallyBlock` 为最终块
- **定义** `CatchCondition` 为拦截条件
- **定义** `wildcard` 为捕获所有抛出值且不绑定的拦截条件
- **定义** `Name` 为被拦截值名称（见 [标识符](#14-标识符)）
  - **当** `Name` 省略**时**，**判定**拦截条件不绑定被拦截值
- **定义** `Type` 为目标类型（见 [类型构造语法](#21-类型构造语法)）
- 有关 `Block`，见 [代码块](#42-代码块)
- `catch` 绑定的类型**允许**使用 [标识符定义简写](#15-标识符定义简写)

有关拦截：

- 运行时异常**必须**按抛出值处理（见 [异常处理](#491-异常处理)）
- **当**抛出值在语句体内产生，**或**在内层 `trap` 中产生且未被内层 `trap` 拦截，到达当前 `trap` 语句**时**，**若** trap 语句携带 `catch`，**必须**尝试拦截
- **当**尝试拦截**时**，**必须**终止执行语句体**并**按照 `catch` 的先后顺序匹配拦截条件
- **当**拦截条件为 `wildcard` **时**，匹配**必须**成功
- **当**拦截条件不是 `wildcard`**时**，目标类型等于抛出值的类型，**或**目标类型为抛出值类型的基类**或**接口**时**，匹配成功；**否则**匹配失败
- `wildcard` **必须**为最后一个 `catch` 条件
- **当**拦截块中抛出值**时**，**不得**被当前 trap 语句拦截
- **当**所有 `catch` 条件均不匹配**时**，退出 trap 语句；**当**外层 `trap` 可拦截**时**，抛出值继续交由外层处理；**否则**程序**必须**终止

有关拦截匹配成功时的行为：

1. **若**对应 `catch` 携带被拦截值名称，**则**将抛出值赋给被拦截值名称
2. **必须**执行对应的拦截块
3. 退出 trap 语句

有关最终：

- **当** trap 语句携带 `finally`，**且**满足如下任一条件**时**，**必须**执行最终块：
  - 语句体、拦截块正常退出
  - 语句体、拦截块出现 `return` 语句（见 [return 语句](#492-return-语句)）
  - 语句体、拦截块出现 `break` 语句**或** `continue` 语句（见 [break 语句](#487-break-语句)、[continue 语句](#488-continue-语句)）
  - 语句体、拦截块出现未被当前 trap 拦截的抛出值
- 最终块**不得**包含 `return` 语句、`break` 语句、`continue` 语句**或** `throw` 语句
- **当**最终块退出**时**，**必须**恢复如下行为（如有）：
  - 被拦截的 `return` 语句
  - 未拦截成功的抛出值的继续传播
  - 拦截块内部的 `throw` 语句
  - `break` 语句
  - `continue` 语句

例如：

```novasharp
// 合法：throw 在 trap 体内，由 catch 拦截
constant Handle(): integer(4)
{
    trap
    {
        throw OutOfRangeException();
    }
    catch error: OutOfRangeException
    {
        return 1;
    }

    return 0;
}

// 合法：内层 catch 不匹配，外层 catch 以基类拦截
constant Nested(): integer(4)
{
    trap
    {
        trap
        {
            throw OutOfRangeException();
        }
        catch error: DivideByZeroException
        {
            // 不匹配
        }
    }
    catch error: Exception
    {
        return 1;
    }

    return 0;
}

// 合法：finally 在 return 之前执行
constant WithFinally(): integer(4)
{
    trap
    {
        return 1;
    }
    finally
    {
        // 在 return 之前执行
    }
}

// 合法：wildcard 捕获所有抛出值且不绑定
trap
{
    throw OutOfRangeException();
}
catch wildcard
{
}

// 非法：trap 语句出现在函数体外
// trap { }
// catch error: Exception { }
// 错误：trap 语句必须仅出现在函数体中

// 非法：最终块包含 return
// trap { }
// finally { return; }
// 错误：最终块不得包含 return 语句
```

## 5. 名称

### 5.1 作用域

**作用域**是代码中标识符（见 [标识符](#14-标识符)）的有效范围边界。

作用域由以下形式之一组成：

- 全局作用域
- 文件作用域
- 模块作用域
- 类型作用域
- 函数作用域
- 语句作用域

其中：

- **定义**文件作用域为源代码文件的最外层作用域
- **定义**模块作用域为模块（见 [模块](#61-模块)）声明体构成的作用域
- **定义**外层作用域为直接包含当前作用域的上一级作用域
- **定义**内层作用域为被当前作用域直接包含的下一级作用域

有关语法：

- **若**源代码文件**未**包含模块声明，**则**该文件的所有内容处于全局作用域内
- 内层作用域**必须**可访问外层作用域的标识符
- 外层作用域**不得**访问内层作用域的标识符
- **允许**模块作用域嵌套（见 [模块](#61-模块)）
- `#{ ... }` **不得**构成作用域；其中声明**必须**属于外层作用域（见 [编译期块](#104-编译期块)）

### 5.2 可访问性

**可访问性**是标识符对外部作用域的可见程度。

其中：

- 标识符的默认可访问性**必须**按 [可访问性修饰符](#82-可访问性修饰符) 的规定确定
- **允许**使用可访问性修饰符（见 [可访问性修饰符](#82-可访问性修饰符)）覆盖默认可访问性

有关约束：

- **若**标识符被可访问性修饰符（见 [可访问性修饰符](#82-可访问性修饰符)）限制，**则**外层作用域**不得**访问该标识符

### 5.3 标识符唯一性

**标识符唯一性**是同一作用域内不得出现同名标识符的约束。

其中：

- 同一作用域内**不得**定义同名标识符

有关例外：

- 对于函数常量（见 [函数类型构造器](#264-函数类型构造器)），**允许**在同一作用域内出现参数列表不同、同名的函数常量（见 [重载决议](#75-重载决议)）
- 对于方法（见 [方法](#74-方法)），**允许**出现同名方法，**当且仅当**满足如下**任一**条件：
  - `this` 参数类型不同
  - 移除 `this` 参数后，参数列表不同
- 对于类（见 [类](#271-类)），派生类的标识符**允许**与基类的同名标识符共存，**并**遮蔽基类的标识符（见 [遮蔽](#54-遮蔽)）
  - 有关重写，见 [类](#271-类)

有关语法：

- 标识符的访问**不得**受定义先后顺序的限制
  - **若**访问发生在函数体之外，**则**先定义的标识符**允许**访问后定义的标识符

### 5.4 遮蔽

**遮蔽**是内层作用域中的标识符使外层作用域同名标识符不可直接访问的机制。

其中：

- **判定**标识符 `X` 遮蔽标识符 `Y`，当且仅当满足如下所有条件：
  - `X` 与 `Y` 同名
  - `X` 定义于内层作用域
  - `Y` 定义于外层作用域

有关语法：

- **若**名称被遮蔽，**则**在内层作用域中直接访问该名称**时**，解析为内层作用域的定义
- **允许**使用关键字 `owner` 访问被遮蔽的外层作用域名称
  - `owner` 后紧跟 `.` 和名称
  - **当**访问被遮蔽的名称**时**，**必须**经成员访问表达式访问（见 [成员访问表达式](#352-成员访问表达式)）
  - `owner` 访问的是直接外层作用域中的名称
  - **允许** `owner` 嵌套使用；每嵌套一层，向外扩展一层作用域

例如：

```novasharp
// 定义：全局变量 a
variable a: integer(4) = 1;

constant Main(): integer(4)
{
    // 定义：局部变量 a，遮蔽全局变量 a
    variable a: integer(4) = 2;

    // 合法：访问局部变量 a
    variable b: integer(4) = a; // b = 2

    // 合法：使用 owner 访问被遮蔽的全局变量 a
    variable c: integer(4) = owner.a; // c = 1

    {
        // 定义：代码块内的局部变量 a，遮蔽 Main 的 a
        variable a: integer(8) = 3;

        // 合法：嵌套 owner
        variable d: integer(4) = owner.owner.a; // d = 1
    }

    return 0;
}
```

## 6. 模块

### 6.1 模块

**模块**是组织标识符的命名空间，其格式如下：

```ebnf
ModuleDeclaration = { Modifier } "module" Name Block .
```

其中：

- **定义** `ModuleDeclaration` 为模块声明
- **定义** `Modifier` 为修饰符（见 [修饰符](#81-修饰符)）
- **定义** `Name` 为模块名（见 [标识符](#14-标识符)）
- **定义** `Block` 为模块的体（见 [代码块](#42-代码块)）

有关模块声明：

- 修饰符列表**必须**位于 `module` 之前
- 模块的体**必须**为 `Block`（见 [代码块](#42-代码块)）
- 模块**必须**构成模块作用域（见 [作用域](#51-作用域)）
- 模块**不得**作为类型使用
- **允许**模块声明嵌套

有关类型中的模块：

- 类型声明体（见 [类](#271-类)、[结构体](#272-结构体)、[接口](#273-接口)）内的模块**仅**用于标识符整理
- 类型声明体中的模块**不得**产生运行时实体

例如：

```novasharp
// 合法：块级模块
module MyModule
{
    variable Flag: boolean = true;

    // 合法：嵌套模块
    module MySubModule
    {

    }
}

// 非法：将模块用作类型
// variable bad: MyModule;
// 错误：模块不得作为类型使用
```

### 6.2 导入

**导入**是将目标标识符的成员引入当前作用域的语句，其格式如下：

```ebnf
ImportStatement = "import" Identifier .
```

其中：

- **定义** `ImportStatement` 为导入语句
- **定义** `Identifier` 为被导入的目标（见 [标识符](#14-标识符)）

有关导入：

- 导入语句**必须**将目标标识符的成员导入当前作用域
- 导入语句**必须**以分号 `;` 终止（见 [语句终止](#18-语句终止)）

有关作用域：

- 导入语句**允许**出现在任意代码块中
- 导入语句**必须**仅对其所在作用域中位于其后的代码生效
- 导入语句**不得**提升

例如：

```novasharp
// 定义：模块 MyModule
module MyModule
{
    variable Flag: boolean = true;
}

// 合法：导入模块的成员
import MyModule;

// 合法：在代码块中导入，仅对该块内其后的代码生效
constant Main(): integer(4)
{
    import Math;

    return 0;
}
```

## 7. 函数

### 7.1 函数定义语法糖

**函数定义语法糖**是在常量定义中以 `Block` 替代 `= <函数字面量>` 的语法形式，其格式如下：

```ebnf
FunctionDeclarationSugar = { Modifier } "constant" Name [ GenericParameters ] ":" FunctionTypeConstructor Block .
```

其中：

- **定义** `FunctionDeclarationSugar` 为函数定义语法糖
- **定义** `Name` 为名称（见 [标识符](#14-标识符)）
- **定义** `FunctionTypeConstructor` 为函数类型（见 [函数类型构造器](#264-函数类型构造器)）
- 有关 `GenericParameters`，见 [泛型参数](#91-泛型参数)
- 有关 `Block`，见 [代码块](#42-代码块)

有关适用：

- 常量类型**必须**为函数类型
- 常量类型**必须**携带参数名（见 [函数类型构造器](#264-函数类型构造器)）
- 本语法糖**允许**用于所有自定义类型的函数成员
- 本语法糖**允许**用于扩展内的函数成员
- 函数字段由字段定义规则管辖；本语法糖不适用于字段
- **允许**使用函数简写；函数简写**必须**在类型检查前展开为本语法糖的形式（见 [标识符定义简写](#15-标识符定义简写)）

有关展开：

- **当**满足上述条件**时**，`Block` **必须**展开为 `= <函数字面量>`
  - 展开出的函数字面量**必须**以常量类型的参数列表为参数列表
  - 展开出的函数字面量**必须**以常量类型的返回值类型为返回值类型
  - 展开出的函数字面量**不得**携带返回值类型之外的额外标注

有关方法：

- `this` 参数**必须**显式书写，**不得**隐式插入（见 [方法](#74-方法)）

有关初始化：

- **当**不提供 `Block` **时**，常量**必须**被赋值，即 `=` **必须**出现（见 [常量](#44-常量)）
- **当**处于接口声明体中**时**，上述约束**不得**适用（见 [接口](#273-接口)）

例如：

```novasharp
// 合法：函数常量
constant Main: function() integer(4)
{
    return 0;
}

// 合法：函数简写，展开为上述显式形式
constant Shorthand(): integer(4)
{
    return 0;
}

// 合法：脱糖写法
constant Desugar: function() =
    () =>
    {

    };

// 合法：泛型函数常量
constant Echo<T>: function(value: T) T
{
    return value;
}

// 定义：类 MyClass
class MyClass
{
    extension
    {
        // 合法：方法
        public constant Inc: function(this: MyClass)
        {

        }

        // 合法：普通函数常量
        public constant F: function()
        {

        }
    }

    // 合法：函数字段，属于字段定义，不使用本语法糖
    public Callback: function();
}

// 非法：省略 this 参数
// class Bad
// {
//     extension
//     {
//         public constant Inc: function() { }
//         public constant Wrong: function(this: Bad)
//         {
//             this.Inc();
//         }
//     }
// }
// 错误：this 参数必须显式书写

// 非法：无 Block 且无赋值
// constant Bad: function();
// 错误：常量必须被初始化

// 非法：非函数类型使用该语法糖
// constant Bad: integer(4) { }
// 错误：函数定义语法糖的常量类型必须为函数类型
```

### 7.2 参数

**参数**是声明函数所接受值的形式，其格式如下：

```ebnf
Parameters        = Parameter { "," Parameter } .

Parameter         = [ "#" ] [ Name ":" ] [ "&" ] Type [ "=" Expression ] .

LiteralParameters = LiteralParameter { "," LiteralParameter } .

LiteralParameter  = [ "#" ] Name [ ":" [ "&" ] Type ] .
```

其中：

- **定义** `Parameters` 为函数类型构造器的参数列表
- **定义** `Parameter` 为函数类型构造器的参数
- **定义** `LiteralParameters` 为函数字面量的参数列表
- **定义** `LiteralParameter` 为函数字面量的参数
- **定义** `Name` 为参数名（见 [标识符](#14-标识符)）
  - **当**参数名为 `this` **时**，**判定**该参数为 this 参数（见 [方法](#74-方法)）
  - `this` 在参数列表中**最多**出现一次
- **定义** `Type` 为参数类型（见 [类型构造语法](#21-类型构造语法)）
- **定义** `Expression` 为默认值表达式（见 [表达式](#31-表达式)）

有关参数列表：

- 参数之间**必须**以逗号 `,` 分隔
- 函数类型构造器的参数类型**必须**出现
- 函数字面量的参数类型**允许**省略
  - **当**省略参数类型**时**，该参数的类型**必须**由期望的函数类型推断
  - **当**无法推断**时**，编译器**必须**报错
- 函数字面量的参数**不得**携带默认值表达式（见 [函数](#1710-函数)）
- 参数类型**允许**使用 [标识符定义简写](#15-标识符定义简写) 替代 `Name ":" Type`

有关参数名：

- 函数字面量的参数名**必须**出现
- 函数类型构造器的参数名**必须**出现，**但**以下情况除外：
  - 参数名在所在上下文中无用
- **当**参数名省略**时**，参数**必须**仅由类型声明
  - 默认值表达式**不得**在参数名省略时出现
- `#` 是编译期常量参数约定，不是参数名的一部分
- **当**参数携带 `#` **时**，其名称**允许**省略；省略时写作 `#Type`
- `this` 参数**不得**携带 `#`

有关编译期常量参数：

- **当**参数前携带 `#` **时**，**判定**该参数为编译期常量参数
- 编译期常量参数的实参**必须**为编译期常量（见 [编译期常量参数](#105-编译期常量参数)）
- 编译期常量参数**必须**参与函数类型相等与重载签名（见 [函数类型构造器](#264-函数类型构造器)、[重载决议](#75-重载决议)）
- 函数**必须**按编译期常量参数的实参单态化（见 [编译期常量参数](#105-编译期常量参数)）
- 编译期常量参数在函数体内是编译期绑定；运行期**不得**访问该绑定

有关引用参数：

- **当**类型前紧邻字符 `&` **时**，**判定**该参数为引用参数（见 [引用](#25-引用)）
- 引用参数**必须**按引用传递
- `&` **不是**类型的一部分，不参与类型相等与重载签名（见 [函数类型构造器](#264-函数类型构造器)、[重载决议](#75-重载决议)）

有关默认值表达式：

- 携带默认值表达式的 `Parameter` 后**不得**出现**无**默认值表达式的 `Parameter`
- **允许**调用方省略携带默认值表达式的参数（见 [实参](#73-实参)）

例如：

```novasharp
// 合法：函数类型构造器，参数名可省略
variable Callback(integer(4));
variable Named(value: integer(4));
variable Ref(&integer(4));
variable NamedRef(value: &integer(4));

// 合法：编译期常量参数
variable CompileTime(#integer(4));
variable NamedCompileTime(#value: integer(4));

// 合法：携带默认值
variable WithDefault(value: integer(4) = 0): integer(4);

// 合法：this 参数
variable WithThis(this: MyClass);

// 合法：函数字面量，参数类型推断
variable F(value: integer(4)): integer(4) =
    (value) integer(4) => value;

// 合法：函数字面量，引用参数类型推断
variable G(value: &integer(4)): integer(4) =
    (value: &integer(4)) integer(4) => value;

// 非法：函数字面量省略参数名
// variable Bad: function(integer(4)) integer(4) =
//     (integer(4)) integer(4) => 0;
// 错误：函数字面量的参数名必须出现

// 非法：函数字面量携带默认值
// variable Bad: function(value: integer(4)) integer(4) =
//     (value: integer(4) = 0) integer(4) => value;
// 错误：函数字面量的参数不得携带默认值表达式
```

### 7.3 实参

**实参**是调用方传入函数的值，其格式如下：

```ebnf
Arguments = [ Argument { "," Argument } ] .

Argument = [ Name ":" ] Expression .
```

其中：

- **定义** `Arguments` 为实参列表
- **定义** `Argument` 为实参
- **定义** `Name` 为实参名（见 [标识符](#14-标识符)）
- **定义** `Expression` 为实参值表达式（见 [表达式](#31-表达式)）

有关实参列表：

- 实参之间**必须**以逗号 `,` 分隔
- **当**实参携带实参名**时**，其后的所有实参**必须**携带实参名

有关代入：

- **若**实参不携带实参名，**则**按照其在实参列表的顺序，代入函数
- **若**实参携带实参名，**则**将其代入函数的对应参数（见 [参数](#72-参数)）
- 实参的返回值类型**必须为**对应参数的类型**或**可隐式转换为对应参数的类型
- **当**对应参数携带 `#` 约定**时**，实参表达式**必须**为编译期常量（见 [编译期常量参数](#105-编译期常量参数)）
- **当**多个实参被代入函数的同一个参数**时**，**则**编译器**必须**报错

有关省略：

- **允许**实参被省略，**当且仅当**满足如下**所有**条件：
  - 使用函数标识符
  - 该实参在函数标识符所指向的函数中所对应的参数具有默认值（见 [参数](#72-参数)）
- **当**实参被省略**时**，其值**必须**被视为对应参数的默认值
- **当**实参未被省略**时**，其值**必须**被视为对应 `Expression` 的返回值

例如：

```novasharp
// 定义：函数 Echo
constant Echo(value: integer(4)): integer(4)
{
    return value;
}

// 定义：函数 WithDefault
constant WithDefault(value: integer(4) = 0): integer(4)
{
    return value;
}

// 合法：按顺序传入实参
variable a: integer(4) = Echo(1);

// 合法：携带实参名
variable b: integer(4) = Echo(value: 2);

// 合法：省略具有默认值的实参
variable c: integer(4) = WithDefault();

// 非法：命名实参之后出现无名实参
// variable bad: integer(4) = Echo(value: 1, 2);
// 错误：命名实参后的所有实参必须携带实参名
```

### 7.4 方法

**方法**是声明在扩展块内、`this` 参数的类型为扩展目标类型的函数常量，用于直接操作实例及实例成员。

其中：

- **定义**方法为声明在扩展块内、`this` 参数的类型为扩展目标类型的函数常量（见 [常量](#44-常量)、[函数类型构造器](#264-函数类型构造器)）
- **定义**目标类型为 `this` 参数的类型
- **定义**扩展方法为在扩展块内声明的方法（见 [扩展](#283-扩展)）

有关判定：

- **判定**函数常量为方法，**当且仅当**满足如下**所有**条件：
  - 该常量声明在扩展块内
  - 该常量的常量类型的参数列表中含有 `this` 参数
  - 该常量不以 `static` 修饰（见 [static 修饰符](#816-static-修饰符)）
  - 该 `this` 参数的类型**必须为**扩展目标类型（见 [扩展](#283-扩展)）
- **当**函数常量声明在扩展块之外**时**，其**不得**携带 `this` 参数
- 扩展块内携带其他类型 `this` 参数的函数常量**不得**被判定为方法

有关 this 参数：

- `this` 参数**必须**显式书写，**不得**隐式插入
- `this` 参数**允许**出现在参数列表的任意位置
- **当**目标类型为值类型**时**，`this` 参数的类型前**必须**写 `&`（见 [引用](#25-引用)）
- **当**目标类型为引用类型**时**，`this` 参数的类型前**不得**写 `&`
- `this` 参数**必须**允许访问目标类型的私有成员
- 方法**必须**通过成员访问表达式调用（见 [成员访问表达式](#352-成员访问表达式)）
- 方法**不得**以普通函数调用形式显式传入 `this` 参数
- 方法**不得**进入目标类型的内存布局

有关参数列表：

- **定义**方法的参数列表为去除 `this` 参数后的参数列表

有关泛型：

- 方法**允许**携带泛型参数（见 [泛型参数](#91-泛型参数)）

例如：

```novasharp
// 定义：类 Counter
class Counter
{
    public Count: integer(4);

    extension
    {
        public constant Construct(this: Counter)
        {
            this.Count = 0;
        }

        public constant Increment(this: Counter)
        {
            this.Count = this.Count + 1;
        }
    }
}

// 定义：结构体 ValueCounter
// 合法：值类型方法，this 参数类型前必须写 &
structure ValueCounter
{
    public Count: integer(4);

    extension
    {
        public constant Increment(this: &ValueCounter)
        {
            this.Count = this.Count + 1;
        }
    }
}

// 合法：扩展方法，声明在扩展块内
extension for Counter
{
    public constant Reset(this: Counter)
    {
        this.Count = 0;
    }
}

// 定义：函数 Main
constant Main(): integer(4)
{
    variable c: Counter = Counter();
    c.Increment();
    c.Reset();

    return 0;
}

// 非法：值类型的 this 参数类型前未写 &
// structure Bad
// {
//     extension
//     {
//         public constant Increment: function(this: Bad) { }
//     }
// }
// 错误：值类型方法的 this 参数类型前必须写 &

// 非法：静态函数常量的参数列表含有 this 参数
// class BadStatic
// {
//     extension
//     {
//         public static constant F: function(this: BadStatic) { }
//     }
// }
// 错误：静态函数常量的参数列表不得含有 this 参数

// 非法：在扩展块之外携带 this 参数
// constant Reset: function(this: Counter) { }
// 错误：函数常量不得在扩展块之外携带 this 参数

// 非法：以普通函数调用形式显式传入 this 参数
// Reset(c);
// 错误：方法不得以普通函数调用形式显式传入 this 参数
```

### 7.5 重载决议

**重载决议**是从同名函数常量中选取被调用者的编译期过程。

其中：

- **定义**重载决议为从同名函数常量**或**运算符定义中选取被调用者的编译期过程
- **定义**参数列表为参数数量、顺序与类型的列表（见 [参数](#72-参数)）
- **定义**精确匹配为实参类型与参数类型相同
- 重载决议**必须**在编译期完成
- 重载决议**必须仅**依据实参的类型
- 返回值类型**不得**参与重载决议

有关判定：

- **当**实参类型精确匹配唯一一个函数常量**时**，调用该函数常量
- **当**实参类型精确匹配多个函数常量**时**，编译器**必须**报错
- **当**实参类型不精确匹配任何函数常量**时**：
  - **若**恰有一个函数常量的参数类型与实参类型相同**或**可接受实参的隐式转换，**则**调用该函数常量
  - **当**多个函数常量的参数类型均可接受**时**，编译器**必须**报错
    - 调用方**必须**以显式 `Cast` 使实参精确匹配唯一一个函数常量
  - **当**无函数常量的参数类型可接受**时**，编译器**必须**报错

有关签名：

- 引用标记 `&` **不得**参与重载决议（见 [参数](#72-参数)）
- 参数名与默认值表达式**不得**参与重载决议（见 [参数](#72-参数)）
- 编译期常量参数约定 `#` **必须**参与重载决议和签名（见 [参数](#72-参数)、[编译期常量参数](#105-编译期常量参数)）

有关调用约定：

- 仅调用约定不同的函数常量**不得**共存（见 [函数类型构造器](#264-函数类型构造器)、[标识符唯一性](#53-标识符唯一性)）
- 调用约定**不得**参与重载决议
- 调用约定**不得**参与签名（见 [函数类型构造器](#264-函数类型构造器)）

有关适用：

- 运算符定义**必须**按本章规则分派（见 [运算符重载](#3103-运算符重载)）
- 方法的重载决议**必须**按参数列表的声明顺序进行，`this` 参数**不得**被移动到其它位置（见 [方法](#74-方法)）
- 泛型函数常量**必须**先单态化、再进行重载决议（见 [单态化表达式](#92-单态化表达式)）

例如：

```novasharp
// 定义：函数常量 Calculate
constant Calculate(a: integer(4), b: integer(4)): integer(4)
{
    return a + b;
}

// 定义：函数常量 Calculate
// 合法：同名但参数列表不同
constant Calculate(a: float(4), b: float(4)): float(4)
{
    return a + b;
}

// 定义：函数 Main
constant Main(): integer(4)
{
    // 合法：按实参类型决议到整数版本
    variable i: integer(4) = Calculate(1, 2);

    // 合法：按实参类型决议到浮点版本
    variable f: float(4) = Calculate(1.0, 2.0);

    // 非法：无匹配的重载
    // variable bad: integer(4) = Calculate(true, false);
    // 错误：实参类型无匹配的函数常量

    return 0;
}

// 非法：仅返回值类型不同
// constant Bad: function() integer(4) { return 0; }
// constant Bad: function() boolean { return false; }
// 错误：函数常量之间的参数列表不得重复

// 非法：仅调用约定不同
// constant Bad: function() { }
// constant Bad: function(; CDeclaration) { }
// 错误：函数常量之间的参数列表不得重复

```

## 8. 修饰符

### 8.1 修饰符

**修饰符**是位于标识符种类之前、用于限定标识符行为的语法形式，其格式如下：

```ebnf
Modifier = AccessibilityModifier
         | BehaviorLimitingModifier
         | BehaviorEnablingModifier
         | OptimizationModifier
         | OtherModifier .

BehaviorLimitingModifier = ReadonlyModifier .

BehaviorEnablingModifier = ImplicitableModifier .

OptimizationModifier = VerbatimModifier .

OtherModifier = LinkableModifier
              | AbstractModifier
              | SealedModifier
              | VirtualModifier
              | OverrideModifier
              | AlignedModifier
              | StaticModifier .
```

其中：

- **定义** `Modifier` 为修饰符
- **定义** `AccessibilityModifier` 为可访问性修饰符（见 [可访问性修饰符](#82-可访问性修饰符)）
- **定义** `BehaviorLimitingModifier` 为行为限定修饰符
- **定义** `BehaviorEnablingModifier` 为行为激活修饰符
- **定义** `OptimizationModifier` 为优化修饰符
- **定义** `OtherModifier` 为其它修饰符
- **定义** `ReadonlyModifier` 为 `readonly` 修饰符（见 [readonly 修饰符](#87-readonly-修饰符)）
- **定义** `AbstractModifier` 为 `abstract` 修饰符（见 [abstract 修饰符](#811-abstract-修饰符)）
- **定义** `SealedModifier` 为 `sealed` 修饰符（见 [sealed 修饰符](#812-sealed-修饰符)）
- **定义** `VirtualModifier` 为 `virtual` 修饰符（见 [virtual 修饰符](#813-virtual-修饰符)）
- **定义** `OverrideModifier` 为 `override` 修饰符（见 [override 修饰符](#814-override-修饰符)）
- **定义** `AlignedModifier` 为 `aligned(N)` 修饰符（见 [aligned(N) 修饰符](#815-alignedn-修饰符)）
- **定义** `LinkableModifier` 为 `linkable` 修饰符（见 [linkable 修饰符](#810-linkable-修饰符)）
- **定义** `StaticModifier` 为 `static` 修饰符（见 [static 修饰符](#816-static-修饰符)）
- **定义** `VerbatimModifier` 为 `verbatim` 修饰符（见 [verbatim 修饰符](#89-verbatim-修饰符)）
- **定义** `implicitable`、`verbatim` 为关键字（见 [关键字](#16-关键字)）

有关类别：

- 可访问性修饰符由 `public`、`private`、`protected` 和 `scoped` 组成（见 [可访问性修饰符](#82-可访问性修饰符)）
- 行为限定修饰符由 `readonly` 组成（见 [readonly 修饰符](#87-readonly-修饰符)）
- 行为激活修饰符由 `implicitable` 组成
- 优化修饰符由 `verbatim` 组成
- 其它修饰符由 `linkable`、`abstract`、`sealed`、`virtual`、`override`、`aligned(N)` 和 `static` 组成

有关语法：

- 修饰符**必须**位于其目标之前
- **允许**多个修饰符同时出现
- **允许**修饰符以任意顺序出现
- 修饰符之间**必须**以空白分隔
- 同一修饰符**不得**重复出现

有关适用：

- 修饰符**必须仅**修饰其允许的目标
- 有关各修饰符允许的目标，见其页面
- 有关各修饰符的语义，见 [语义映射表](#19-语义映射表)

例如：

```novasharp
// 定义：类 Singleton
// 合法：多个修饰符，顺序任意
public sealed class Singleton
{
    // 定义：常量 Instance
    // 合法：静态只读
    public static readonly Instance: Singleton;
}

// 非法：同一修饰符重复出现
// public public class Bad { }
// 错误：同一修饰符不得重复出现

// 非法：修饰符位于其目标之后
// class public Bad { }
// 错误：修饰符必须位于其目标之前
```

### 8.2 可访问性修饰符

**可访问性修饰符**是限定标识符可被哪些作用域访问的修饰符（见 [可访问性](#52-可访问性)），其格式如下：

```ebnf
AccessibilityModifier = BaseAccessibilityModifier | ScopedModifier .

BaseAccessibilityModifier = PublicAccessibilityModifier
                          | PrivateAccessibilityModifier
                          | ProtectedAccessibilityModifier .
```

其中：

- **定义** `AccessibilityModifier` 为可访问性修饰符
- **定义** `BaseAccessibilityModifier` 为基础可访问性修饰符
- 有关 `PublicAccessibilityModifier`，见 [public 修饰符](#83-public-修饰符)
- 有关 `PrivateAccessibilityModifier`，见 [private 修饰符](#84-private-修饰符)
- 有关 `ProtectedAccessibilityModifier`，见 [protected 修饰符](#85-protected-修饰符)
- 有关 `ScopedModifier`，见 [scoped 修饰符](#86-scoped-修饰符)

有关维度：

可访问性修饰符由以下两个维度组成：

| 维度                   | 修饰符                           | 作用                     |
| ---------------------- | -------------------------------- | ------------------------ |
| **基础可访问性修饰符** | `public`、`private`、`protected` | 给出可访问对象的基础集合 |
| **可访问性裁剪修饰符** | `scoped`                         | 以具名目标收窄基础集合   |

有关组合：

- **定义**标识符的最终可访问性为基础可访问性与**所有**裁剪的交集
- **当**省略基础可访问性修饰符**时**，基础可访问性**必须为** `private`，**但**其种类另有规定者除外（见 [private 修饰符](#84-private-修饰符)）
- 枚举成员、变体状态与共同体成员的基础可访问性**必须为** `public`
- 可访问性裁剪**不得**放宽基础可访问性
- 基础可访问性修饰符**最多**出现一个

有关作用域：

- 可访问性修饰符**允许**出现在任意作用域（见 [作用域](#51-作用域)）
- **当**出现在全局作用域**时**，基础可访问性修饰符**不得**产生区分作用
- **当**出现在模块作用域**时**，`protected` **不得**产生区分作用
- 无区分作用**不得**导致编译器报错

有关函数值：

- **定义**访问权为函数值可访问的成员范围
  - 函数常量的访问权是其声明所在处的访问权
  - 函数字面量的访问权是其书写所在处的访问权
- 函数值**必须**携带其访问权
- **当**承载函数值的位置的可访问范围大于该函数值的访问权**时**，**必须**报错
  - 可访问范围的大小**必须**按作用域的包含关系判定

> [!NOTE] 无区分作用不是错误
> `private` 的作用范围是声明所在作用域，`protected` 的派生作用域来自声明所在类型。
> 在全局作用域中，前者退化为「全部」，后者因不存在声明所在类型而退化；在模块作用域中，后者同样退化。
> 此时修饰符语义仍然成立，故不报错。

例如：

```novasharp
// 定义：类 Container
class Container
{
    extension
    {
        private constant Hidden(): integer(4) { return 0; }

        // 非法：把访问权更大的函数值存入可访问范围更大的位置
        // public Exposed: function() integer(4) = Hidden;
        // 错误：承载函数值的位置的可访问范围大于该函数值的访问权
    }
}

// 定义：类 Animal
class Animal
{
    extension
    {
        // 合法：基础可访问性与裁剪的组合
        public scoped(Animal) constant Shared()
        {

        }
    }
}
```

### 8.3 public 修饰符

**public 修饰符**是声明可被所有作用域访问的基础可访问性修饰符，其格式如下：

```ebnf
PublicAccessibilityModifier = "public" .
```

其中：

- **定义** `PublicAccessibilityModifier` 为公共基础可访问性修饰符
- **定义** `public` 为其关键字（见 [关键字](#16-关键字)）
- **定义** `public` 标识符的可访问对象为所有作用域
- `public` 标识符**必须**可被任意作用域访问

有关语法：

- 修饰符列表**必须**位于标识符种类之前（见 [关键字](#16-关键字)）

有关作用域：

- **当**出现在全局作用域**时**，`public` **不得**产生区分作用（见 [可访问性修饰符](#82-可访问性修饰符)）

例如：

```novasharp
// 定义：类 Animal
class Animal
{
    // 合法：任意作用域均可访问
    public Name: integer(4);
}

// 定义：类 Cat
class Cat: Animal
{
    extension
    {
        public constant Read(this: Cat): integer(4)
        {
            // 合法：访问基类的 public 成员
            return this.Name;
        }
    }
}
```

### 8.4 private 修饰符

**private 修饰符**是声明仅在声明所在作用域内可访问的基础可访问性修饰符，其格式如下：

```ebnf
PrivateAccessibilityModifier = "private" .
```

其中：

- **定义** `PrivateAccessibilityModifier` 为私有基础可访问性修饰符
- **定义** `private` 为其关键字（见 [关键字](#16-关键字)）
- **定义** `private` 标识符的可访问对象为其声明所在作用域、其所属类型的成员以及携带该类型 `this` 参数的函数
- `private` 标识符**必须**仅可被声明所在作用域、其所属类型的成员以及携带该类型 `this` 参数的函数访问，**但**扩展成员的 `private` **必须仅**在该扩展块内可见
- 有关默认可访问性，见 [可访问性修饰符](#82-可访问性修饰符)

有关语法：

- 修饰符列表**必须**位于标识符种类之前（见 [关键字](#16-关键字)）

有关作用域：

- **当**标识符出现在类型声明体中**时**，其可访问对象为该类型的类型作用域（见 [类](#271-类)、[结构体](#272-结构体)）
  - 该类型的其余成员**必须**可访问该标识符
- **当**出现在全局作用域**时**，`private` **不得**产生区分作用（见 [可访问性修饰符](#82-可访问性修饰符)）

例如：

```novasharp
// 定义：类 Counter
class Counter
{
    // 合法：默认可访问性
    Count: integer(4);

    extension
    {
        public constant Increment(this: Counter)
        {
            // 合法：同一类型作用域内可访问私有成员
            this.Count = this.Count + 1;
        }
    }
}

// 定义：类 Spy
class Spy
{
    extension
    {
        public constant Peek(target: Counter): integer(4)
        {
            // 非法：类型作用域之外不可访问私有成员
            // return target.Count;
            // 错误：Count 在当前作用域中不可访问
        }
    }
}
```

### 8.5 protected 修饰符

**protected 修饰符**是声明可被声明所在作用域及其派生作用域访问的基础可访问性修饰符，其格式如下：

```ebnf
ProtectedAccessibilityModifier = "protected" .
```

其中：

- **定义** `ProtectedAccessibilityModifier` 为受保护基础可访问性修饰符
- **定义** `protected` 为其关键字（见 [关键字](#16-关键字)）
- **定义** `protected` 标识符的可访问对象为其声明所在作用域与其派生作用域
- **定义** `protected` 标识符的派生作用域为所有直接或间接继承自声明所在类型的类型（见 [类](#271-类)、[继承列表](#277-继承列表)）
- `protected` 标识符**必须**可被上述两类作用域访问

有关语法：

- 修饰符列表**必须**位于标识符种类之前（见 [关键字](#16-关键字)）

有关作用域：

- **当**出现在全局作用域**或**模块作用域**时**，`protected` **不得**产生区分作用（见 [可访问性修饰符](#82-可访问性修饰符)）

例如：

```novasharp
// 定义：类 Animal
class Animal
{
    // 合法：本类型与派生类型均可访问
    protected Name: integer(4);
}

// 定义：类 Cat
class Cat: Animal
{
    extension
    {
        public constant Read(this: Cat): integer(4)
        {
            // 合法：派生作用域内可访问
            return this.Name;
        }
    }
}

// 定义：类 Stranger
class Stranger
{
    extension
    {
        public constant Peek(target: Animal): integer(4)
        {
            // 非法：既非本类型作用域，也非派生作用域
            // return target.Name;
            // 错误：Name 在当前作用域中不可访问
        }
    }
}
```

### 8.6 scoped 修饰符

**scoped 修饰符**是以具名目标裁剪可访问性的可访问性裁剪修饰符，其格式如下：

```ebnf
ScopedModifier = "scoped" "(" ScopedTarget { "," ScopedTarget } ")" .

ScopedTarget = [ "sealed" ] Identifier
             | "operator" [ Identifier | OperatorSymbol ] .
```

其中：

- **定义** `ScopedModifier` 为 scoped 修饰符
- **定义** `ScopedTarget` 为裁剪目标
- **定义** `sealed` 为继承项取消标记
  - `sealed` 是关键字（见 [关键字](#16-关键字)）
- **定义** `operator` 为运算符作用域标记
  - `operator` 是关键字（见 [关键字](#16-关键字)）
- **定义** `Identifier` 为目标标识符（见 [标识符](#14-标识符)）
- 有关 `OperatorSymbol`，见 [运算符](#3101-运算符)

有关裁剪：

- **定义**裁剪范围为由全部裁剪目标构建的可访问对象集合
- **定义**标识符的最终可访问性为基础可访问性与**所有**裁剪的交集（见 [可访问性修饰符](#82-可访问性修饰符)）
- 单个 `scoped` 中的多个裁剪目标**必须**取并集
- 多个 `scoped` 之间**必须**取交集
- `scoped` **不得**放宽基础可访问性
- `scoped` 的裁剪目标**必须**为具名目标，**不得**为作用域形式

有关裁剪目标：

- **定义**目标 `X` 的自身项为 `X` 自身及其成员
- **定义**目标 `X` 的继承项为所有直接或间接继承自 `X` 的对象及其成员
  - **当** `X` 为成员**时**，上述继承项为 `X` 的 override（见 [override 修饰符](#814-override-修饰符)）
- **当**目标为 `Identifier` 形式**时**，裁剪范围**必须**由自身项与继承项组成
- **当**目标携带 `sealed` **时**，其继承项**必须**被取消，即裁剪范围**仅**包含自身项
- **定义**类型 `X` 的运算符为参数列表中含 `X` 的运算符（见 [运算符](#3101-运算符)）
- `operator` 目标**必须**出现在类型声明体**或**扩展块内
- **当**目标为 `operator` **时**，其裁剪范围为声明所在类型的运算符
- **当**目标为 `operator` `OperatorSymbol` **时**，其裁剪范围为声明所在类型的该符号运算符
- **当**目标为 `operator` `Identifier` **时**，其裁剪范围为转换目标类型为该 `Identifier` 的转换运算符

有关解析：

- **当**目标为相对标识符**时**，其解析**必须**相对于 `scoped` 所在作用域（见 [作用域](#51-作用域)）

例如：

```novasharp
// 定义：类 Animal
class Animal
{
    extension
    {
        // 合法：自身项为 Animal 及其成员，继承项为继承自 Animal 的类型及其成员
        protected scoped(Animal) constant VisibleToAnimal()
        {

        }

        // 合法：目标为成员，继承项即其 override
        protected scoped(Speak) constant VisibleToSpeak()
        {

        }

        // 合法：sealed 取消继承项，仅对 Speak 自身可见
        protected scoped(sealed Speak) constant VisibleToSpeakOnly()
        {

        }

        public virtual constant Speak(this: Animal)
        {
            // 合法：自身项使上述三个常量均可见
        }
    }
}

// 定义：类 Cat
class Cat: Animal
{
    extension
    {
        public override constant Speak(this: Cat)
        {
            // 合法：继承项使 VisibleToAnimal 与 VisibleToSpeak 可见
            // 非法：sealed 已取消继承项
            // VisibleToSpeakOnly;
            // 错误：VisibleToSpeakOnly 仅对 Animal.Speak 可见
        }
    }
}

// 定义：结构体 A
structure A
{
    // 合法：字段对 A 的运算符与 A 自身可见
    public scoped(operator, A) Member: integer(4);

    extension
    {
        public constant Construct(this: &A, member: integer(4))
        {
            this.Member = member;
        }

        // 合法：以 A 为参数的运算符，可访问 A.Member
        operator +(a: A, b: A): A
        {
            return A(a.Member + b.Member);
        }

        // 合法：参数列表含 A（位于第二个参数），故仍可访问 A.Member
        operator +(a: B, b: A): integer(4)
        {
            // 合法：b.Member 可访问
            return b.Member;
        }
    }
}

// 定义：结构体 B
structure B
{
    // 合法：字段对 B 的运算符与 B 自身可见
    public scoped(operator, B) Member: boolean;

    extension
    {
        public constant Construct(this: &B, member: boolean)
        {
            this.Member = member;
        }

        // 合法：以 B 为参数的运算符，可访问 B.Member
        operator ==(a: B, b: B): boolean
        {
            // 非法：A.Member 在此处不可访问
            // variable bad: A = A(1);
            // bad.Member;
            // 错误：bad.Member 仅对 A 的运算符与 A 自身可见

            return a.Member == b.Member;
        }
    }
}
```

### 8.7 readonly 修饰符

**readonly 修饰符**是用于声明只读成员的修饰符，其格式如下：

```ebnf
ReadonlyModifier = "readonly" .
```

其中：

- **定义** `ReadonlyModifier` 为只读成员修饰符
- **定义** `readonly` 为其关键字（见 [关键字](#16-关键字)）
- `readonly` **必须仅**修饰以下目标：
  - `class` 与 `structure` 中的字段（见 [字段](#281-字段)）
- `readonly` **不得**与常量同时出现（见 [常量](#44-常量)）
- **仅允许** `readonly` 成员被初始化，**或**在构造函数中被赋值

### 8.8 implicitable 修饰符

**implicitable 修饰符**是用于声明类型转换可隐式进行的修饰符，其格式如下：

```ebnf
ImplicitableModifier = "implicitable" .
```

其中：

- **定义** `ImplicitableModifier` 为 implicitable 修饰符
- **定义** `implicitable` 为其关键字（见 [关键字](#16-关键字)）
- `implicitable` **必须仅**修饰以下目标：
  - 转换运算符（见 [运算符](#3101-运算符)）

有关行为：

- **当**转换运算符携带 `implicitable` **时**，该转换**允许**被隐式调用（见 [类型转换表达式](#34-类型转换表达式)）
- **当**转换运算符不携带 `implicitable` **时**，该转换**必须仅**经类型转换表达式调用
- **允许**上述隐式调用不受隐式转换无损的约束（见 [核心设计哲学](#141-核心设计哲学)）

例如：

```novasharp
// 定义：结构体 HSLColor
structure HSLColor
{
    extension
    {
        // 定义：转换运算符
        // 合法：允许隐式调用
        implicitable operator HSLColor: function(from: RGBColor) HSLColor
        {
            // ...
        }
    }
}

// 定义：结构体 RGBColor
structure RGBColor
{
    extension
    {
        // 定义：转换运算符
        // 合法：需要显式调用
        operator RGBColor: function(from: HSLColor) RGBColor
        {
            // ...
        }
    }
}

// 定义：函数 Main
constant Main(): integer(4)
{
    variable rgb: RGBColor = RGBColor();
    variable hsl: HSLColor = HSLColor();

    // 合法：经类型转换表达式调用
    variable a: HSLColor = Cast<HSLColor>(rgb);

    // 合法：经隐式转换调用
    variable b: HSLColor = rgb;

    // 非法：目标转换运算符未携带 implicitable
    // variable bad: RGBColor = hsl;
    // 错误：转换运算符必须经类型转换表达式调用

    return 0;
}

// 非法：修饰非转换运算符
// implicitable operator +: function(left: RGBColor, right: RGBColor) RGBColor { }
// 错误：implicitable 的修饰目标必须为转换运算符
```

### 8.9 verbatim 修饰符

**verbatim 修饰符**是用于禁止编译期优化的修饰符，其格式如下：

```ebnf
VerbatimModifier = "verbatim" .
```

其中：

- **定义** `VerbatimModifier` 为 verbatim 修饰符
- **定义** `verbatim` 为其关键字（见 [关键字](#16-关键字)）
- `verbatim` **必须仅**修饰以下目标：
  - 代码块（见 [代码块](#42-代码块)）
  - 变量（见 [变量](#43-变量)）
  - 常量（见 [常量](#44-常量)）

有关行为：

- **定义** `verbatim` 块为携带 `verbatim` 的代码块
- `verbatim` **必须**直接位于代码块之前
- `verbatim` 块的内容**必须**符合所在作用域的语法（见 [代码块](#42-代码块)）
- 编译器**不得**对 `verbatim` 的目标进行任何编译期优化
- **允许**必要的代码生成，**但**其**不得**改变源码结构
- 编译器**不得**在 `verbatim` 的目标中进行编译期求值（见 [编译期执行](#101-编译期执行)）

> [!NOTE] 必要的代码生成不属编译期优化
> 指令选择、寄存器分配、按 ABI 排布栈与参数，这些不做就不成程序，故不受本修饰符约束。

例如：

```novasharp
// 定义：函数常量 Main
constant Main(): integer(4)
{
    // 合法：该块内的初始化式不得被折叠
    verbatim
    {
        variable sum: integer(4) = 1 + 2;
    }

    return 0;
}

```

### 8.10 linkable 修饰符

**linkable 修饰符**是保证函数常量以外部符号暴露的修饰符，其格式如下：

```ebnf
LinkableModifier = "linkable" [ "(" StringLiteral ")" ] .
```

其中：

- **定义** `LinkableModifier` 为 linkable 修饰符
- **定义** `linkable` 为其关键字（见 [关键字](#16-关键字)）
- **定义** `StringLiteral` 为符号名字符串（见 [字符串](#176-字符串)）
- `linkable` **必须仅**修饰函数常量（见 [常量](#44-常量)）

有关符号名：

- **当**省略参数**时**，符号名**必须**为常量名（见 [标识符](#14-标识符)）
- **当**出现参数**时**，符号名**必须**为该字符串字面量的内容
- 符号名**不得**受可访问性管辖
- `linkable` **必须**携带零个**或**一个参数
- 参数**不得**为两个

有关编译：

- 目标符号**必须**以外部链接的形式产生
- 目标符号**不得**被内部化
- 目标符号**不得**因不存在使用者被消除
- `linkable` 的修饰符列表**必须仅**包含可访问性修饰符（见 [可访问性修饰符](#82-可访问性修饰符)）

有关链接：

- `linkable` **仅**保证符号暴露
- `linkable` **不得**负责导入、库解析**或**链接方向
- 运行期所需的库**必须**由 linker 处理
- 编译期所需的库**必须**由编译器命令参数提供
- 源码**不得**携带库名

有关未初始化：

- **当** linkable 函数常量省略 `=` 与 `Block` **时**，符号**必须**由外部提供
- **当** linkable 函数常量省略 `=` 与 `Block` **时**，`:` **必须**出现
- **当** linkable 函数常量使用函数简写**时**，`: Type` **必须**出现

> [!NOTE] 由 linkable 带来的副作用由开发者自行承担
> 越过外部边界后的行为不由本标准规定，编译器不诊断边界之外的行为；例如指针越过边界后的存续、以及目标的分配与释放。

例如：

```novasharp
// 合法：符号名取常量名 ExportSum
public linkable constant ExportSum(a: integer(4), b: integer(4)): integer(4)
{
    return a + b;
}

// 合法：符号名为 Total
public linkable("Total") constant RenamedSum(a: integer(4), b: integer(4)): integer(4)
{
    return a + b;
}

// 合法：私有的 linkable，符号名仍为 Hidden
private linkable constant Hidden(a: integer(4), b: integer(4)): integer(4)
{
    return a - b;
}

// 非法：携带两个参数
// linkable("lib", "Symbol") constant Bad: function() { }

// 非法：参数不为字符串字面量
// linkable(4) constant Bad: function();

// 非法：修饰非函数常量
// linkable constant Answer: integer(4);
```

### 8.11 abstract 修饰符

**abstract 修饰符**是用于声明抽象类的修饰符，其格式如下：

```ebnf
AbstractModifier = "abstract" .
```

其中：

- **定义** `AbstractModifier` 为抽象类修饰符
- **定义** `abstract` 为其关键字（见 [关键字](#16-关键字)）
- `abstract` **必须仅**修饰 `class` 的声明（见 [类](#271-类)）
- 抽象类**不得**被实例化
- 抽象类**允许**携带继承列表
- 抽象类中的 `Construct`/`Destruct` **不得**被识别为构造函数/析构函数；它们是普通方法
- 抽象类的 `Construct`/`Destruct` **允许**被继承
- **当**非抽象类继承抽象类的 `Construct`/`Destruct` **时**，它们**必须**被识别为该类的构造函数/析构函数

### 8.12 sealed 修饰符

**sealed 修饰符**是用于声明不可被继承的类或不可被重写的方法的修饰符，其格式如下：

```ebnf
SealedModifier = "sealed" .
```

其中：

- **定义** `SealedModifier` 为密封修饰符
- **定义** `sealed` 为其关键字（见 [关键字](#16-关键字)）
- `sealed` **必须仅**修饰以下目标：
  - `class` 的声明（见 [类](#271-类)）
  - 重写方法（见 [方法](#74-方法)）

### 8.13 virtual 修饰符

**virtual 修饰符**是用于声明可被重写的方法的修饰符，其格式如下：

```ebnf
VirtualModifier = "virtual" .
```

其中：

- **定义** `VirtualModifier` 为虚方法修饰符
- **定义** `virtual` 为其关键字（见 [关键字](#16-关键字)）
- `virtual` **必须仅**修饰方法（见 [方法](#74-方法)）
- `virtual` **不得**修饰 `structure` 的成员（见 [结构体](#272-结构体)）
- 以 `virtual` 修饰的方法**必须**提供函数体（见 [函数定义语法糖](#71-函数定义语法糖)）

### 8.14 override 修饰符

**override 修饰符**是用于声明重写方法的修饰符，其格式如下：

```ebnf
OverrideModifier = "override" .
```

其中：

- **定义** `OverrideModifier` 为方法重写修饰符
- **定义** `override` 为其关键字（见 [关键字](#16-关键字)）
- `override` **必须仅**修饰满足类中方法重写要求的方法（见 [类](#271-类)、[方法](#74-方法)）
- `override` **不得**修饰 `structure` 的成员（见 [结构体](#272-结构体)）
  - `this` 参数的目标类型**允许**协变替换（见 [类](#271-类)）

### 8.15 aligned(N) 修饰符

**aligned(N) 修饰符**是用于声明结构体默认对齐、结构体字段对齐要求或共同体成员偏移的带参修饰符，其格式如下：

```ebnf
AlignedModifier = "aligned" "(" IntegerLiteral ")" .
```

其中：

- **定义** `AlignedModifier` 为对齐修饰符
- **定义** `aligned` 为其关键字（见 [关键字](#16-关键字)）
- **定义** `IntegerLiteral` 为对齐要求或偏移的字面量（见 [整数](#172-整数)）
- **定义** N 为 `IntegerLiteral` 的值，单位为字节
- N **必须**为非负整数

- **当** `aligned(N)` 修饰 `structure` 声明**时**：
  - N **必须**为全部字段的默认对齐要求
  - 字段的默认偏移**必须**按该默认对齐要求计算
  - **当**字段声明 `aligned(M)` **时**，该字段**必须**按 M 字节对齐，覆盖结构体的默认对齐要求
  - **当** N 为 0 **时**，全部字段默认按 0 字节对齐，仅取消对齐填充，形成紧凑布局
  - **当**目标平台的对齐能力不足以满足 N **时**，编译器**必须**以软件方式模拟
- **当** `aligned(N)` 修饰 `structure` 中的字段**时**：
  - N **必须**为对齐要求
  - **当**目标平台的对齐能力不足以满足 N **时**，编译器**必须**以软件方式模拟
- **当** `aligned(N)` 修饰共同体成员**时**：
  - N **必须**为该成员相对于共同体基础起始点的偏移（见 [共同体](#276-共同体)）
  - 该偏移**不得**按平台对齐能力调整
- `aligned(N)` **必须仅**修饰以下目标：
  - `structure` 声明（见 [结构体](#272-结构体)）
  - `structure` 中的字段（见 [字段](#281-字段)）
  - 共同体成员（见 [共同体](#276-共同体)）

例如：

```novasharp
// 合法：紧凑布局；全部字段默认按 0 字节对齐
aligned(0) structure Compact
{
    public A: integer(1);
    public B: integer(4);
}

// 合法：全部字段默认按 8 字节对齐
aligned(8) structure Aligned
{
    public A: integer(1);
    public B: integer(4);
}

// 合法：字段覆盖结构体的默认对齐
aligned(8) structure Mixed
{
    public A: integer(1);
    public aligned(1) B: integer(1);
}
```

### 8.16 static 修饰符

**static 修饰符**是用于声明与类型关联、但不与实例关联的成员的修饰符，其格式如下：

```ebnf
StaticModifier = "static" .
```

其中：

- **定义** `StaticModifier` 为静态成员修饰符
- **定义** `static` 为其关键字（见 [关键字](#16-关键字)）
- `static` **必须仅**修饰以下目标：
  - `class` 的声明（见 [类](#271-类)）
  - `class` 与 `structure` 中的字段（见 [字段](#281-字段)）
  - `class` 与 `structure` 的扩展块中不含 `this` 参数的常量（见 [常量](#44-常量)）
  - `class` 与 `structure` 的扩展块中的访问器（见 [访问器](#282-访问器)）
- `static` **不得**修饰以下目标：
  - 含 `this` 参数的常量（见 [方法](#74-方法)）
  - 变量（见 [变量](#43-变量)）
  - 接口成员（见 [接口](#273-接口)）
  - `structure`、`interface`、`union`、`variant`、`enumeration`、`module` 的声明

有关成员：

- `static` 成员**不得**进入实例内存布局
- `static` 成员**必须**通过类型标识符经成员访问表达式访问，**不得**通过实例访问（见 [成员访问表达式](#352-成员访问表达式)）
- **当** `static` 修饰泛型类型的成员**时**，该成员**必须**依附于单态化后的类型（见 [泛型参数](#91-泛型参数)）
- **当**静态字段的初值在编译期可确定**时**，其**必须**编入可写段；**否则**由 Launcher 在运行期初始化（见 [启动流程](#132-启动流程)）

有关静态构造函数：

- **定义**静态构造函数为名为 `Construct`、返回值类型为空类型**且**以 `static` 修饰的常量（见 [类](#271-类)）
- 静态构造函数**必须**在主函数（见 [主函数](#131-主函数)）调用前执行

有关静态类：

- 静态类的成员**必须**为 `static` 成员
- 静态类**必须**为全局单例
- **禁止**为静态类创建实例

有关类型级访问器：

- 类型级访问器的成员**必须**为不含 `this` 参数的常量（见 [访问器](#282-访问器)）
- 类型级访问器的 Backing **必须**为同类型的 `static` 字段、全局变量**或**全局常量（见 [访问器](#282-访问器)、[字段](#281-字段)）

> [!NOTE] 静态类与模块的分工
> 模块（见 [模块](#61-模块)）用于标识符整理与内联初始化，不提供初始化钩子。
> 静态类可声明静态构造函数，用于承载任意初始化逻辑。

例如：

```novasharp
// 定义：结构体 Vector2D
structure Vector2D
{
    public X: float(4);
    public Y: float(4);

    extension
    {
        // 合法：静态函数常量，不含 this 参数
        public static constant GetX(v: Vector2D): float(4)
        {
            return v.X;
        }
    }

    // 合法：静态字段
    public static InstanceCount: integer(4) = 0;
}

// 定义：类 Container
// 合法：泛型类型的静态成员
class Container<T>
{
    public static Count: integer(4) = 0;
}

// 定义：静态类 CounterSingleton
// 合法：静态类
static class CounterSingleton
{
    public static Count: integer(4);

    extension
    {
        // 合法：静态构造函数
        public static constant Construct()
        {
            CounterSingleton.Count = 0;
        }
    }
}

// 定义：函数 Main
constant Main(): integer(4)
{
    // 合法：通过类型标识符访问
    variable v: Vector2D;
    variable x: float(4) = Vector2D.GetX(v);
    Container<integer(4)>.Count = 5;
    CounterSingleton.Count = CounterSingleton.Count + 1;

    return 0;
}

// 非法：static 修饰结构体声明
// static structure Bad { }
// 错误：static 必须仅修饰类、字段、不含 this 参数的常量或访问器

// 非法：static 修饰含 this 参数的常量
// class Bad
// {
//     extension
//     {
//         public static constant F: function(this: Bad) { }
//     }
// }
// 错误：static 不得修饰含 this 参数的常量

// 非法：为静态类创建实例
// variable bad: CounterSingleton = CounterSingleton();
// 错误：静态类为全局单例，不得为其创建实例

// 非法：通过实例访问静态成员
// v.GetX(v);
// 错误：不得通过实例访问静态成员
```

## 9. 泛型

### 9.1 泛型参数

**泛型参数**是声明中的类型占位符，用于编译期单态化，其格式如下：

```ebnf
GenericParameters = "<" GenericParameterDefinition { ";" GenericParameterDefinition } ">" .

GenericParameterDefinition = GenericParameter [ ":" Constraint { "," Constraint } ] .

GenericParameter = Identifier .
Constraint       = TypeKind | Identifier .

TypeKind = "class" | "structure" | "interface" | "enumeration" | "variant" | "union" | "basic" .
```

其中：

- **定义** `GenericParameters` 为泛型参数列表
- **定义** `GenericParameterDefinition` 为泛型参数定义
- **定义** `GenericParameter` 为泛型参数名（见 [标识符](#14-标识符)）
  - 泛型参数名**必须**为名称（见 [标识符](#14-标识符)）
- **定义** `Constraint` 为泛型参数约束
- **定义** `Identifier` 为约束目标类型（见 [标识符](#14-标识符)）
- **定义** `TypeKind` 为种类关键字（见 [关键字](#16-关键字)）
- **定义** `basic` 为基本类型种类关键字（见 [基本类型](#22-基本类型)）

有关语法：

- 泛型参数定义之间**必须**以分号 `;` 分隔
- 约束之间**必须**以逗号 `,` 分隔
- 约束聚合**必须**遵循 AND 语义
- 泛型参数**必须**位于名称之后（见 [标识符](#14-标识符)）
- **当**约束为种类关键字**时**，传入类型**必须**属于该种类
- **当**约束为具体类型**时**，传入类型**必须**继承、实现或等于该类型

有关作用域：

- **定义**泛型参数的作用域为声明体
- 泛型参数**必须**在其作用域内可访问
- 泛型参数**必须**为编译期常量
  - 泛型参数**允许**在编译期代码中直接使用（见 [编译期边界](#106-编译期边界)）

有关约束：

- 泛型参数**必须仅**出现在以下种类的名称之后：
  - `constant`（见 [常量](#44-常量)）
  - `class`（见 [类](#271-类)）
  - `structure`（见 [结构体](#272-结构体)）
  - `interface`（见 [接口](#273-接口)）
  - `union`（见 [共同体](#276-共同体)）
  - `variant`（见 [变体](#275-变体)）
  - 编译期函数名（见 [编译期边界](#106-编译期边界)）
  - `extension`（见 [扩展](#283-扩展)）
- `enumeration`（见 [枚举](#274-枚举)）**不得**携带泛型参数
- 字段定义（见 [字段](#281-字段)）**不得**携带泛型参数
- `variable`（见 [变量](#43-变量)）**不得**携带泛型参数
- `allocate`（见 [堆分配](#45-堆分配)）**不得**携带泛型参数
- `operator`（见 [运算符](#3101-运算符)）**不得**携带泛型参数
- `accessor`（见 [访问器](#282-访问器)）**不得**声明泛型参数
  - **允许**访问器借用其外层声明的泛型参数

有关单态化：

- 泛型单态化**必须**在编译期执行
- 单态化的单位**必须为**携带泛型参数的声明
- 单态化**必须**经单态化表达式发起（见 [单态化表达式](#92-单态化表达式)）
- **若**单态化失败，**则**编译器**必须**报错

例如：

```novasharp
// 定义：结构体 Box
// 合法：带约束的泛型结构体
structure Box<T: structure>
{
    public Value: T;
}

// 定义：结构体 Pair
// 合法：多参数泛型
structure Pair<T: class; U>
{
    public First: T;
    public Second: U;
}

// 假设：有接口 IComparable
// 定义：结构体 SortedList
// 合法：多约束泛型参数
structure SortedList<T: class, IComparable>
{
    public Value: T;
}

// 定义：结构体 BasicBox
// 合法：基本类型种类约束
structure BasicBox<T: basic>
{
    public Value: T;
}

// 定义：函数常量 Echo
// 合法：泛型函数常量
constant Echo<T>(value: T): T
{
    return value;
}

// 合法：编译期单态化
variable x: integer(4) = Echo<integer(4)>(42);

// 非法：字段携带泛型参数
// structure Bad
// {
//     public Value<T>: T;
// }
// 错误：字段不得携带泛型参数

// 非法：约束不满足
// structure Bad<T: class>
// {
//     public Value: T;
// }
// variable bad: Bad<integer(4)>;
// 错误：integer(4) 不属于 class 种类
```

### 9.2 单态化表达式

**单态化表达式**是对泛型标识符进行单态化的表达式，其语法如下：

```ebnf
MonomorphizationExpression = ( Identifier | Expression ) "<" [ Type ] { ";" [ Type ] } ">" .
```

其中：

- **定义** `MonomorphizationExpression` 为单态化表达式
- **定义** `Identifier` 为被单态化的标识符（见 [标识符](#14-标识符)）
- **定义** `Expression` 为被单态化的表达式（见 [表达式](#31-表达式)）
- **定义** `Type` 为泛型实参（见 [类型构造语法](#21-类型构造语法)）
  - 泛型实参之间**必须**以分号 `;` 分隔（见 [泛型参数](#91-泛型参数)）
  - 泛型实参**允许**留空；留空表示空类型（见 [类型构造器](#261-类型构造器)）

有关类型：

- 被单态化的标识符**必须**携带泛型参数（见 [泛型参数](#91-泛型参数)）
- 泛型实参的数量**必须**与被单态化的标识符的泛型参数数量相等
- 泛型实参**必须**满足对应泛型参数的约束（见 [泛型参数](#91-泛型参数)）

有关行为：

- 单态化**必须**在编译期执行（见 [泛型参数](#91-泛型参数)）
- **若**单态化失败，**则**编译器**必须**报错

有关返回值：

- 单态化表达式的返回值是被单态化的标识符的单态化结果
- 单态化结果的种类**必须**与被单态化的标识符的种类相同

有关单态化实例的体积优化，见 [体积优化](#1332-体积优化)。

## 10. 编译期

### 10.1 编译期执行

**编译期执行**是以 `#` 为前缀、由编译器求值的执行形式。

`#` 后**仅允许**以下两种形式：

- `#(Expression)`：编译期表达式（见 [编译期表达式](#103-编译期表达式)）
- `#{ Block }`：编译期块（见 [编译期块](#104-编译期块)）

有关 `#`：

- `#` 与 `(` **或** `{` 之间**不得**存在空白
- `#` **不得**用作类型前缀
- `#[]` 不属于本语言形式

有关编译期常量：

- 编译期常量参数的语法与规则，见 [编译期常量参数](#105-编译期常量参数)
- 编译期常量、变量与运行时边界的规则，见 [编译期边界](#106-编译期边界)
- 多文件编译时的执行顺序，见 [编译期执行顺序](#102-编译期执行顺序)

### 10.2 编译期执行顺序

**编译期执行顺序**是多文件编译时顶层编译期代码与函数体编译期代码的执行次序。

有关全量解析：

- 所有源文件**必须**作为同一次编译的输入
- 类型、函数、常量以及导入**必须**在该次编译中全部可见
- `import` **不得**改变执行顺序；其**仅**影响名称解析
- 顶层 `#{}` **必须**在全部声明完成名称解析后执行

有关顶层执行：

- 文件顺序**允许**由构建输入给定
- **当**构建输入未给定文件顺序**时**，编译器**必须**采用固定顺序，例如按路径排序
- 每个文件内**必须**按源代码出现顺序执行
- 文件顶层与模块顶层的 `#{}` **必须**各执行一次
- 多个顶层 `#{}` **必须**按文件顺序与源码顺序依次执行

有关内嵌编译期表达式：

- 顶层定义初值中的 `#()` **必须**参与顶层执行顺序
- 顶层 `#()` **必须**在全部声明完成名称解析后执行
- 同一文件内，顶层 `#()` **必须**与顶层 `#{}` 按源码出现顺序执行
- 跨文件时，顶层 `#()` **必须**按文件顺序执行
- 后续顶层 `#()` **允许**读取前面执行产生的编译期变量
- 前面的顶层 `#()` **不得**依赖后面尚未执行的初始化

有关跨文件初始化：

- 后续顶层 `#{}` **允许**读取前面顶层 `#{}` 产生的编译期变量
- 前面的顶层 `#{}` **不得**依赖后面尚未执行的初始化
- 所有文件中的声明**允许**被任意顶层 `#{}` 引用

有关函数体执行：

- 函数声明**不得**触发函数体 `#{}` 与 `#()` 的执行
- 函数体中的 `#{}` 与 `#()` **必须**在其所属函数体被编译时执行
- **当**函数按编译期常量实参单态化**时**，每个实例的 `#{}` 与 `#()` **必须**分别执行
- 运行期调用**不得**触发 `#{}` 或 `#()` 的求值
- 顶层 `#{}` 调用函数**时**，函数体执行**必须**发生在该函数体编译时

有关残留：

- 顶层与函数体 `#{}` 的终产物**必须**保留到运行时（见 [编译期边界](#106-编译期边界)）
- 运行时**不得**重放编译期执行顺序
- 运行时**不得**访问编译期绑定

例如：

```novasharp
// File A.ns
#{
    variable Base: integer(4) = 1;
}

// File B.ns
#{
    variable Derived: integer(4) = Base + 1;
}
```

按 `A.ns`、`B.ns` 的文件顺序执行时，`Base` 先于 `Derived` 初始化。

### 10.3 编译期表达式

**编译期表达式**是在编译期求值、并把最终结果保留到运行时的表达式，其格式如下：

```ebnf
CompileTimeExpression = "#" "(" Expression ")" .
```

其中：

- **定义** `CompileTimeExpression` 为编译期表达式
- **定义** `Expression` 为被求值的表达式（见 [表达式](#31-表达式)）
- `#` 与 `(` 之间**不得**存在空白

有关求值：

- `Expression` **必须**在编译期确定
- **当** `Expression` 无法在编译期确定**时**，编译器**必须**报错
- `CompileTimeExpression` 的最终结果**必须**保留到运行时

有关结果：

- 最终结果的类型**必须**为运行期类型
- **当**最终结果为编译期定义的类型**时**，编译器**必须**报错
- **当**最终结果为 `linkable` 函数**时**，编译器**必须**报错
- **当**最终结果为普通编译期函数**时**，该函数值**允许**进入运行时

有关边界：

- 编译期常量、变量与运行时的过界规则，见 [编译期边界](#106-编译期边界)
- 编译期执行的副作用规则，见 [编译期边界](#106-编译期边界)

例如：

```novasharp
// 合法：编译期求值，结果保留到运行时
variable size: unsigned integer(8) = #(Type.SizeOf<Vector3>());

// 假设：CompileTimeHandler 为普通编译期函数
// 合法：编译期函数值进入运行时
variable handler(): integer(4) = #(CompileTimeHandler);

// 非法：最终结果为 linkable 函数
// variable bad(): unsigned integer(8) = #(Type.SizeOf<Vector3>);
```

### 10.4 编译期块

**编译期块**是在编译期执行代码、并把被需要的终产物保留到运行时的代码块，其格式如下：

```ebnf
CompileTimeBlock = "#" Block .
```

其中：

- **定义** `CompileTimeBlock` 为编译期块
- **定义** `Block` 为被执行的代码块（见 [代码块](#42-代码块)）
- `#` 与 `{` 之间**不得**存在空白

有关执行：

- `#{ Block }` **必须**在编译期执行
- 块内语句**必须**按普通控制流顺序执行
- 多个顶层 `#{}` 的执行顺序，见 [编译期执行顺序](#102-编译期执行顺序)

有关作用域：

- `#{}` **不得**构成作用域
- 其中的声明**必须**属于外层编译期作用域
- 其中的 `import` **必须**在外层编译期作用域生效（见 [导入](#62-导入)）
- 编译期变量**仅允许**在编译期赋值；运行期只保留其最终值（见 [编译期边界](#106-编译期边界)）

有关位置：

- `#{}` **允许**直接出现在文件顶层，不要求外层代码块
- `#{}` **允许**出现在模块体与函数体中
- **当** `#{}` 位于顶层**时**，其中**不得**出现 `return`
- `#{}` 中的 `return`、`break` 以及 `continue` **必须**绑定外层函数或循环

有关控制流：

- **当**执行遇到不完整控制流**时**，该控制流**必须**以最简形式保留到运行时
- **当**无法保留**时**，编译器**必须**报错

有关终产物：

- 被运行期需要的终产物**必须**保留到运行时
- **当**终产物为编译期定义的类型**时**，编译器**必须**报错
- **当**终产物为 `linkable` 函数值**时**，编译器**必须**报错
- 普通编译期函数值**允许**保留到运行时

有关副作用：

- 编译期执行**允许**副作用
- 副作用**不得**进入运行时的终产物，**且**编译器**必须**报 Warning
- 编译期分配单位的处理，见 [编译期边界](#106-编译期边界)

例如：

```novasharp
#{
    variable X: integer(4) = 1;
    X = 2;
}

// 合法：X 的最终值以运行时常量形式保留
variable value: integer(4) = X;

// 非法：运行期不得修改编译期变量
// X = 3;
```

### 10.5 编译期常量参数

**编译期常量参数**是以 `#` 标记、要求调用方传入编译期常量的函数参数。

其写法为：

- 有名：`#Name: Type`
- 无名：`#Type`

有关语法：

- `#` **必须**位于参数名**或**参数类型之前
- **当**参数名存在**时**，`#` **必须**位于参数名之前
- **当**参数名省略**时**，`#` **必须**位于类型之前
- `#` **不是**参数名的一部分，也不是类型的一部分
- `this` 参数**不得**携带 `#`
- 参数类型、`&` 与默认值的规则，见 [参数](#72-参数)

有关调用：

- 调用方传入的实参**必须**为编译期常量（见 [编译期边界](#106-编译期边界)）
- **当**实参不是编译期常量**时**，编译器**必须**报错

有关类型：

- `#` 约定**必须**参与函数类型相等（见 [函数类型构造器](#264-函数类型构造器)）
- `#` 约定**必须**参与重载签名（见 [重载决议](#75-重载决议)）

有关单态化：

- 函数**必须**按每个编译期常量实参单态化
- 多个编译期常量参数**必须**按实参组合分别单态化
- 单态化版本的合并**必须**遵守 [编译优化总则](#1331-编译优化总则)

有关函数体：

- 编译期常量参数在函数体内是编译期绑定
- 运行期**不得**访问该绑定
- 编译期块**允许**引用该参数（见 [编译期块](#104-编译期块)）
- 泛型参数恒为编译期常量（见 [泛型参数](#91-泛型参数)）

例如：

```novasharp
// 定义：函数 Apply
constant Apply(#value: integer(4)): integer(4)
{
    #{
        return value + 1;
    }
}

// 合法：实参为编译期常量
variable result: integer(4) = Apply(1);

// 非法：实参不是编译期常量
// variable bad: integer(4) = Apply(RuntimeValue());
```

函数类型中可写作：

```novasharp
function(#integer(4), #integer(4))
```

### 10.6 编译期边界

**编译期边界**是编译期与运行时之间值、定义与副作用的可见性边界。

有关编译期常量：

**定义**编译期常量为值在编译期确定的标识符或表达式。

编译期常量**必须**来自以下之一：

- 字面量
- 泛型参数（见 [泛型参数](#91-泛型参数)）
- 编译期常量参数（见 [编译期常量参数](#105-编译期常量参数)）
- `#{}` 中产生的值（见 [编译期块](#104-编译期块)）
- 初始化可在编译期求值的常量（见 [常量](#44-常量)）

普通 `variable` **不得**作为编译期常量。

有关编译期变量：

- `#{}` 中声明的 `variable` **必须**为编译期变量
- 编译期变量**仅允许**在编译期赋值
- 编译期变量的最终值**允许**以运行时常量形式保留到运行时
- 运行期**不得**赋值编译期变量

有关运行时到编译期：

- 编译器**允许**读取运行时定义
- 编译期代码引用运行期标识符**时**，该标识符**必须**为编译期常量
- **当**引用不是编译期常量**时**，编译器**必须**报错

有关编译期到运行时：

- 运行期类型的值**允许**进入运行时
- 编译期变量的最终值**允许**以运行时常量形式进入运行时
- 普通编译期函数值**允许**进入运行时
- 编译期定义的类型**不得**进入运行时
- `linkable` 函数值**不得**进入运行时

**定义**编译期函数为编译期代码空间中的函数。

- 编译期函数包括普通编译期函数和 `linkable` 函数
- 普通编译期函数**允许**作为值进入运行时
- `linkable` 函数**不得**作为值进入运行时，**但**其返回值**允许**进入运行时

有关副作用：

- 编译期执行**允许**副作用
- 副作用**不得**进入运行时的终产物
- **当**编译期执行产生副作用**时**，编译器**必须**报 Warning

有关分配：

- 编译期执行中的分配单位**必须**在编译期执行结束时释放
- 编译期执行中的分配单位**不得**进入运行时
- NOLAA **不得**管辖编译期执行中的分配单位（见 [NOLAA](#112-nolaa)）

有关体积优化：

- 编译期残留的体积清理，见 [编译优化总则](#1331-编译优化总则)

有关编译器 API：

- 编译器 API 的函数**必须**为 `linkable` 函数
- 编译器 API 的函数值**不得**进入运行时
- `Type`、`Compiler`、`NOLAA` **必须**为编译期代码空间中的命名空间
- `Type.SizeOf<T>()` **必须**返回 `T` 的内存大小
- `Type` 的返回值**允许**进入运行时
- `Compiler` 与 `NOLAA` 的返回值类型**必须**为空类型
- `NOLAA` 的函数参数**必须**指向 NOLAA 可追踪的堆对象

有关概念，见 [编译器 API](#107-编译器-api)；有关完整定义，见 [Compile-Time Library 完整内容](#153-compile-time-library-完整内容)。

例如：

```novasharp
#{
    variable X: integer(4) = 1;
    X = 2;
}

// 合法：X 的最终值成为运行时常量
variable value: integer(4) = X;

// 非法：运行期不能修改编译期变量
// X = 3;

// 非法：编译期定义的类型不能进入运行时
// variable bad: CompileTimeType;
```

### 10.7 编译器 API

**编译器 API**是编译器在编译期代码空间中提供的 `linkable` 函数集合。

有关其完整签名与内容，见 [Compile-Time Library 完整内容](#153-compile-time-library-完整内容)。

## 11. 内存模型

### 11.1 内存分配

**内存分配**是为实例取得内存空间的行为。由以下存储期组成：

| 存储期       | 发起方式                                     | 生存期                      |
| ------------ | -------------------------------------------- | --------------------------- |
| 作用域存储期 | `variable`（见 [变量](#43-变量)）            | 由当前作用域决定            |
| 自动堆存储期 | `allocate`（见 [堆分配](#45-堆分配)）        | 由 [NOLAA](#112-nolaa) 决定 |
| 手动堆存储期 | `allocate manual`（见 [堆分配](#45-堆分配)） | 由开发者决定                |

其中：

- **定义**内存分配为：为实例取得内存空间的行为
- **定义**存储期为实例所占内存空间自分配到释放的时长
- 内存分配方式**必须仅**由标识符定义指定
- 内存分配**不得**成为表达式的组成部分
- 内存分配**不得**出现在类型中
- NovaSharp **不得**为任何类型指定默认内存分配方式

有关类型：

- 内存分配方式**必须**与类型无关
- 值类型（见 [值类型](#23-值类型)）和引用类型（见 [引用类型](#24-引用类型)）**必须**均可使用上表的任一存储期
- **当**标识符的类型为引用类型**时**，标识符**必须**存储指向该存储的引用

有关构造：

- **当**实例的类型声明了构造函数**时**，实例**必须**经构造表达式构造（见 [构造表达式](#37-构造表达式)）
- **当**实例的类型为变体**或**共同体**时**，实例**必须**经成员构造表达式构造（见 [成员构造表达式](#38-成员构造表达式)）
- 上述两种构造**不得**指定内存分配方式
- **当**上述两种构造位于定义或赋值的右侧**时**，实例**必须**被构造到该定义或赋值的目标存储中

有关失败：

- 内存分配失败**必须**产生 `AllocateFailedException` 运行时异常（见 [异常处理](#491-异常处理)）

有关值：

- 所有未被标识符定义绑定的值**必须**由编译器分配存储
  - 上述分配**不得**产生危险行为
  - 上述分配的生存期**必须**尽量短

有关未初始化存储：

- **定义**未初始化存储为尚未被写入的存储（见 [变量](#43-变量)、[字段](#281-字段)、[堆分配](#45-堆分配)）
- 可能在赋值之前被读取的存储**必须**支持以 `uninitialized` 作为初始值（见 [未初始化](#1713-未初始化)）
- 未以 `uninitialized` 作为初始值的存储**仅允许**在被赋值之后被读取
- 读取未初始化存储**必须**得到未初始化值（见 [未初始化](#1713-未初始化)）
- 编译器**不得**假定未初始化存储的值
- **当**未初始化存储的类型为函数类型，**且**在该存储被赋值之前被调用**时**，编译器**必须**予以 Warning
- **当**未初始化存储的类型为指针类型（见 [指针类型构造器](#263-指针类型构造器)），**且**在该存储被赋值之前被解引用**时**，编译器**必须**予以 Warning
- **当**未初始化存储的类型为引用类型（见 [引用类型](#24-引用类型)），**且**在该存储被赋值之前被用于成员访问**时**，编译器**必须**予以 Warning

有关逃逸：

- 作用域存储期的实例的引用**不得**逃出该实例的作用域，**但**以下情况除外：
  - 上述引用为返回值，**且**该实例已被构造到调用方提供的存储中（见 [return 语句](#492-return-语句)）
- 逃逸路径由以下组成：
  - 返回值（见 [return 语句](#492-return-语句)）
  - 写入全局存储**或**堆存储（见 [堆分配](#45-堆分配)）
  - 被函数字面量捕获（见 [函数](#1710-函数)）
  - 被 `throw`（见 [throw 语句](#493-throw-语句)）

有关释放：

- 作用域存储期的实例**必须**在作用域结束时释放
- 自动堆存储期的实例**必须**由对象生命周期分析算法判定释放（见 [NOLAA](#112-nolaa)）
- 手动堆存储期的实例**不得**由对象生命周期分析算法管辖（见 [NOLAA](#112-nolaa)）
- 对象生命周期分析算法的插入**必须**经 dispose 语句完成（见 [dispose 语句](#47-dispose-语句)）
- **允许**自动堆存储期和手动堆存储期的实例以 dispose 语句显式释放（见 [dispose 语句](#47-dispose-语句)）
- 作用域存储期的实例**不得**以 dispose 语句释放（见 [dispose 语句](#47-dispose-语句)）

例如：

```novasharp
// 定义：类 Cat
class Cat
{
    public Legs: integer(4);
}

// 定义：函数 Main
constant Main(): integer(4)
{
    // 合法：作用域存储期
    variable cat: Cat = Cat();

    // 合法：自动堆存储期
    allocate heapCat: Cat = Cat();

    // 合法：手动堆存储期
    allocate manual rawCat: Cat = Cat();

    return 0;
}
```

### 11.2 NOLAA

**NOLAA**是分析堆分配单位生命周期的编译期工具。由以下职责组成：

| 职责                | 对象                 | 结果           |
| ------------------- | -------------------- | -------------- |
| Double-Dispose 检查 | 全部堆分配单位       | Warning        |
| Early-Dispose 检查  | 全部堆分配单位       | Warning        |
| Never-Disposed 检查 | 非 `manual` 分配单位 | Warning        |
| 插入 dispose        | 非 `manual` 分配单位 | 在其安全点插入 |

其中：

- **定义** NOLAA 为编译期的堆分配单位生命周期分析工具
- **定义**分配单位为一次 `allocate` 取得的堆存储（见 [堆分配](#45-堆分配)）
- **定义**别名为指向同一分配单位的另一标识符（见 [引用类型](#24-引用类型)）
- **定义**需求者为需要分配单位存在的程序点**或**标识符
  - 上述标识符包含别名
- **定义**存在性需求为需求者需要分配单位存在这一事实
- **定义**安全点为从该节点出发，沿**所有**控制流路径都不会再出现需求者的节点
- **定义** Dispose 点为插入 dispose 的位置
- NOLAA **必须**在编译期执行
- NOLAA 的分析范围**必须**为整个程序，**不得**限定于某一作用域**或**函数
- NOLAA **不得**管辖 `allocate manual` 定义的分配单位
- NOLAA **不得**管辖作用域存储期的实例（见 [变量](#43-变量)）
- NOLAA **不得**管辖编译期执行中的分配单位（见 [编译期边界](#106-编译期边界)）

有关插入：

- NOLAA **必须**为不带 `manual` 的分配单位寻找其安全点，**并**在该点插入 dispose（见 [dispose 语句](#47-dispose-语句)）
- NOLAA **必须**保守：**当**无法断言某节点为安全点**时**，**必须**不插入 dispose
- **禁止** NOLAA 在非安全点插入 dispose
- **当**分配单位不存在安全点**时**， NOLAA **必须**不插入 dispose
- **当**分配单位不存在可访问的标识符**时**， NOLAA **必须**不插入 dispose（见 [dispose 语句](#47-dispose-语句)）
- **当**分配单位已存在显式 dispose **时**， NOLAA **必须**不插入 dispose

有关外部调用：

- **定义**放弃为 NOLAA 停止对某分配单位的安全点推理的行为
- 分析到 linkable 函数的调用**时**，NOLAA **必须**放弃（见 [linkable 修饰符](#810-linkable-修饰符)）
  - 上述放弃**必须**不插入 dispose
  - **当**上述放弃发生**时**，该分配单位为 Never-Disposed

有关 API：

- `NOLAA.Abandon(x)` **必须**停止对 `x` 所指堆对象的分析
  - `Abandon` 后**不得**为该对象插入 dispose
  - `Abandon` 后**不得**产生 Never-Disposed Warning
- `NOLAA.Bind(required, requiredBy)` **必须**在 `requiredBy` 与 `required` 所指堆对象之间增加存在性需求
  - `requiredBy` 存在期间，`required` **不得**被释放
  - 上述需求**必须**参与强连通分量判定
- `NOLAA.AssumeNoDemandNext(x)` **必须**仅作用于紧随其后的一个语句
  - 该语句**不得**对 `x` 所指堆对象产生新的存在性需求
  - **当**该语句为 linkable 调用**时**，NOLAA **不得**因该调用放弃分析
  - 该语句之后**必须**恢复正常分析
- `NOLAA` API 的参数**必须**指向 NOLAA 可追踪的堆对象
  - **当**参数不是可追踪堆对象**时**，编译器**必须**报错

有关检查：

- NOLAA **必须**检查 Double-Dispose，**并**发出 Warning
  - **定义** Double-Dispose 为同一分配单位被销毁两次
- NOLAA **必须**检查 Early-Dispose，**并**发出 Warning
  - **定义** Early-Dispose 为分配单位在非安全点被销毁
    - **定义** Use-After-Dispose 为分配单位在被销毁后仍存在需求者的情形，该情形为 Early-Dispose
- NOLAA **必须**检查 Never-Disposed，**并**发出 Warning
  - **定义** Never-Disposed 为从未被销毁的分配单位
  - **当**分配单位已被 `NOLAA.Abandon` **时**，本检查**不得**适用
- 上述 Warning **不得**阻止编译
- 上述 Warning **必须**指明分配单位的标识符和所在程序位置

有关循环引用：

- NOLAA **必须**将相互需要的分配单位判定为一个分析单位
  - 相互需要的分配单位是需求图的强连通分量
- 同一分析单位的成员**必须**在同一安全点被释放

有关析构：

- 插入的 dispose **必须**触发其目标的析构函数（见 [类](#271-类)、[结构体](#272-结构体)）
- 析构函数**不得**依赖析构发生的精确时刻

例如：

```novasharp
// 定义：类 Token
class Token
{
    public Value: integer(4);
}

// 定义：变量 Global
variable Global: Token;

// 定义：函数 Main
constant Main(): integer(4)
{
    // 合法：NOLAA 在 token 的最后一次使用之后插入 dispose
    allocate token: Token = Token();
    token.Value = 1;

    // 不推荐：需求经字段写入延续，此处销毁早于安全点
    // NOLAA 将发出 Early-Dispose Warning
    allocate shared: Token = Token();
    Global = shared;
    dispose shared;

    return 0;
}

// 危险：同一分配单位被销毁两次，NOLAA 将发出 Double-Dispose Warning
// allocate duplicated: Token = Token();
// dispose duplicated;
// dispose duplicated;
```

## 12. ABI

### 12.1 NovaSharp ABI

**NovaSharp ABI**是 NovaSharp 编译产物在二进制层面互相调用的接口约定。

有关组成：

- **定义** NovaSharp ABI 由调用约定、内存布局和名称修饰组成
- 有关调用约定，见 [Built-In Library 完整内容](#152-built-in-library-完整内容)
- 有关基本类型，见 [基本类型](#22-基本类型)、[指针类型构造器](#263-指针类型构造器)
- 有关内存布局，见 [结构体](#272-结构体)、[类](#271-类)、[共同体](#276-共同体)、[变体](#275-变体)、[枚举](#274-枚举)、[字段](#281-字段)、[数组类型构造器](#262-数组类型构造器)
- 有关对齐，见 [aligned(N) 修饰符](#815-alignedn-修饰符)
- 有关名称修饰，见 [名称修饰](#122-名称修饰)
- 有关外部符号名，见 [linkable 修饰符](#810-linkable-修饰符)
- 有关体积优化，见 [体积优化](#1332-体积优化)

### 12.2 名称修饰

**名称修饰**是把 NovaSharp 名字编码为二进制符号名的规则。

有关组成：

- **定义**符号名由以下成分按固定顺序组成：作用域路径、声明名、参数类型列表的哈希
  - 方法的 `this` 类型**必须**计入参数类型列表的首位（见 [方法](#74-方法)）
  - 泛型实参**必须**以单态化后的类型计入（见 [单态化表达式](#92-单态化表达式)）
- 符号名**不得**含返回值类型
- 符号名**不得**含调用约定
- 符号名的成分**不得**含空白字符；**当**类型的书写可含空白**时**，**必须**略去
- 符号名**必须**由上述三个成分唯一决定

有关形式：

- 符号名**必须**写为 `N`，后接作用域路径的编码，后接声明名的编码，后接哈希
- 作用域路径与声明名**必须**各写为「十进制长度 + 转义文本」
  - 转义文本**仅**含 `A-Za-z0-9`
  - 其它字符**必须**写为 `_` 加两位十六进制小写数字
  - `_` **必须**写为 `_5f`
  - 长度为转义文本的字节数
- 哈希**必须**为 FNV-1a 64 位，写作 16 位十六进制小写数字
  - 其偏移基为 `0xcbf29ce484222325`，质数为 `0x100000001b3`
  - 其输入为每个参数类型的编码依次相接的字节序列
  - 每个参数类型的编码为「十进制长度 + 转义文本」，转义规则同上
- 各成分**必须**依次相接，**不得**插入其它分隔符
- 不同参数类型列表的哈希**允许**相同，**但\*\***必须\*\*为小概率事件

> [!NOTE] 算例如下
> 作用域路径 `Main`、声明名 `Compute`、参数类型列表 `integer(4)` 的符号名为 `N4Main7Compute2bf5d948506c5341`。

有关外部符号：

- **当**函数常量携带 `linkable`**时**，符号名**必须**取该修饰符暴露的符号名（见 [linkable 修饰符](#810-linkable-修饰符)）
- **当** `linkable` 省略参数**时**，符号名**必须**为常量名（见 [标识符](#14-标识符)）
- **当** `linkable` 携带字符串参数**时**，符号名**必须**为该字符串的内容

## 13. 程序

### 13.1 主函数

**主函数**是程序启动时被调用的函数常量。

其中：

- **定义**主函数为名为 `Main` 的函数常量（见 [常量](#44-常量)）
  - 一个可执行产物**必须**恰有一个主函数

有关调用：

- 主函数**必须仅**由 Launcher 调用（见 [启动流程](#132-启动流程)）
- 主函数的返回值类型**允许**省略（见 [启动流程](#132-启动流程)）

例如：

```novasharp
// 合法：返回值类型为 integer(4)，由 Launcher 原样交给入口点
constant Main(): integer(4)
{
    return 0;
}

// 合法：以平台实参为参数，由被调用方自行解释
constant Main(handle: pointer, table: pointer): integer(4)
{
    return 0;
}

// 合法：返回值为空类型，入口点不传递任何值
constant Main()
{
    return;
}

// 非法：一个可执行产物存在两个主函数
// constant Main: function() integer(4) { return 1; }
// 错误：一个可执行产物必须恰有一个主函数
```

### 13.2 启动流程

**启动流程**是程序从入口点开始、直到终止的执行次序。

其中：

- **定义**启动流程为程序从入口点开始、直到终止的执行次序
- **定义**入口点为与语言标准无关、由构建与链接选定的符号
- **定义** Launcher 为由编译器生成**且**由入口点调用的函数
- **定义**编译期初值为编译器可在编译期求值的初值（见 [编译期执行](#101-编译期执行)）
- **定义**运行期初始化为模块级或静态存储中初值在编译期不可确定的初始化

有关次序：

1. 入口点调用 Launcher
2. Launcher **执行**全部静态构造函数（见 [static 修饰符](#816-static-修饰符)）与全部运行期初始化，使程序进入已初始化状态
3. Launcher 调用主函数（见 [主函数](#131-主函数)）
4. **当**主函数的返回值类型不为空类型**时**，Launcher **必须**将返回值原样交给入口点，入口点以该返回值终止程序
   - **当**主函数的返回值类型为空类型**时**，Launcher **不得**传递返回值

有关段：

- **当**模块级或静态存储的初值在编译期可确定**时**，编译器**必须**将其编入可执行文件的映像
  - 非函数常量的初值**必须**编入只读段
  - 变量与静态字段的初值**必须**编入可写段
  - 上述初值**必须**在入口点被调用前生效
- **当**模块级或静态存储的初值在编译期不可确定**时**，其**必须**由 Launcher 在运行期初始化
- 常量的运行期初始化完成后，其存储**不得**再被写入

有关初始状态：

- 入口点的初始状态由构建与链接提供，**且\*\***必须\*\*与目标平台一致
- Launcher **必须**保证其调用的每一个函数的初始状态与入口点被调用时的初始状态相同
  - 该状态**必须**以实参值的形式复现
- 被调用方如何解释该状态**必须**由其自身决定

有关初始化：

- 静态构造函数**必须**在全部用户代码执行前完成
- 运行期初始化**必须**在全部用户代码执行前完成
- 上述初始化之间的执行顺序**必须**由编译器确定
  - 同一程序的顺序**必须**保持一致
- 编译器**必须**优化上述执行顺序，使全部可确定的依赖关系得到满足，即被依赖的初始化**必须**先于依赖方
- **当**可确定的依赖关系成环**时**，编译器**必须**报错

有关职责划分：

- 入口点的选择**必须**由构建与链接承担
- 入口点的初始状态**必须**由构建与链接保证与目标平台一致
- Launcher 的生成**必须**由编译器承担
- 返回值向入口点的传递**必须**由 Launcher 承担

> [!NOTE] 入口点位于语言边界之外
> 入口点由语言之外调用，其初始状态由构建与链接保证与目标平台一致。
> 程序如何解释该状态，由其自身决定。

例如：

```novasharp
// 定义：函数 Main
constant Main(): integer(4)
{
    return 0;
}

// 启动流程：
// 1. 入口点调用 Launcher
// 2. Launcher 执行全部静态构造函数与运行期初始化
// 3. Launcher 调用 Main，取得返回值 0
// 4. Launcher 将 0 原样交给入口点，入口点以此终止程序

// 非法：初始化之间的依赖关系成环，无法确定顺序
// module A { variable X: integer(4) = B.Y; }
// module B { variable Y: integer(4) = A.X; }
// 错误：初始化之间的依赖关系成环
```

### 13.3 编译优化

#### 13.3.1 编译优化总则

**编译优化总则**是体积优化与速率优化共同遵守的约束。

有关共同约束：

- 优化**不得**改变语法
- 优化**不得**改变结构体的字段顺序、大小、偏移**或**对齐
- 优化**不得**改变可观察行为
- 优化**不得**破坏 `linkable` 符号、外部可见 ABI**或**必需元数据
- 优化**允许**以全程序编译为前提

有关体积专项，见 [体积优化](#1332-体积优化)。

有关速率专项，见 [速率优化](#1333-速率优化)。

有关全程序死代码消除：

- 编译器**允许**删除运行期不可达的声明、成员、泛型实例、接口实现与 Built-In 定义
- 编译器**必须**保留 `linkable` 导出符号
- 编译器**必须**保留异常拦截、类型判定与接口转换所需的元数据

有关单态化去重与相同代码合并：

- 编译器**允许**合并机器码相同的泛型实例与编译期实例
- 编译器**允许**合并机器码相同的函数体
- 编译器**必须**保留每个泛型实例的类型身份与静态字段
- 编译器**不得**合并 `linkable` 导出符号对应的函数地址

有关元数据最小化：

- 编译器**允许**删除运行时不需要的类型名
- 编译器**允许**合并相同的类型描述符与接口表
- 编译器**允许**删除未使用的虚表槽与接口表项
- 编译器**必须**保留 `is` 表达式、接口转换与 `trap` 所需的类型信息

有关无捕获函数值：

- 无捕获函数值**允许**表示为函数指针
- 有捕获函数值**允许**共享函数代码，仅保留环境数据
- 编译器**必须**保持参数传递、捕获语义与调用结果

有关全程序去虚化：

- 编译器**允许**将可确定目标的虚调用与接口调用替换为直接调用
- 编译器**允许**删除不再可达的虚表槽与接口表项
- 编译器**必须**保持动态分派结果不变
- 编译器**不得**移除外部可见的 `linkable` 符号

有关编译期残留清理：

- 编译器**允许**在编译期折叠常量表达式
- 编译器**允许**删除未被运行期引用的编译期残留声明
- 编译器**必须**保留运行期需要的终产物

有关表示边界：

- Built-In Library 的语言定义**必须**保留；其未被引用的代码与数据**允许**从产物中省略
- 类实例的类型信息与虚表本体**必须**保留；**仅允许**删除名称、未使用槽位与未使用表项
- 接口表是分派元数据，**不得**视为接口成员的运行时实体
- 函数类型仍为引用类型；函数指针**仅**为内部表示或 ABI 表示
- 索引访问的边界校验规则见 [索引访问表达式](#354-索引访问表达式)；本总则**不得**改变越界语义

有关共同预算：

产物体积：

- 总产物增长**必须**小于 2%
- 对应功能维度增长**必须**小于 5%

运行时成本：

| 指标                         | 显著回归 |
| ---------------------------- | -------- |
| 语料总体运行时间，几何平均   | ≥ 3%     |
| 任一代表性工作负载的运行时间 | ≥ 10%    |
| p95 延迟                     | ≥ 10%    |
| 峰值内存                     | ≥ 5%     |
| 分配次数或分配字节数         | ≥ 10%    |
| 启动时间                     | ≥ 10%    |

共享优化**不得**超过上述预算。体积专项与速率专项**允许**追加更严格的条件。

#### 13.3.2 体积优化

**体积优化**是在 [编译优化总则](#1331-编译优化总则) 约束下缩小产物的专项方案。

有关字面量池化：

- 相同的字符串、数组与常量字面量**允许**共享只读数据
- 编译器**必须**保持值语义；赋值与传参仍按值复制

有关通过条件：

- 语料总体净下降**必须**大于等于 2%
- 对应功能维度净下降**必须**大于等于 10%
- 任一指标**不得**超过 [编译优化总则](#1331-编译优化总则) 的体积与运行时预算

共享优化由 [编译优化总则](#1331-编译优化总则) 定义，不在此页重复。

#### 13.3.3 速率优化

**速率优化**是在 [编译优化总则](#1331-编译优化总则) 约束下提高运行速度的专项方案。

有关 `trap` 快路径：

- 编译器**允许**优化 `trap` 的无异常路径
- 编译器**不得**改变 `catch` 匹配、`finally` 执行**或**未被捕获时的终止行为

有关小函数内联：

- **允许**内联热且小的函数
- 总产物体积增长**必须**小于 2%
- 目标工作负载提速**必须**大于等于 5%
- 任一工作负载回退**必须**小于 3%

有关热路径特化：

- **允许**对类型稳定的热调用点特化
- 总产物体积增长**必须**小于 2%
- 目标工作负载提速**必须**大于等于 5%

有关边界检查：

- 索引访问的边界校验消除**必须**遵循 [索引访问表达式](#354-索引访问表达式)
- 本页**不得**新增改变越界语义的优化

有关不采用：

- 引用类型泛型共享
- 接口表全局化**或**接口胖指针
- 结构体布局调整
- NOLAA 批量释放
- 激进内联**或**循环展开
- 以增加峰值内存换取速度

有关通过条件：

| 指标                   | 要求       |
| ---------------------- | ---------- |
| 总体运行时间，几何平均 | 提速 ≥ 5%  |
| 目标工作负载           | 提速 ≥ 10% |
| 任一代表性工作负载     | 回退 < 3%  |
| p95 延迟               | 回退 < 5%  |
| 峰值内存               | 增加 < 5%  |
| 启动时间               | 回退 < 5%  |

**当**任一条件不满足**时**，该优化**不得**启用。

共享优化由 [编译优化总则](#1331-编译优化总则) 定义，不在此页重复。

## 14. 设计基准

### 14.1 核心设计哲学

**核心设计哲学**是 NovaSharp 语法设计的根本宗旨。

NovaSharp 遵循以下核心哲学：

- **不依赖特定操作系统**：
  - 在调用 `ExitBootService` 后的裸机环境中，全语法功能可用
- **将控制权还给开发者**
  - 编译器**仅**对语法错误与静态语义错误报错
  - **定义**静态语义错误为下列情形之一：
    - 语义不存在、不成立、不明确**或**不唯一
    - 描述的行为无法被实现
  - **判定**问题的处置为静态语义错误，**当且仅当**：编译期可**完整**判定，**且**程序**无**意义
  - **判定**问题的处置为运行期抛出，**当且仅当**：运行期才可**完整**判定，**且**语言规定了失败时的结果
  - **判定**问题的处置为 Warning，**当且仅当**：程序有意义，**但**存在危险**或**隐患，**且**不属于上述两种情形
  - 所有警告及非致命诊断信息**不得**阻止代码生成
  - 无 `unsafe` 关键字
  - 保留“危险的”语法设计，开发者知道自己在做什么
  - 语言**仅**为安全性提供可移除的工具
  - 危险行为**必须**在其引入的书写处有显式记号，**且**该记号**不得**兼作他用
    - 上述记号**不得**由省略**或**默认值取得
    - **当**危险不可由使用者选择**时**，**必须仅**以 Warning 处置
- **基本安全零认知代价**：
  - 基本安全**必须**默认生效，**不得**要求程序员书写记号**或**记忆额外规则
- **显式语义**：
  - 语义中不含有即无对应控制流
  - 保留语义中含有的隐式控制流
- **隐式转换无损**：
  - **定义**同类数据为属于同一类型族**且**字长相同的数据
  - **定义**无损转换为结果可精确还原为源值的转换
  - 隐式转换**必须仅**发生在同类数据之间
  - 隐式转换**必须**为无损转换
  - **允许**经 `implicitable` 授权的转换运算符不受上述两条要求约束（见 [implicitable 修饰符](#88-implicitable-修饰符)）
- **可读性至上**：
  - 语法低缩写、简写

### 14.2 设计原则

**设计原则**是对核心设计哲学（见 [核心设计哲学](#141-核心设计哲学)）的具体落地。

NovaSharp 遵循以下**设计原则**：

- **零语义歧义**：
  - 拒绝出现任何没有处理规定的语义歧义
- **尽可能零成本抽象**：
  - 语法糖在编译期完全擦除
  - 未使用的抽象尽可能不产生运行时开销
- **语法最小化**：
  - **当**语法构造的表达力可由既有构造等价获得**时**，**必须**删除该构造
  - **当**删除该构造会削减表达力**时**，**不得**删除
  - 决策成本、逃逸面和使用场景为上述判定的依据
- **剥离标准库**：
  - NovaSharp 语法**不得**提供标准库
  - 语法**仅**提供 Built-In Library
  - 更多，见 [Built-In Library 设计原则](#143-built-in-library-设计原则)
- **函数是一等公民**：
  - 将函数视作引用类型，由 Lambda 全权创建
- **函数调用方约定和被调用方约定分离**：
  - 函数类型负责为调用行为
  - 函数字面量负责响应调用
  - 双方在类型无关约定（例如参数名）上互不干扰
- **明确语义**：
  - 每一个符号都有其对应的语义
- **分隔符使用**：
  - `,` 用于小型分隔
  - `;` 用于大型分隔
- **无默认内存分配方式**：
  - 内存分配方式与类型无关
- **语法限制维护安全性**：
  - **若**运行时无此限制，**则**NovaSharp 依然**必须**在语法层面要求它
  - 危险行为**必须**显式表达

### 14.3 Built-In Library 设计原则

**Built-In Library 设计原则**是对设计原则（见 [设计原则](#142-设计原则)）在 Built-In Library 的设计上的具体落地。

Built-In Library 是 NovaSharp 编译时强制性附带的附加代码。

Built-In Library 遵循以下**设计原则**：

- **必要基础设施**：
  - 与 NovaSharp 语法互操作的必不可少的内容
- **前瞻式定义**：
  - 为每个 NovaSharp 项目之间高度重合的内容进行同一定义，防止混乱

## 15. 附录

### 15.1 语法速查表

**语法速查表**是 NovaSharp 全部语法点的清单，按类别列出各构造的写法与所在页面。

有关词法：

- NovaSharp 中具有固定语义的保留词（见 [关键字](#16-关键字)）
- `FunctionLiteral = "(" [ LiteralParameters ] [ ";" CallingConventionExpression ] ")" [ Type ] "=>" Block .` — 函数字面量实现被调用方的约定，是创建函数的唯一方式（见 [函数](#1710-函数)）
- `CharacterLiteral = "'" ( Character | EscapeSequence ) "'" [ ":" CharacterEncodingTag ] .` — 将字符映射为无符号整数的字面量表示（见 [字符](#175-字符)）
- `StringLiteral = NormalStringLiteral | VerbatimStringLiteral . …` — 将字符串映射为无符号整数类型数组的字面量表示（见 [字符串](#176-字符串)）
- `Literal = IntegerLiteral …` — 表示常量的语法形式（见 [字面量](#171-字面量)）
- `BooleanLiteral = "true" | "false" .` — 布尔类型的字面量表示（见 [布尔值](#174-布尔值)）
- `ArrayLiteral = "{" [ Element { "," Element } [ "," ] ] "}" . …` — 数组类型的字面量表示（见 [数组](#179-数组)）
- `IntegerLiteral = DecimalLiteral | HexLiteral | BinaryLiteral . …` — 整数类型的字面量表示（见 [整数](#172-整数)）
- `InfiniteLiteral = "infinite" .` — IEEE 754 正无穷大的字面量表示（见 [无穷值](#1711-无穷值)）
- `UninitializedLiteral = "uninitialized" .` — 存储的未初始化表示（见 [未初始化](#1713-未初始化)）
- `FloatLiteral = DecimalLiteral "." DecimalLiteral [ Exponent ] . …` — 浮点类型的字面量表示（见 [浮点数](#173-浮点数)）
- `CharacterEncodingTag = "ascii" …` — 字符和字符串的字符集标注方式（见 [编码与编码标注](#177-编码与编码标注)）
- `EscapeSequence = "\" ( "a" | "b" | "f" | "n" | "r" | "t" | "v" | "\" | '"' | "'" | "0" ) …` — 字符和字符串中表示特殊字符的字符组合（见 [转义序列](#178-转义序列)）
- `IllegalLiteral = "illegal" .` — IEEE 754 非数的字面量表示（见 [非法值](#1712-非法值)）
- `Identifier       = Name | MemberAccessExpression . …` — 开发者自定义内容的名称或成员访问表达式（见 [标识符](#14-标识符)）
- 编译器忽略的代码说明文本（见 [注释](#13-注释)）
- 承载 NovaSharp 代码的文本文件（见 [源代码文本文件](#11-源代码文本文件)）
- 用于分隔 Token 的字符集合（见 [空白与行终止](#12-空白与行终止)）
- NovaSharp 中关键字与符号的语义对照表（见 [语义映射表](#19-语义映射表)）
- 用于分隔语句的字符集合（见 [语句终止](#18-语句终止)）

有关名称：

- 代码中标识符的有效范围边界（见 [作用域](#51-作用域)）
- 标识符对外部作用域的可见程度（见 [可访问性](#52-可访问性)）
- 同一作用域内不得出现同名标识符的约束（见 [标识符唯一性](#53-标识符唯一性)）
- 内层作用域中的标识符使外层作用域同名标识符不可直接访问的机制（见 [遮蔽](#54-遮蔽)）

有关类型：

- 标识符直接持有实例本体的类型，（见 [值类型](#23-值类型)）
- `BasicType = IntegerType …` — NovaSharp 内置的基础数据类型（见 [基本类型](#22-基本类型)）
- 对实例本体的间接访问机制（见 [引用](#25-引用)）
- 标识符存储实例引用的类型，（见 [引用类型](#24-引用类型)）
- `FieldDefinition = { Modifier } Name [ ":" Type ] [ "=" Expression | Block ] .` — 类型声明体中的数据成员（见 [字段](#281-字段)）
- `IdentifierDefinitionShorthand = FunctionShorthand | ArrayShorthand .` — 标识符定义中以参数列表或维度列表替代类型标注的简写（见 [标识符定义简写](#15-标识符定义简写)）
- `FunctionShorthand = Name [ GenericParameters ] "(" [ Parameters | "wildcard" ] [ ";" CallingConventionExpression ] ")" [ ":" Type ] .` — 函数简写（见 [标识符定义简写](#15-标识符定义简写)）
- `ArrayShorthand = Name "[" Expression { "," Expression } "]" [ ":" Type ] .` — 数组简写（见 [标识符定义简写](#15-标识符定义简写)）
- `ExtensionDeclaration = "extension" [ "for" ExtensionTarget ] Block . …` — 为类型追加成员的声明（见 [扩展](#283-扩展)）
- `AccessorDefinition        = { Modifier } "accessor" Name ":" Type [ "=>" Backing ] [ AccessorMembers ] . …` — 封装读写行为的标识符种类（见 [访问器](#282-访问器)）
- `FunctionTypeConstructor = "function" [ "(" [ ParameterList ] [ ";" CallingConventionExpression ] ")" ] . …` — 构造函数类型的语法形式，函数类型是引用类型，用于描述调用方的调用行为（见 [函数类型构造器](#264-函数类型构造器)）
- `PointerTypeConstructor = "pointer" .` — 构造指针类型的语法形式，指针类型是值类型，用于表示对内存地址的引用（见 [指针类型构造器](#263-指针类型构造器)）
- `ArrayTypeConstructor = "array(" Expression { "," Expression } ")" .` — 构造数组类型的语法形式，数组类型是值类型，用于表示固定长度的同类型元素序列（见 [数组类型构造器](#262-数组类型构造器)）
- `ConstructedType = TypeConstructor [ ConstructTargetType ] . …` — 构造复合类型的语法形式，用于将基本类型或已有类型扩展为新类型（见 [类型构造器](#261-类型构造器)）
- `Type = ConstructedType | BasicType | Identifier | MonomorphizationExpression .` — 构造类型的形式（见 [类型构造语法](#21-类型构造语法)）
- `UnionDeclaration = { Modifier } "union" Name [ GenericParameters ] "{" { UnionMemberDeclaration | ExtensionDeclaration } "}" . …` — 值类型，用于以不同方式访问同一块内存，无默认内存分配方式；成员直接声明，可内嵌扩展块（见 [共同体](#276-共同体)）
- `VariantDeclaration = { Modifier } "variant" Name [ GenericParameters ] "{" { VariantMemberDeclaration | ExtensionDeclaration } "}" . …` — 值类型，用于表示不同状态的值，无默认内存分配方式；状态直接声明，可内嵌扩展块（见 [变体](#275-变体)）
- `InterfaceDeclaration = { Modifier } "interface" Name [ GenericParameters ] [ BaseList ] Block .` — 对扩展内容的 API 契约，必须仅被 `class` 实现；成员直接声明，不含扩展块（见 [接口](#273-接口)）
- `EnumerationDeclaration = { Modifier } "enumeration" Name ":" BasicType "{" { EnumerationMemberDeclaration | ExtensionDeclaration } "}" . …` — 值类型，提供标识符与底层类型值的映射；成员直接声明，可内嵌扩展块（见 [枚举](#274-枚举)）
- `ClassDeclaration = { Modifier } "class" Name [ GenericParameters ] [ BaseList ] Block .` — 引用类型，无默认内存分配方式，支持单继承、多接口实现、多态和方法重写；类型体直接包含字段、模块与扩展块（见 [类](#271-类)）
- `StructureDeclaration = { Modifier } "structure" Name [ GenericParameters ] Block .` — 值类型，无默认内存分配方式；类型体直接包含字段、模块与扩展块（见 [结构体](#272-结构体)）
- `BaseList = ":" ( Identifier | MonomorphizationExpression ) { "," ( Identifier | MonomorphizationExpression ) } .` — 被继承或被实现目标的列表（见 [继承列表](#277-继承列表)）

有关表达式：

- `IsExpression = Expression "is" IsTarget . …` — 判定形态的表达式（见 [is 表达式](#39-is-表达式)）
- `ValueExpression = Identifier …` — 表示值的表达式（见 [值表达式](#32-值表达式)）
- `FunctionCallExpression = Expression "(" Arguments ")" .` — 调用函数的表达式（见 [函数调用表达式](#36-函数调用表达式)）
- `MemberConstructionExpression = ConstructedTypeName "." Name "(" Expression ")" .` — 以成员构造宿主实例的表达式（见 [成员构造表达式](#38-成员构造表达式)）
- `ParenthesisExpression = "(" Expression ")" .` — 改变求值优先级的表达式（见 [括号表达式](#33-括号表达式)）
- `ConstructionExpression = ConstructedTypeName "(" Arguments ")" . …` — 构造实例的表达式（见 [构造表达式](#37-构造表达式)）
- `TypeConversionExpression = "Cast" "<" Type ">" "(" Expression ")" .` — 以显式转换将值转换为目标类型的表达式（见 [类型转换表达式](#34-类型转换表达式)）
- `Expression = ValueExpression …` — 一类带有返回值的语法形式，用于计算和求值（见 [表达式](#31-表达式)）
- `MemberAccessExpression = ( Identifier | Expression ) "." Name .` — 获取标识符、类型或实例的成员的表达式（见 [成员访问表达式](#352-成员访问表达式)）
- `PointerMemberAccessExpression = ( Identifier | Expression ) "->" Name .` — 获取标识符或实例所承载指针的目标实例的成员的表达式（见 [指针成员访问表达式](#353-指针成员访问表达式)）
- `IndexAccessExpression = ( Identifier | Expression ) "[" Expression "]" .` — 通过索引获取标识符或实例的内容的表达式（见 [索引访问表达式](#354-索引访问表达式)）
- `AccessExpression = MemberAccessExpression …` — 描述对标识符或实例进行访问的表达式（见 [访问表达式](#351-访问表达式)）
- `NotEqualExpression = Expression "!=" Expression .` — 对判断两个值是否不等的表达式（见 [不等表达式](#31021-不等表达式)）
- `MultiplyExpression = Expression "*" Expression .` — 对两个值进行求积的表达式（见 [乘法表达式](#3109-乘法表达式)）
- `MinusExpression = Expression "-" Expression .` — 对两个值进行求差的表达式（见 [减法表达式](#31013-减法表达式)）
- `AddExpression = Expression "+" Expression .` — 对两个值进行求和的表达式（见 [加法表达式](#31012-加法表达式)）
- `NegateExpression = "-" Expression .` — 对操作数取算术负值的表达式（见 [取负表达式](#3104-取负表达式)）
- `GreaterEqualExpression = Expression ">=" Expression .` — 对判断两个值是否大于等于的表达式（见 [大于等于表达式](#31019-大于等于表达式)）
- `GreaterExpression = Expression ">" Expression .` — 对判断两个值是否大于的表达式（见 [大于表达式](#31017-大于表达式)）
- `LessEqualExpression = Expression "<=" Expression .` — 对判断两个值是否小于等于的表达式（见 [小于等于表达式](#31018-小于等于表达式)）
- `LessExpression = Expression "<" Expression .` — 对判断两个值是否小于的表达式（见 [小于表达式](#31016-小于表达式)）
- `ReferenceExpression = "&" Expression .` — 获取实例地址的表达式（见 [引用表达式](#3107-引用表达式)）
- `BitwiseAndExpression = Expression "&" Expression .` — 对两个值进行按位 AND 操作的表达式（见 [按位与表达式](#31022-按位与表达式)）
- `BitwiseNotExpression = "^" Expression .` — 对一个值进行按位 NOT 操作的表达式（见 [按位取反表达式](#3106-按位取反表达式)）
- `BitwiseXorExpression = Expression "^" Expression .` — 对两个值进行按位 XOR 操作的表达式（见 [按位异或表达式](#31023-按位异或表达式)）
- `BitwiseOrExpression = Expression "|" Expression .` — 对两个值进行按位 OR 操作的表达式（见 [按位或表达式](#31024-按位或表达式)）
- `ConditionalExpression = Expression "?" Expression ":" Expression .` — 根据条件在两个值之间选取的表达式（见 [条件表达式](#31028-条件表达式)）
- `RemainderExpression = Expression "%" Expression .` — 对两个值进行求余的表达式（见 [求余表达式](#31011-求余表达式)）
- `EqualExpression = Expression "==" Expression .` — 对判断两个值是否相等的表达式（见 [相等表达式](#31020-相等表达式)）
- `NullCoalescingExpression = Expression "??" CoalescingAlternative . …` — 以 `??` 对左操作数进行决策，并在决策为 `Alternative` 时执行右侧续体的表达式（见 [空值合并表达式](#31027-空值合并表达式)）
- `DereferenceExpression = "*" Expression .` — 获取指针所指向实例的表达式（见 [解引用表达式](#3108-解引用表达式)）
- `OperatorDefinition = { Modifier } "operator" OperatorHead [ "=" Expression | Block | AccessorMembers ] . …` — 为运算符提供运算行为的标识符种类（见 [运算符](#3101-运算符)）
- `OperatorHead = OperatorShorthand | OperatorNotation [ ":" Type ] . …` — 运算符头部（见 [运算符](#3101-运算符)）
- `OperatorShorthand = OperatorSymbol "(" [ Parameters ] ")" [ ":" Type ] . …` — 运算符简写（见 [运算符](#3101-运算符)）
- 表达式结合次序的规范（见 [运算符优先级](#3102-运算符优先级)）
- 为运算符提供符合自定义类型的运算行为的机制（见 [运算符重载](#3103-运算符重载)）
- `LogicalRightShiftExpression = Expression ">>" Expression .` — 对两个值进行逻辑右移操作的表达式（见 [逻辑右移表达式](#31015-逻辑右移表达式)）
- `LogicalAndExpression = Expression "&&" Expression .` — 对两个布尔值进行 AND 操作的表达式（见 [逻辑和表达式](#31025-逻辑和表达式)）
- `LogicalLeftShiftExpression = Expression "<<" Expression .` — 对两个值进行逻辑左移操作的表达式（见 [逻辑左移表达式](#31014-逻辑左移表达式)）
- `LogicalOrExpression = Expression "||" Expression .` — 对两个布尔值进行 OR 操作的表达式（见 [逻辑或表达式](#31026-逻辑或表达式)）
- `LogicalNotExpression = "!" Expression .` — 对一个布尔值进行取反的表达式（见 [逻辑非表达式](#3105-逻辑非表达式)）
- `DivideExpression = Expression "/" Expression .` — 对两个值进行求商的表达式（见 [除法表达式](#31010-除法表达式)）

有关语句：

- `DisposeStatement = "dispose" ( Identifier | PointerMemberAccessExpression ) .` — 销毁堆存储的语句（见 [dispose 语句](#47-dispose-语句)）
- `Block = "{" { Statement | Block } "}" .` — 包含语句序列的作用域（见 [代码块](#42-代码块)）
- `VariableDefinition = { Modifier } "variable" Name [ ":" Type ] [ "=" Expression ] .` — 在当前作用域内取得实例存储的标识符种类（见 [变量](#43-变量)）
- `AllocateDefinition = { Modifier } "allocate" [ "(" Expression ")" ] [ "manual" ] Name [ ":" Type ] [ "=" Expression ] .` — 在堆上取得实例存储的标识符种类（见 [堆分配](#45-堆分配)）
- `ConstantDefinition = { Modifier } "constant" Name [ GenericParameters ] [ ":" Type ] [ "=" Expression | Block ] .` — 初始化后不可被赋值的标识符种类（见 [常量](#44-常量)）
- `ReturnStatement = "return" [ Expression ] .` — 通过传递返回值直接退出函数的语句（见 [return 语句](#492-return-语句)）
- `ThrowStatement = "throw" Expression .` — 在 `trap` 或 `catch` 中抛出一个值、交由 `trap` 拦截的本地控制流语句（见 [throw 语句](#493-throw-语句)）
- `TrapStatement  = "trap" TrapBody { "catch" CatchCondition CatchBlock } [ "finally" FinallyBlock ] . …` — 拦截本块及内层 `trap` 中产生的抛出值的本地控制流语句（见 [trap 语句](#494-trap-语句)）
- 程序处理错误和意外情况的方式（见 [异常处理](#491-异常处理)）
- `Statement = VariableDefinition …` — 代码块中可独立出现的语法单位（见 [语句](#41-语句)）
- `ExtensionDeclaration = "extension" [ "for" ExtensionTarget ] Block .` — 为类型追加成员的声明（见 [扩展](#283-扩展)）
- `SetStatement          = AssignmentTarget "=" Expression . …` — 以目标值表达式覆盖赋值目标所占内存的语句（见 [赋值语句](#46-赋值语句)）
- `BreakStatement = "break" [ Name ] .` — 退出控制流的逻辑控制流语句（见 [break 语句](#487-break-语句)）
- `ContinueStatement = "continue" [ Name ] .` — 继续控制流的逻辑控制流语句（见 [continue 语句](#488-continue-语句)）
- `DoWhileStatement = "do" [ ":" Name ] Block "while" Expression .` — 根据条件选择是否继续执行代码块的逻辑控制流语句（见 [do while 语句](#484-do-while-语句)）
- `ForStatement = "for" [ "&" ] Name ":" Type "in" TraverseTarget [ ":" Name ] Block . …` — 遍历数组或可迭代对象并执行代码块的逻辑控制流语句（见 [for 语句](#485-for-语句)）
- `IfStatement = "if" Expression Block { "else" "if" Expression Block } [ "else" Block ] .` — 根据条件选择执行代码块的逻辑控制流语句（见 [if 语句](#482-if-语句)）
- `MatchStatement  = "match" Expression [ ":" Name ] "{" { MatchCase } "}" . …` — 根据模式选择执行代码块的逻辑控制流语句（见 [match 语句](#486-match-语句)）
- `WhileStatement = "while" Expression [ ":" Name ] Block .` — 根据条件选择是否继续执行代码块的逻辑控制流语句（见 [while 语句](#483-while-语句)）
- 用于标识逻辑控制流语句的名称（见 [逻辑控制流名称](#481-逻辑控制流名称)）

有关函数：

- `FunctionDeclarationSugar = { Modifier } "constant" Name [ GenericParameters ] ":" FunctionTypeConstructor Block .` — 在标识符定义中以 `Block` 替代 `= <函数字面量>` 的语法形式（见 [函数定义语法糖](#71-函数定义语法糖)）
- `Parameters = Parameter { "," Parameter } . …` — 声明函数类型构造器的参数（见 [参数](#72-参数)）
- `LiteralParameters = LiteralParameter { "," LiteralParameter } . …` — 声明函数字面量的参数（见 [参数](#72-参数)）
- `ParameterList = Parameters [ "," "wildcard" ] | "wildcard" . …` — 函数类型构造器的参数列表（见 [函数类型构造器](#264-函数类型构造器)）
- `Parameter = [ "#" ] [ Name ":" ] [ "&" ] Type [ "=" Expression ] . …` — 函数类型构造器的参数（见 [参数](#72-参数)）
- `LiteralParameter = [ "#" ] Name [ ":" [ "&" ] Type ] . …` — 函数字面量的参数（见 [参数](#72-参数)）
- `Arguments = [ Argument { "," Argument } ] . …` — 调用方传入函数的值（见 [实参](#73-实参)）
- 声明在扩展块内、`this` 参数的类型为扩展目标类型的函数常量，用于直接操作实例及实例成员（见 [方法](#74-方法)）
- `CompileTimeExpression = "#" "(" Expression ")" .` — 在编译期求值表达式并把结果保留到运行时的形式（见 [编译期表达式](#103-编译期表达式)）
- `CompileTimeBlock = "#" Block .` — 在编译期执行代码并把终产物保留到运行时的形式（见 [编译期块](#104-编译期块)）
- 从同名函数常量中选取被调用者的编译期过程（见 [重载决议](#75-重载决议)）

有关泛型：

- `MonomorphizationExpression = ( Identifier | Expression ) "<" [ Type ] { ";" [ Type ] } ">" .` — 对泛型标识符进行单态化的表达式（见 [单态化表达式](#92-单态化表达式)）
- `GenericParameters = "<" GenericParameterDefinition { ";" GenericParameterDefinition } ">" . …` — 声明中的类型占位符，用于编译期单态化（见 [泛型参数](#91-泛型参数)）

有关修饰符：

- `AbstractModifier = "abstract" .` — 用于声明抽象类的修饰符（见 [abstract 修饰符](#811-abstract-修饰符)）
- `AlignedModifier = "aligned" "(" IntegerLiteral ")" .` — 用于声明结构体默认对齐、结构体字段对齐或共同体成员偏移的带参修饰符（见 [aligned(N) 修饰符](#815-alignedn-修饰符)）
- `ImplicitableModifier = "implicitable" .` — 用于声明类型转换可隐式进行的修饰符（见 [implicitable 修饰符](#88-implicitable-修饰符)）
- `LinkableModifier = "linkable" [ "(" StringLiteral ")" ] .` — 用于保证函数常量以外部符号暴露的修饰符（见 [linkable 修饰符](#810-linkable-修饰符)）
- `OverrideModifier = "override" .` — 用于声明重写方法的修饰符（见 [override 修饰符](#814-override-修饰符)）
- `PrivateAccessibilityModifier = "private" .` — 声明仅在声明所在作用域内可访问的基础可访问性修饰符（见 [private 修饰符](#84-private-修饰符)）
- `ProtectedAccessibilityModifier = "protected" .` — 声明可被声明所在作用域及其派生作用域访问的基础可访问性修饰符（见 [protected 修饰符](#85-protected-修饰符)）
- `PublicAccessibilityModifier = "public" .` — 声明可被所有作用域访问的基础可访问性修饰符（见 [public 修饰符](#83-public-修饰符)）
- `ReadonlyModifier = "readonly" .` — 用于声明只读成员的修饰符（见 [readonly 修饰符](#87-readonly-修饰符)）
- `ScopedModifier = "scoped" "(" ScopedTarget { "," ScopedTarget } ")" . …` — 以具名目标裁剪可访问性的可访问性裁剪修饰符（见 [scoped 修饰符](#86-scoped-修饰符)）
- `SealedModifier = "sealed" .` — 用于声明不可被继承的类或不可被重写的方法的修饰符（见 [sealed 修饰符](#812-sealed-修饰符)）
- `StaticModifier = "static" .` — 用于声明与类型关联、但不与实例关联的成员的修饰符（见 [static 修饰符](#816-static-修饰符)）
- `VerbatimModifier = "verbatim" .` — 用于禁止编译期优化的修饰符（见 [verbatim 修饰符](#89-verbatim-修饰符)）
- `VirtualModifier = "virtual" .` — 用于声明可被重写的方法的修饰符（见 [virtual 修饰符](#813-virtual-修饰符)）
- `Modifier = AccessibilityModifier …` — 位于标识符种类之前、用于限定标识符行为的语法形式（见 [修饰符](#81-修饰符)）
- `AccessibilityModifier = BaseAccessibilityModifier | ScopedModifier . …` — 限定标识符可被哪些作用域访问的修饰符（见 [可访问性修饰符](#82-可访问性修饰符)）

有关模块：

- `ImportStatement = "import" Identifier .` — 将目标标识符的成员引入当前作用域的语句（见 [导入](#62-导入)）
- `ModuleDeclaration = { Modifier } "module" Name Block .` — 组织标识符的命名空间（见 [模块](#61-模块)）

有关内存模型：

- 分析堆分配单位生命周期的编译期工具（见 [NOLAA](#112-nolaa)）
- 为实例取得内存空间的行为（见 [内存分配](#111-内存分配)）

有关程序：

- 程序启动时被调用的函数常量（见 [主函数](#131-主函数)）
- 程序从入口点开始、直到终止的执行次序（见 [启动流程](#132-启动流程)）

有关 ABI：

- NovaSharp 编译产物在二进制层面互相调用的接口约定（见 [NovaSharp ABI](#121-novasharp-abi)）
- 把 NovaSharp 名字编码为二进制符号名的规则（见 [名称修饰](#122-名称修饰)）

有关设计基准：

- 对设计原则在 Built-In Library 的设计上的具体落地（见 [Built-In Library 设计原则](#143-built-in-library-设计原则)）
- NovaSharp 语法设计的根本宗旨（见 [核心设计哲学](#141-核心设计哲学)）
- 对核心设计哲学的具体落地（见 [设计原则](#142-设计原则)）

有关附录：

- Built-In Library 强制附带的全部定义（见 [Built-In Library 完整内容](#152-built-in-library-完整内容)）
- Compile-Time Library 的完整定义（见 [Compile-Time Library 完整内容](#153-compile-time-library-完整内容)）

### 15.2 Built-In Library 完整内容

**Built-In Library 完整内容**是 Built-In Library（见 [Built-In Library 设计原则](#143-built-in-library-设计原则)）强制附带的全部定义。

```novasharp
/// @brief Represents the root class of the inheritance hierarchy.
abstract class Object
{

}

/// @brief Identifies the calling convention of a function type.
enumeration CallingConvention: integer(4)
{
    /// @brief The platform's default calling convention.
    PlatformDefault = 0;
    /// @brief The C declaration calling convention.
    CDeclaration = 1;
    /// @brief The standard calling convention.
    StandardCall = 2;
    /// @brief The fast calling convention.
    FastCall = 3;
    /// @brief The System V AMD64 calling convention.
    SystemVAMD64 = 4;
    /// @brief The this-call calling convention.
    ThisCall = 5;
    /// @brief The vector calling convention.
    VectorCall = 6;
    /// @brief The Microsoft x64 calling convention.
    MicrosoftX64 = 7;
}

/// @brief Serves as the base class of all exceptions.
class Exception
{
    /// @brief Holds the exception that caused this exception, if any.
    public InnerException: Optional<Exception>;

    extension
    {
        /// @brief Initializes the exception.
        /// @param this The exception being initialized.
        /// @param innerException The exception that caused this exception.
        public constant Construct(this: Exception, innerException: Optional<Exception> = Optional<Exception>.Null)
        {
            this.InnerException = innerException;
        }
    }
}

/// @brief Thrown when a requested operation is not implemented.
class NotImplementedException: Exception
{
    extension
    {
        /// @brief Initializes the exception.
        /// @param this The exception being initialized.
        public constant Construct(this: NotImplementedException)
        {
            base.Construct(innerException: Optional<Exception>.Null);
        }
    }
}

/// @brief Thrown when an integer division or remainder has a zero divisor.
class DivideByZeroException: Exception
{
    extension
    {
        /// @brief Initializes the exception.
        /// @param this The exception being initialized.
        /// @param innerException The exception that caused this exception.
        public constant Construct(this: DivideByZeroException, innerException: Optional<Exception> = Optional<Exception>.Null)
        {
            base.Construct(innerException: innerException);
        }
    }
}

/// @brief Thrown when an index is outside the bounds of an array.
class OutOfRangeException: Exception
{
    extension
    {
        /// @brief Initializes the exception.
        /// @param this The exception being initialized.
        /// @param innerException The exception that caused this exception.
        public constant Construct(this: OutOfRangeException, innerException: Optional<Exception> = Optional<Exception>.Null)
        {
            base.Construct(innerException: innerException);
        }
    }
}

/// @brief Thrown when memory allocation fails.
class AllocateFailedException: Exception
{
    extension
    {
        /// @brief Initializes the exception.
        /// @param this The exception being initialized.
        public constant Construct(this: AllocateFailedException)
        {
            base.Construct(innerException: Optional<Exception>.Null);
        }
    }
}

/// @brief Thrown when memory deallocation fails.
class DeallocateFailedException: Exception
{
    extension
    {
        /// @brief Initializes the exception.
        /// @param this The exception being initialized.
        public constant Construct(this: DeallocateFailedException)
        {
            base.Construct(innerException: Optional<Exception>.Null);
        }
    }
}

/// @brief Iterates over the elements of a sequence.
/// @tparam T The type of the elements.
interface IIterator<T>
{
    /// @brief Advances to the next element.
    /// @return The next element, or Null when there are no more elements.
    public constant Next(this: IIterator<T>): Optional<T>;

    /// @brief Returns the iterator to its initial position.
    public constant Reset(this: IIterator<T>);
}

/// @brief Exposes an iterator over the elements of a sequence.
/// @tparam T The type of the elements.
interface IIterable<T>
{
    /// @brief Gets an iterator over the elements.
    public accessor Iterator: IIterator<T> { get; }
}

/// @brief Provides heap allocation and deallocation.
interface IAllocator
{
    /// @brief Allocates memory.
    /// @param this The allocator.
    /// @param size The requested size in bytes.
    /// @param alignment The requested alignment in bytes.
    /// @return The allocated pointer, or an allocation failure.
    public constant Allocate(this: IAllocator, size: unsigned integer(8), alignment: unsigned integer(8)): Result<pointer; AllocateFailedException>;

    /// @brief Deallocates memory.
    /// @param this The allocator.
    /// @param block The block to deallocate.
    /// @return An empty result, or a deallocation failure.
    public constant Deallocate(this: IAllocator, block: pointer): Result<; DeallocateFailedException>;
}

/// @brief Represents an optional value.
variant Optional<T>
{
    Value: T;
    Null;

    extension
    {
        /// @brief Maps Optional to Result for ??.
        /// @param value The optional value.
        /// @return A Result whose Value carries T, or whose Alternative is empty.
        operator ??(value: Optional<T>): Result<T;>
        {
            match value
            {
                case is payload:Optional<T>.Value:
                    return Result<T;>.Value(payload);
                case is Optional<T>.Null:
                    return Result<T;>.Alternative;
            }
        }
    }
}

/// @brief Represents a primary value or an alternative.
/// @tparam TValue The primary value type.
/// @tparam TAlternative The alternative type.
variant Result<TValue; TAlternative>
{
    Value: TValue;
    Alternative: TAlternative;

    extension
    {
        /// @brief Returns the result itself as the ?? decision.
        /// @param value The result to decide on.
        /// @return The same result.
        operator ??(value: Result<TValue; TAlternative>): Result<TValue; TAlternative>
        {
            return value;
        }
    }
}
```

### 15.3 Compile-Time Library 完整内容

**Compile-Time Library 完整内容**是编译器在编译期提供的全部定义。

```novasharp
/// @brief Exposes compile-time type queries.
module Type
{
    /// @brief Returns the size of T in bytes.
    /// @return A value whose width equals the target pointer width.
    public linkable
    constant SizeOf<T>(): unsigned integer(8);
}

/// @brief Exposes compile-time diagnostics.
module Compiler
{
    /// @brief Emits a compile-time note.
    /// @param message The message bytes.
    /// @param length The message byte length.
    public linkable
    constant LogNote(message[length: unsigned integer(4)]: unsigned integer(1));

    /// @brief Emits a compile-time warning.
    /// @param message The message bytes.
    /// @param length The message byte length.
    public linkable
    constant LogWarning(message[length: unsigned integer(4)]: unsigned integer(1));

    /// @brief Emits a compile-time error.
    /// @param message The message bytes.
    /// @param length The message byte length.
    public linkable
    constant LogError(message[length: unsigned integer(4)]: unsigned integer(1));

    /// @brief Asserts a compile-time condition.
    /// @param condition The condition to assert.
    public linkable
    constant Assert(condition: boolean);

    /// @brief Asserts a compile-time condition with a message.
    /// @param condition The condition to assert.
    /// @param message The message bytes.
    /// @param length The message byte length.
    public linkable
    constant Assert(condition: boolean, message[length: unsigned integer(4)]: unsigned integer(1));
}

/// @brief Exposes heap lifetime analysis controls.
module NOLAA
{
    /// @brief Stops automatic analysis of the pointed heap object.
    /// @param x The heap object pointer.
    public linkable
    constant Abandon(x: pointer);

    /// @brief Requires required to exist while requiredBy exists.
    /// @param required The heap object that must exist.
    /// @param requiredBy The heap object that needs required.
    public linkable
    constant Bind(required: pointer, requiredBy: pointer);

    /// @brief Assumes the next statement does not require x.
    /// @param x The heap object pointer.
    public linkable
    constant AssumeNoDemandNext(x: pointer);
}
```

---

This project is licensed under the CC-BY-4.0 License. See the [LICENSE](LICENSE) file for details.
