# NovaSharp 语言规范

- 版本: 1.0-草稿
- 日期：2026-06-26

---

NovaSharp 是一门混合范式的编程语言。它以**强大的多场景适配能力**与**高表达力**为设计目标。

## 1 引言

### 1.1 核心设计哲学

NovaSharp 遵循以下**核心哲学**：

- **显式控制为主**——仅保留少量隐式控制流，以提升编程体验。
- **不依赖特定操作系统**——在移除标准库的前提下，在调用 ExitBootService 后的裸机环境中，全语法功能可用。
- **将控制权还给开发者**——编译器仅对语法错误与静态语义错误报错；所有警告及非致命诊断信息不得阻止代码生成。
- **相信开发者**——无 `unsafe` 关键字；保留“危险的”语法设计，开发者知道自己在做什么；语言只为安全性提供工具。

### 1.2 设计原则

NovaSharp 的设计在不违反核心设计哲学的前提下，遵循以下**设计原则**：

| 原则                 | 规则                                                             |
| -------------------- | ---------------------------------------------------------------- |
| **零歧义**           | 拒绝出现任何没有处理规定的语义歧义。                             |
| **尽可能零成本抽象** | 语法糖在编译期完全擦除；未使用的抽象尽可能不产生运行时开销。     |
| **尽可能最小核心**   | 能被当前语法实现的功能，不进核心语法；若必须进，优先作为语法糖。 |
| **分隔符使用**       | `,` 用于小型分割；`;` 用于大型分割。                             |
| **函数是一等公民**   | 将函数视作引用类型，由 Lambda 全权创建。                         |

## 2 词法结构

### 2.1 源文本

源文本采用 UTF-8 编码。编译器将源文本解析为词法单元（Token）序列，随后进行语法分析。

### 2.2 空白与行终止

空白字符用于分隔 Token，无其他语义，它们包括：

- 空格 `U+0020`
- 水平制表 `U+0009`
- 换行 `U+000A`
- 回车 `U+000D`

行终止符用于行号映射。

### 2.3 语句终止

语句通过以下两种方式之一终止：

1. **分号终止**：当不在泛型上下文中时，语句以 `;` 字符结尾。
2. **大括号终止**：对于 `}` 字符，当在同一行中，该字符之后不再包含任何非空白字符或者非注释代码，同时该字符不在表达式内部时，语句以该字符结尾。

### 2.4 注释

注释包括：

- **单行注释**：由**不在字符串字面量内**的 `//` 开头，至行终止符结束。
- **多行注释**：由**不在字符串字面量内**的 `/*` 开头，至后面第一个 `*/` 结束。不支持嵌套。

注释内容**不参与编译**，视为空白。

### 2.5 关键字与标识符

