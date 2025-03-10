> 人生苦短，我用 Python

# 数字

## 基本类型

### 整数

在 Python 编程中，整数就是数学意义上的整数，包括正整数、负整数和零，且它的位数是任意的。根据表示方法的不同，可以分为：

- 二进制整数
- 八进制整数
- 十进制整数
- 十六进制整数

### 浮点数

浮点数，即数学意义上的小数，由小数点左侧的整数和右侧的小数组成。

### 复数

数学意义上的复数，由实部和虚部组成，并且使用 j 或者 J 表示虚部。当表示一个复数时，可以将其实部和虚部想加，如 2.67+12.5j

## 算数运算

在 Python 编程，使用算数运算符计算整数的和、差、积、商等：

![](https://dioimgstore.oss-cn-beijing.aliyuncs.com/images/%E7%AE%97%E6%95%B0%E8%BF%90%E7%AE%97%E7%AC%A6.png)

## 比较运算

比较运算，也称为关系运算，用于比较左右两侧的值得大小、相等等关系，如果结果为真，则返回 True，否则返回 False。

![](https://dioimgstore.oss-cn-beijing.aliyuncs.com/images/%E6%AF%94%E8%BE%83%E8%BF%90%E7%AE%97%E7%AC%A6.png)

# 布尔

## 基本类型

在 Python 中，布尔类型只有两个值：True（真） 和 False（假）。在编写代码的过程中，所有的对象都可以进行真值测试，其中，只有一下几种情况得到的值为 False：

- False 或 None
- 数字中的零，包括 0、0.0 或虚数 0
- 空虚列（包括字符串、列表、元组、字典）
- 自定义对象的实例，该对象的 \_\_bool\_\_ 方法返回的 False 或者 \_\_len\_\_ 方法返回的 0

## 逻辑运算

在 Python 编程中，逻辑元素包括与、或、非

![](https://dioimgstore.oss-cn-beijing.aliyuncs.com/images/%E9%80%BB%E8%BE%91%E8%BF%90%E7%AE%97%E7%AC%A6.png)

# 赋值运算

在 Python 编程中，使用一个等号（=）用于给变量或其他对象赋值，如：

``` python
x = 12
y = 23
z = x + y
```

由上可以衍生出一些特殊的赋值符号，如：

![](https://dioimgstore.oss-cn-beijing.aliyuncs.com/images/%E8%B5%8B%E5%80%BC%E8%BF%90%E7%AE%97%E7%AC%A6.png)

# 基本输入输出

## print()

print() 用于输出你想输出的任何内容。

## input()

input() 用于输入你想输入的任何内容。