NovaSharp 包含如下**关键字**。它们的语义详见[附录 1](#附录-1语义映射)。

| 类别            | 关键字                                                                                                                                                                                      |
| --------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **类型种类**    | `class`, `structure`, `interface`, `enumeration`, `variant`, `union`                                                                                                                        |
| **代码块种类**  | `module`                                                                                                                                                                                    |
| **类型构造器**  | `function`, `pointer`, `property`, `nullable`                                                                                                                                               |
| **修饰符**      | `public`, `private`, `protected`, `scoped`, `constant`, `readonly`, `precomputable`, `verbatim`, `manual`, `implicitable`, `linkable`, `virtual`, `override`, `packed`, `sealed`, `nothrow` |
| **控制流/动作** | `if`, `else`, `while`, `do`, `for`, `match`, `case`, `break`, `continue`, `return`, `throw`, `trap`, `catch`, `finally`                                                                     |
| **特殊**        | `this`, `owner`, `base`, `wildcard`, `true`, `false`, `null`, `auto`                                                                                                                        |
| **编译器指令**  | `track`, `define`, `if`, `else`, `end`, `line`（仅对于编译器指令上下文有效）                                                                                                                |

**标识符**为开发者自定义内容的名称。

标识符的命名满足以下要求：

1. **仅包括字母、数字和下划线（`_`）**
2. **不能由数字开头**

当标识符与关键字重名时，按照标识符解析。使用 `@` 符号标识符强制解析为关键字原义。

例如：

```novasharp
// 定义 4 字节整数类型变量 class，初始化为 1
// integer 是 Built-In Library 的 alias
integer class = 1;

// 此时 class 作为标识符，遮蔽 class 关键字
// 若想使用 class 关键字，则需要在 class 前加入 @ 符号
@class A
{

}
```

### 2.6 字面量

#### 2.6.1 整数

```ebnf
IntegerLiteral = DecimalLiteral | HexLiteral | BinaryLiteral .

DecimalLiteral = Digit { Digit | "_" } .
HexLiteral = "0x" HexDigit { HexDigit | "_" } .
BinaryLiteral = "0b" ("0" | "1") { ("0" | "1") | "_" } .

Digit = "0" .. "9" .
HexDigit = Digit | "A" .. "F" | "a" .. "f" .
```

下划线分隔符仅用于可读性，编译器擦除。

整数字面量的类型由编译器根据上下文推断。

#### 2.6.2 浮点数

```ebnf
FloatLiteral = DecimalLiteral "." DecimalLiteral [ Exponent ] [ FloatSuffix ] .

Exponent = ("e" | "E") [ "+" | "-" ] DecimalLiteral .
```

浮点数字面量的类型由编译器根据上下文推断。

#### 2.6.3 字符

```ebnf
CharacterLiteral = "'" Character "'" .
Character = ASCIIChar | EscapeSequence .
ASCIIChar = U+0000 .. U+007F 除 "'" 和 "\" .
```

字符字面量类型为 `unsigned integer(1)`。**仅允许 ASCII 字符及转义序列**；非 ASCII 字符（如 `'中'`）构成编译错误。

#### 2.6.4 字符串

```ebnf
StringLiteral = '"' { StringCharacter } '"' .
StringCharacter = ASCIICharExceptQuoteBackslash | EscapeSequence .
VerbatimString = '@' '"' { AnyCharacterExceptQuote } '"' .
InterpolatedString = '$' StringLiteral | '$' VerbatimString .
```

- 字符串字面量 `"..."`：类型 `pointer byte`，UTF-8 null-terminated，存放于常量段。
- 逐字字符串 `@"..."`：**不处理转义**，**支持多行**，类型 `pointer byte`。
- 插值字符串 `$"..."`：编译期/运行时拼接语法糖，类型 `pointer byte`。
- 逐字插值字符串 `$@"..."`（仅 `$@` 顺序合法）：逐字 + 插值组合。

字符串以 `'\0'` 结尾。

#### 2.6.5 转义序列

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

#### 2.6.6 数组字面量

```ebnf
ArrayLiteral = "{" Expression { "," Expression } [ "," ] "}" .
```

数组字面量的类型为 `pointer T`，丢失长度信息，其中 `T` 为元素表达式的公共可推断类型。所有元素**必须可隐式转换为 `T`**；若无法推断（如空数组 `{}` 且无上下文约束），编译错误。

定义语法糖：

- _（提升编程体验的隐式控制流）_ 隐式转换 `ICollection`：当推断出数组字面量所在表达式的返回值类型为一个实现了 `ICollection<T>` 接口的对象，并且 `T` 与该数组字面量的公共可推断类型一致的时候（作为样例，假设该对象为 `Array`，该数组字面量为 `{ 1, 2 }`，且 `T` 为 `integer`），则展开为 `Array<T>({ 1, 2 }, 2)`，**此时保留长度信息**。关于 `ICollection<T>`，详见[附录 2](#附录-2built-in-library-内容)。

### 2.7 代码块（Block）

**代码块**（Block）以**不在字符串字面量或注释内**的 `{` 字符开头，以**不在字符串字面量或注释内**的 `}`字符结尾。

代码块是一个语句集合。同时，一个代码块是一个作用域。

### 2.8 作用域与遮蔽

在**没有文件级 `module` 声明语法糖**的前提下，一切内容**默认在全局作用域内部**。

当作用域 $A$ 内部出现了作用域 $B$，则认为：

- $A$ 是 $B$ 的**外层作用域**
- $B$ 是 $A$ 的**内层作用域**

当一个作用域中定义了该作用域的外层作用域已经定义过的标识符，则该作用域的标识符遮蔽外层作用域的标识符。使用 `owner` 访问外层作用域的标识符。

例如：

```novasharp
// 不在任何代码块内部，也没有文件级 module 声明语法糖，因此是全局作用域

// 定义 4 字节整数类型变量 a，初始化为 1
// integer 是 Built-In Library 的 alias
integer a = 1;

// 通过函数定义语法糖定义函数 Main
function integer Main()
{
    // 代码块内部，属于全局作用域的内层作用域

    // 定义重名的标识符
    integer a = 2;

    // 此时，Main 函数内部的 a 遮蔽全局作用域的 a
    // 当访问 a 时，访问的是 Main 函数作用域内部的 a
    integer b = a; // b = 2

    // 使用 owner 关键字范围外层作用域的标识符
    integer c = owner.a; // b = 1

    // 同理
    {
        // 代码块内部，属于 Main 函数作用域的内层作用域

        // 定义 8 字节整数类型变量 a，初始化为 1
        // long 是 Built-In Library 的 alias
        // 遮蔽仅针对于标识符，与类型无关
        long c = 3;

        // 因为该作用域下没有与 b 同名的标识符
        // 所以访问所有外层作用域中最内层的、定义了标识符 b 的作用域的标识符 b
        // 通过 Cast 进行类型转换（8 字节整数类型 -> 4 字节整数类型）
        // Cast 是编译器内置的伪函数
        b = Cast<integer>(c);

        // owner 访问的当前作用域的外层作用域，即 Main 函数作用域
        // 而不是全局作用域
        integer d = owner.a; // d = 2

        // owner 可以嵌套
        // 访问 Main 函数作用域的外层作用域，即全局作用域
        d = owner.owner.a; // d = 1
    }

    return 0;
}
```

同一作用域内部**不能定义同名标识符**。

## 3 类型系统

### 3.1 基本类型（BasicType）

**基本类型**（BasicType）由以下内容组成。

| 类型                  | 说明                                            |
| --------------------- | ----------------------------------------------- |
| `integer(N)`          | N 字节有符号整数，N 的合法值为 1、2、4、8 和 16 |
| `unsigned integer(N)` | N 字节无符号整数，N 的合法值同 `integer(N)`     |
| `float(N)`            | N 字节浮点数，N 的合法值为 4 和 8               |
| `boolean`             | 布尔值                                          |
| `void`                | 空类型，仅用于函数返回，不可作为变量类型        |

> [!NOTE]
> 带有括号的基本类型（例如 `integer(N)`）的括号**不可省略**。

### 3.2 类型别名

以下别名由 Built-In Library 强制提供，**不可剥离**：

```novasharp
alias byte = unsigned integer(1);
alias short = integer(2);
alias integer = integer(4);
alias long = integer(8);
alias float = float(4);
alias double = float(8);
```

Built-In Library 完整内容请参考[附录 2](#附录-2built-in-library-内容)。

### 3.3 类型构造器 (TypeConstructor)

**类型构造器**（TypeConstructor）负责与基本类型结合构成新类型。

```ebnf
ConstructedType = TypeConstructor ConstructTargetType .

TypeConstructor = FunctionTypeConstructor
                | PointerTypeConstructor
                | PropertyTypeConstructor
                | NullableTypeConstructor

ConstructTargetType = BasicType | Type
```

#### 3.3.1 函数类型构造器（FunctionTypeConstructor）

**函数类型构造器**所构造的类型为**函数类型**，该类型能够承载函数（作为引用类型），其结构如下：

```ebnf
FunctionTypeConstructor = [ "nothrow" ] "function" [ "(" [ UnnamedParameters | "wildcard" ] [ [","] CallingConventionExpression] ")" ] .

UnnamedParameters = UnnamedParameter {"," UnnamedParameter} .
CallingConventionExpression = Expression.

UnnamedParameter = Type ["this"].
```

其中，`CallingConventionExpression` 所代表的表达式是一个常量表达式，其返回值是一个类型为 `CallingConvention` 的枚举值，该值决定该函数所采用的调用约定。`CallingConvention` 一个定义在 Built-In Library 的枚举，其定义如下：

```novasharp
enumeration CallingConvention : integer
{
    NovaSharpCallingConvention = 0,
    CDeclaration = 1,
    StandardCall = 2,
    FastCall = 3,
    SystemVAMD64 = 4,
    ThisCall = 5,
    VectorCall = 6,
    MicrosoftX64 = 7
}
```

Built-In Library 完整内容请参考[附录 2](#附录-2built-in-library-内容)。

注意：

- `nothrow` 作为类型构造器前缀，**允许且仅允许**修饰 `function`。
- 函数类型构造器的参数列表中的参数**不允许命名**，仅声明类型。唯一允许出现的“参数名”是 `this`，且必须紧跟在类型之后（`Type this`）。
- 参数列表中最多出现一次 this。
- 当省略 `CallingConventionExpression` 时，则默认为 `CallingConvention.NovaSharpCallingConvention`。
- 参数列表为空时，括号内为空：`function()` 表示无参函数构造器。
- 函数类型构造器的 `ConstructTargetType`（见 [3.3](#33-类型构造器-typeconstructor)）是该函数类型的**返回值类型**。
- 当 `wildcard` 独占参数列表时，当调用该类型承载的函数，编译器不会校验传入的参数，这意味着原则上可以传入任意数量和种类的参数。**这是一个会导致未定义行为的高危操作**。

> [!NOTE]
> this 本质上是一个关键字。但是在编写代码的时候，建议将它当作函数名。

对于两个函数类型 $F$ 和 $L$ 函数类型，当同时满足如下条件时，判定 $F = L$：

1. $F$ 和 $L$ 的参数列表的参数数量、顺序和类型相等，或者至少有一方的参数列表为 `wildcard`
2. $F$ 和 $L$ 的调用约定相同
3. $F$ 和 $L$ 的返回值类型相等

> [!NOTE]
> 原则上允许如下**及其危险**的写法：
>
> ```novasharp
> // 定义一个人畜无害的函数变量 A
> function(integer) void A =
>     (integer value) void =>
>     {
>         // Do Something;
>     }
>
> // 定义采用 wildcard 参数列表的函数变量 Middle
> // Middle 的参数列表为 wildcard，条件 1 满足
> // Middle 和 A 的调用约定都为 CallingConvention.NovaSharpCallingConvention（默认值），条件 2 满足
> // Middle 和 A 的返回值类型都为 void（无返回值），条件 3 满足
> // Middle 和 A 的类型相等，允许赋值
> function(wildcard) void Middle = A;
>
> // 这里！
> // Middle 的参数列表为 wildcard，条件 1 满足
> // Middle 和 B 的调用约定都为 CallingConvention.NovaSharpCallingConvention（默认值），条件 2 满足
> // Middle 和 B 的返回值类型都为 void（无返回值），条件 3 满足
> // Middle 和 B 的类型相等，允许赋值
> // 但是调用 B 的时候，由于 B 所承载的函数实际上接受一个 integer 作为第一个参数，这会导致未定义行为
> function(boolean) void B;
> ```
>
> 编译器会对这种安全隐患进行 Warning。

<!--
    一般不存在这样的使用场景……总不可能是取随机数吧？

    —— @willowtree1184
-->

定义语法糖：

- 函数类型构造器的参数列表省略：当参数列表内容可以被编译器根据上下文推断，且给出了具体的函数调用约定时，可以省略参数列表；当条件不满足但参数列表为空时，按原样解读为空参数列表。
- 函数类型构造器的括号省略：当括号内容可以被编译器根据上下文推断时，函数类型构造器的括号可以被省略，即只剩下 `function`。

> [!NOTE]
> 当参数列表与调用约定同时存在时，调用约定表达式必须位于参数列表之后，且用逗号分隔。

#### 3.3.2 指针类型构造器（PointerTypeConstructor）

**指针类型构造器**所构造的类型为**指针类型**。其结构如下：

```ebnf
PointerTypeConstructor = "pointer"
```

### 3.3.3 属性类型构造器（PropertyTypeConstructor）

**属性类型构造器**所构造的类型为**属性**。其结构如下：

```ebnf
PropertyTypeConstructor = "property"
```

属性类型构造器只能够出现在 `class` 和 `interface` 的定义与实现中。

### 3.3.4 可空类型构造器（NullableTypeConstructor）

**可空类型构造器**所构造的类型为**可空类型**，这意味着该类型可以被赋值为 `null`。其结构如下：

```ebnf
NullableTypeConstructor = "nullable"
```

### 3.4 泛型

泛型参数允许类型、函数和接口声明在定义时保留类型占位符，在实例化时由编译器单态化。定义时，其结构如下。单态化应该在编译期执行，失败则报错。

```ebnf
GenericParameters = "<" GenericParameterDefinition { ";" GenericParameterDefinition } ">" .

GenericParameterDefinition = GenericParameter [ ":" Constraint { "," Constraint } ] .

GenericParameter = Identifier .
Constraint = TypeKind | Identifier .

TypeKind = "class" | "structure" | "enumeration" | "property" | "function" | "interface" | "variant" | "union" .
```

其中：

- 参数间用分号 `;` 分隔；约束间用逗号 `,` 聚合（AND 语义）。
- 约束可以是类型种类关键字（见 [2.5](#25-关键字与标识符)），也可以是一个具体的类型。当一个约束为：
  - 类型种类关键字时，含义为“要求传入类型的种类必须是要求的种类”；
  - 具体类型时，含义为“要求传入类型必须继承、实现或者是该类型”。
- 泛型仅允许出现在 `class`、`structure`、`interface`、`enumeration`、`variant`、`constant function` 声明中。函数或函数指针类型（`pointer function(...) T` 或 `function(...) T` 类型的值）不可携带泛型参数。

泛型相关的代码样例如下：

```novasharp
// 定义结构体 A
// 此时 A 为一个类型
// structure 是 A 的类型种类
structure A
{
    // 通过函数定义语法糖定义构造函数
    public function void Construct()
    {

    }
}

// 定义类 B
// 同理，此时 B 为一个类型
// class 是 B 的类型种类
class B
{
    // 通过函数定义语法糖定义构造函数
    public function void Construct()
    {

    }
}

// 我们以泛型函数举例
// 全脱糖地定义一个泛型函数
// 其中，约束 T 的类型种类为结构体（structure）
<T: structure> constant function(T) T Foo =
    (T value) T => {
        return value; // 直接原样返回
    };

// 再以泛型结构体举例
// 其中，约束 T 的类型种类为结构体（structure），U 没有约束
// U 和 T 之间用分号 `;` 隔开
<T: class; U> structure C
{
    // 类型为泛型 T 的结构体成员
    T ClassMember;

    // 类型为泛型 U 的结构体成员
    U AnotherMember;

    // 通过函数定义语法糖定义构造函数
    public function void Construct(T classMember, U anotherMember)
    {
        // this 可以省略（因为没有遮蔽），这里践行最佳实践
        this.ClassMember = classMember;
        this.AnotherMember = anotherMember;
    }
}

// 通过函数定义语法糖定义函数 Main
function integer Main()
{
    // 这里！
    A value1 = Foo<A>(new A());

    // 泛型参数的传入通过尖括号：`<A>`，尖括号跟在 Foo 的函数名后面，此时 T = A
    // 由于 A 的类型种类为结构体，符合约束
    // 泛型参数必须是一个标识符，而不是表达式

    // [重要！] 如果有多个参数，用逗号 `,` 隔开，这和定义时不一样，如下：
    C value2 = new C<B, A>(new B(), value1);

    // 而对于非泛型函数变量，必须传入一个单态化后的函数
    function(A) A SpecializedFoo = Foo<A>;
    SpecializedFoo(value1);
}
```

### 3.5 类型构造语法

一个完整的类型的格式应当如下：

```ebnf
Type = [ GenericParameters ] (ConstructedType | BasicType) .
```

其中，`GenericParameters` 仅被修饰为 `constant` 的函数类型可用。

NovaSharp 的类型构造语法是前缀、右结合的。例如一个如下函数常量声明：

```novasharp
// 此处假设有结构体 String，作为对原始字符串的高级封装。
public precomputable constant <T> function(String, String) pointer function(wildcard, CallingConvention.CDeclaration) T LoadFunctionFromDLL = /* Lambda 表达式，此处留空 */;
```

其中：

1. 由于最外层 `function(String, String)` 被 `constant` 修饰，泛型使用合法。
2. 对于类型 `<T> function(String, String) pointer function(wildcard, CallingConvention.CDeclaration) T`，含义为：这是一个接收两个 `String` 类型参数的、接受泛型 `T` 的泛型函数（`<T> function(String, String)`），它返回一个函数指针（`pointer function(wildcard, CallingConvention.CDeclaration) T`）；该指针指向一个参数列表未知的、采用 CDecl 约定的、返回值类型为 T 的函数（`function(wildcard, CallingConvention.CDeclaration) T`）。

### 3.6 枚举（Enumeration）

枚举是一个值类型，它提供标识符-值映射。其结构如下：

```ebnf
EnumerationDeclaration = [Modifiers] "enumeration" Identifier ":" BasicType "{" EnumerationMemberDeclaration { "," EnumerationMemberDeclaration } [","] "}".

EnumerationMemberDeclaration = Identifier "=" Expression .
```

其中：

- 强制显式赋值：成员必须写 `= Value`。
- 不允许有超过一个成员表示相同的值
- 必须给出底层类型，且底层类型只能是基本类型（见 [3.1](#31-基本类型basictype)）
- 在内存中，枚举值直接存储其对应为的、底层类型的值
- 在语法上，枚举值可以隐式转换为其对应的、底层类型的值；但是底层类型的值要转换为枚举值必须显式显式转换

定义语法糖：

- 隐藏枚举类型名：当不存在二义性时，可以省略枚举类型名。例如：`CallingConvention.CDeclaration` 可以简写为 `CDeclaration`。

例如：

```novasharp
// 定义枚举 Enumeration
enumeration Enum : integer
{
    // 枚举值 A 对应 1
    A = 1,

    // 同理
    B = 2,

    // 同理
    C = 3
}

// 通过函数定义语法糖定义函数 Foo
// 该函数采用 CDecl，由于没有二义性，所以 CallingConvention.CDeclaration 简写为 CDeclaration
function(CDeclaration) integer Foo(integer value)
{
    return value;
}

// 通过函数定义语法糖定义函数 Main
function integer Main()
{
    Enum enum = Enum.A; // 通过 枚举类型名.枚举值

    // enum 原本为底层类型为 integer 的 Enum 类型，被隐式转换为 integer
    integer returnValue = Foo(enum);

    // integer -> Enum 必须显式转换
    // 通过 Cast 进行类型转换
    // Cast 是编译器内置的伪函数
    Enum anotherEnum = Cast<Enum>(returnValue);
}
```

## 附录 1：语义映射

NovaSharp 中的部分关键字与符号拥有其专门的**语义**。它们按照下表映射：

| 项              | 语义                                                |
| --------------- | --------------------------------------------------- |
| `class`         | 类                                                  |
| `structure`     | 结构                                                |
| `interface`     | 接口；约定                                          |
| `enumeration`   | 枚举；标识符-值映射                                 |
| `variant`       | 变体；拥有多种形态的值                              |
| `union`         | 联合体                                              |
| `module`        | 模块                                                |
| `function`      | 函数                                                |
| `pointer`       | 指针                                                |
| `property`      | 属性                                                |
| `nullable`      | 可为 `null` 的                                      |
| `public`        | 公共的                                              |
| `private`       | 私密的                                              |
| `protected`     | 受保护的；外部仅继承者可见的                        |
| `scoped`        | 可被……访问的                                        |
| `constant`      | 常量                                                |
| `readonly`      | （内容确定后）只读的                                |
| `precomputable` | 允许启用“编译期求值”的（但不强制）                  |
| `verbatim`      | 不进行任何优化                                      |
| `manual`        | 手动管理                                            |
| `implicitable`  | 允许隐式                                            |
| `linkable`      | 可以被外部链接的                                    |
| `virtual`       | 虚拟的，可被 `override` 的                          |
| `override`      | 覆写                                                |
| `packed`        | 被打包的，没有间隙的                                |
| `sealed`        | 密封的，不允许被继承的                              |
| `nothrow`       | 不能够通过 `throw` 退出的                           |
| `if`            | 如果                                                |
| `else`          | 否则                                                |
| `while`         | 当                                                  |
| `do`            | 先执行，再……                                        |
| `for`           | 对于                                                |
| `match`         | 匹配                                                |
| `case`          | 情况                                                |
| `break`         | 打破                                                |
| `continue`      | 尝试从下一次/下一个的开头处继续（如果判断通过的话） |
| `return`        | 返回；携带值返回                                    |
| `throw`         | 抛出一个对象                                        |
| `trap`          | 拦截                                                |
| `catch`         | 尝试接住抛出的对象                                  |
| `finally`       | 最终的；函数退出前必须执行的最后代码                |
| `this`          | 当前处理的                                          |
| `owner`         | 所有者；父                                          |
| `base`          | 基类型                                              |
| `wildcard`      | 通配符                                              |
| `true`          | 真；条件成立                                        |
| `false`         | 假；条件不成立                                      |
| `null`          | 空                                                  |
| `auto`          | 自动判断                                            |
| `@`             | 原来的，原本的                                      |
| `:`             | 标记；身份                                          |

## 附录 2：Built-In Library 内容

Built-In Library 是编译时必须附加，且不能被剥离的代码。

```novasharp
// NovaSharp Built-In Library

// ========================================
// Aliases
// ========================================

/// @brief 8-bit unsigned integer type alias.
alias byte = unsigned integer(1);

/// @brief 16-bit signed integer type alias.
alias short = integer(2);

/// @brief 32-bit signed integer type alias (default integer).
alias integer = integer(4);

/// @brief 64-bit signed integer type alias.
alias long = integer(8);

/// @brief 32-bit IEEE 754 floating-point type alias.
alias float = float(4);

/// @brief 64-bit IEEE 754 floating-point type alias.
alias double = float(8);

// ========================================
// Calling Convention enumeration
// ========================================

/// @brief Specifies the calling convention for function invocation.
/// @details Determines how arguments are passed and the stack is managed across different platforms and interoperability scenarios.
enumeration CallingConvention : integer
{
    /// @brief Default NovaSharp calling convention.
    NovaSharpCallingConvention = 0,
    /// @brief C declaration calling convention (cdecl).
    CDeclaration = 1,
    /// @brief Standard x86 calling convention (stdcall).
    StandardCall = 2,
    /// @brief Fast calling convention (fastcall).
    FastCall = 3,
    /// @brief System V AMD64 ABI calling convention.
    SystemVAMD64 = 4,
    /// @brief ThisCall calling convention (passes this pointer in register).
    ThisCall = 5,
    /// @brief Vector calling convention for SIMD types.
    VectorCall = 6,
    /// @brief Microsoft x64 calling convention.
    MicrosoftX64 = 7
}

// ========================================
// Value
// ========================================

/// @brief A generic wrapper class encapsulating a single value.
/// @tparam TValue The type of the encapsulated value.
<TValue> class Value
{
    /// @brief Gets or sets the encapsulated value.
    public virtual property TValue Value { get; set; }

    /// @brief Constructs a new Value instance.
    /// @param value The initial value to encapsulate.
    public function void Construct(TValue value)
    {
        this.Value = value;
    }
}

// ========================================
// Enumerable
// ========================================

/// @brief Defines an enumerable sequence that supports iteration.
/// @tparam T The type of elements in the sequence.
<T> interface IEnumerable
{
    /// @brief Gets an enumerator to iterate through the sequence.
    public property IEnumerator<T> Enumerator { get; }
}

/// @brief Supports a simple iteration over a generic collection.
/// @tparam T The type of elements being enumerated.
<T> interface IEnumerator
{
    /// @brief Gets the current element in the collection.
    public property T Current { get; }

    /// @brief Advances the enumerator to the next element.
    /// @return true if the enumerator was successfully advanced; false if the end was reached.
    public function boolean Next();

    /// @brief Resets the enumerator to its initial position.
    public function void Reset();
}

// ========================================
// Collection
// ========================================

/// @brief Represents a generic collection of elements with add/remove capabilities.
/// @tparam T The type of elements in the collection.
/// @extends IEnumerable<T>
<T> interface ICollection : IEnumerable<T>
{
    /// @brief Adds an item to the collection.
    /// @param item The element to add.
    public function void Add(T item);

    /// @brief Removes the first occurrence of a specific item.
    /// @param item The element to remove.
    public function void Remove(T item);

    /// @brief Removes all elements from the collection.
    public function void Clear();

    /// @brief Determines whether the collection contains a specific item.
    /// @param item The element to locate.
    /// @return true if the item is found; otherwise false.
    public function boolean IsContain(T item);

    /// @brief Gets the number of elements contained in the collection.
    public property long Count { get; }

    /// @brief Constructs a collection from a native pointer and size.
    /// @param begin Pointer to the first element.
    /// @param size Number of elements.
    public function void Construct(pointer T begin, long size);

    /// @brief Constructs a collection from an existing enumerable source.
    /// @param source The source sequence to copy elements from.
    public function void Construct(IEnumerable<T> source);
}

// ========================================
// Aspect
// ========================================

/// @brief Provides aspect-oriented programming (AOP) interception points.
/// @details Draft implementation for cross-cutting concerns. Allows interception of function calls, property access, field access, and object lifecycle events.
/// @note This is a draft and not the final version.
abstract class Aspect
{
    // ====================
    // For function
    // ====================

    /// @brief Called before a function is invoked.
    /// @param callee The function being intercepted.
    public virtual function void OnBeforeInvoke(constant function(wildcard) callee)
    {

    }

    /// @brief Called after a function completes execution.
    /// @tparam TValue The return type of the intercepted function.
    /// @param callee The function that was executed.
    public virtual <TValue> function void OnAfterInvoke(constant function(wildcard) callee)
    {

    }

    /// @brief Called when a function throws an exception.
    /// @tparam TValue The exception type (must be a class).
    /// @param thrower The function that threw the exception.
    /// @param value The thrown exception instance.
    public virtual <TValue: class> function void OnThrow(constant function(wildcard) thrower, constant TValue value)
    {

    }

    /// @brief Called when an exception is caught within the interception context.
    /// @tparam TValue The exception type (must be a class).
    /// @param catcher The function context where the exception was caught.
    /// @param value The caught exception instance.
    public virtual <TValue: class> function void OnCatch(constant function(wildcard) catcher, constant TValue value)
    {

    }

    /// @brief Called when a function returns a value.
    /// @tparam TReturn The return type of the function.
    /// @param returner The function returning the value.
    /// @param returnValue Pointer to the return value.
    public virtual <TReturn> function void OnReturn(constant function(wildcard) returner, constant pointer TReturn returnValue)
    {

    }

    // ====================
    // For property
    // ====================

    /// @brief Called before a property getter is accessed.
    /// @tparam TValue The property type.
    /// @param callee The property getter being accessed.
    /// @param value Pointer to the property value.
    public virtual <TValue> function void OnBeforePropertyGet(constant function(wildcard) callee, constant pointer TValue value)
    {

    }

    /// @brief Called after a property getter completes.
    /// @tparam TValue The property type.
    /// @param callee The property getter that was accessed.
    /// @param value Pointer to the retrieved property value.
    public virtual <TValue> function void OnAfterPropertyGet(constant function(wildcard) callee, constant pointer TValue value)
    {

    }

    /// @brief Called before a property setter is invoked.
    /// @tparam TValue The property type.
    /// @param callee The property setter being invoked.
    /// @param value Pointer to the new property value.
    public virtual <TValue> function void OnBeforePropertySet(constant function(wildcard) callee, constant pointer TValue value)
    {

    }

    /// @brief Called after a property setter completes.
    /// @tparam TValue The property type.
    /// @param callee The property setter that was invoked.
    /// @param value Pointer to the assigned property value.
    public virtual <TValue> function void OnAfterPropertySet(constant function(wildcard) callee, constant pointer TValue value)
    {

    }

    // ====================
    // For field
    // ====================

    /// @brief Called before a field value is read.
    /// @tparam TValue The field type.
    /// @param value Pointer to the field value.
    public virtual <TValue> function void OnBeforeFieldGet(constant pointer TValue value)
    {

    }

    /// @brief Called after a field value is read.
    /// @tparam TValue The field type.
    /// @param value Pointer to the field value.
    public virtual <TValue> function void OnAfterFieldGet(constant pointer TValue value)
    {

    }

    /// @brief Called before a field value is written.
    /// @tparam TValue The field type.
    /// @param value Pointer to the new field value.
    public virtual <TValue> function void OnBeforeFieldSet(constant pointer TValue value)
    {

    }

    /// @brief Called after a field value is written.
    /// @tparam TValue The field type.
    /// @param value Pointer to the written field value.
    public virtual <TValue> function void OnAfterFieldSet(constant pointer TValue value)
    {

    }

    // ====================
    // For class / structure
    // ====================

    /// @brief Called before a class or structure constructor executes.
    /// @tparam TTarget The type being constructed.
    public virtual <TTarget> function void OnBeforeConstruct()
    {

    }

    /// @brief Called after a class or structure is constructed.
    /// @tparam TTarget The type that was constructed.
    /// @param target Pointer to the newly constructed instance.
    public virtual <TTarget> function void OnAfterConstruct(constant pointer TTarget target)
    {

    }

    /// @brief Called before a class or structure destructor executes.
    /// @tparam TTarget The type being destructed.
    /// @param target Pointer to the instance being destroyed.
    public virtual <TTarget> function void OnBeforeDestruct(constant pointer TTarget target)
    {

    }

    /// @brief Called after a class or structure destructor completes.
    /// @tparam TTarget The type that was destructed.
    public virtual <TTarget> function void OnAfterDestruct()
    {

    }
}
```

---

This project is licensed under the CC-BY-4.0 License. See the [LICENSE](LICENSE) file for details.
