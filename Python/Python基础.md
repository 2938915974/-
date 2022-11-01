# Python 基础

[TOC]

## 变量与基础数据

### 基础数据类型定义

python有三个基本数据类型

- int
- float
- String

python 定义数据类型并不需要声明，程序会根据内容自动分配

```py
test01 = "aaaa"
test02 = 18
test03 = 1.37
print("%s , %d , %f" %(test01,test02,test03))
```

### 变量定义

$~~~~~$ 变量作为储存一切对象的东西，是代码中复用与可变的关键。
$~~~~~$ 变量的限制：中文，数字，英文，下划线；其中数字不能作为开头，并且不能与关键字冲突,变量的写法如下：

```python
[变量名] = [变量值]
```

$~~~~~$ python 中变量不需要声明变量类型，系统会自动去识别。
> 主要还是python的变量类型少，不过这样对运行效率并不友好

下面是 python 变量的几个使用例子

```py
var01 = 1
var02 = 1.245
var03 = -5.2
var04 = "dsdadad"
var05 = (5+3)/2 
```

### 字符串

String（字符串）有三种命名方式

```py
name = 'value'
name = "value"
name ="""value"""
```

前两种没什么大区别，第三种支持换行
前两种可以互相包裹，如

```py
str01 = 'aaaaaaa'
str02 = 'bbbbbbb'
str03 = """ccccccc
           ddddddd"""
str04 = '"asdaasdas"'
str05 = "'sdadadsas'"
print("三括号字符串输出结果："+str03)
```

这样name 的值就等于 "value" ，这个方案主要是避免传输数据时需要引号。

### 字符串占位符

1. 通过 `+` 号将变量插入到字符串中，该方法只适用于字符串变量。

    ```py
    str01 = 'aaaaaaa'
    print("QQQ"+str01+"AAA")
    ```

2. 使用格式化占位符 `%`，该方法适用于基础数据类型，格式化方式详见字符串格式化

   ```py
   str01 = 18
   str08 = "str01 = %d " %str01
   print(str01)
   ```

3. 变量占位符
   在字符串前面写一个f，然后在字符串之中使用：{变量名}，这样就会直接将变量的数据拉入，不用进行其他设置，如果需要精度控制就只有转换完再放变量
    > 大括号之中可以放算数表达式

    ```py
    var01 = 1
    var02 = 1.245
    str11 = f"str01 ={var01} ; str02 = {var02}"
    print(f"大括号占位符测试输出结果：{str11}")
    ```

### 字符串拼接

字符串之间可以通过 + 号来拼接，注意只能字符串之间拼接，不能和其他数据类型拼接

```py
str01 = 'aaaaaaa'
str02 = 'bbbbbbb'
str06 = str01+str02
str07 = "第一"+"第二"
print("字符串拼接输出结果："+str06 + str07)
```

### 字符串格式化

使用 %s（将变量转换成string）、%d（将变量转换成int）、%f(将变量转换成float) 在字符串之中进行占位。
然后在字符串后面加上一个 % 符号，将变量或数据写在后面，如果是多个就需要用括号括起来，并用逗号隔开
这样就会自动把数据依次镶嵌进去

```py
str01 = 'aaaaaaa'
str02 = 'bbbbbbb'
str08 = "str01 = %s " %str01
str09 = "str01 = %s ; str02 = %s" % (str01,str02)
print("字符串格式化输出结果："+str09)
```

### 字符串精度转换

$~~~~~$ 数据宽度和精度可以通过 `%[宽度],[精度][int/float]` 来设置（宽度小数点左边，精度小数点右边），这样做的目的是为了保证出现只保留多少位的需求，提高效率。
> 这个貌似只能用在字符串格式化之中
> 注意，int 类型没有精度设置

```py
var01 = 1
var02 = 1.245
str10 = "str01 =%d ; str02 = %3.2f" %(var01,var02)
print("数据宽度和精度控制输出结果 ：" +str09) 
```

### 数据类型转换

$~~~~~$ 该方法可以将基础数据进行互相转换，但是如字母无法被转换成数字一样，这个转换也是具有上下级关系的，int 和 float 都可以转换成 String ，int 能转 float ，float 却不一定能转 int 。这主要看内部的数据是什么，要是为 1 就都能转，要是字母 A 的话就只能是字符串，转换的关键在于数据，而不是数据类型。

转换的语法为

```py
[数据类型]([变量])
```

使用例子如下

```py
var01 = "15"
print(type(int(var01)))  # tpye(变量名) : 获取变量的数据类型
```

> type 方法用于检测变量的数据类型

### 算数运算符

python 的算术运算符有以下几个

- `+` ：加
- `-` ：减
- `/` ：除
- `//` ：整除（没有有值的小数，即9.0/2.0=4.0）
- `%` ：除法取余数
- `**` ：指数，即 A^B  = A**B

### 比较运算符

比较运算有以下几个
`> , < , == , != , >= , <=`
比较运算符返回结果为boolean 类型
> == 与 != 可用于字符串的比较

```py
test01 = 12 > 13
print("test01 :" +test01)
test02 = "adads"
test03 = "adads"
test04 = test02 == test03
print("test04:"+test04)
```

## 输入输出

### 命令行输出

python 通过 print 关键字可以在命令行中进入输出，语法为

```py
print([数据])
```

可输出的东西有很多，只要最后的结果是数据就行

```py
print("Hello, World!")
print(3+2)
print(4)
```

### 命令行输入

python 通过 input 关键字可以在命令行中进入输入，语法为

```py
[变量名] = input([提示语句])
```

单独使用input不会保存，需要使用变量来储存输入数据
input输入的数据一律视作字符串类型，类型转换要单独写代码

```py
name = input("input提示语句，请输入内容")
print("内容是："+name)
```

## 基础语句 if ; while ; for

三个语句都支持互相嵌套，同语句嵌套，注意前置空格就行

### if

if用于判断条件，条件成立就执行下面的语句，不成立就执行 else 之后的语句

```py
if [判断条件] :
    [条件成立时执行的语句01]
    [条件成立时执行的语句02]
    ……………………

elif [判断条件] :
    [条件成立时执行的语句01]
    [条件成立时执行的语句02]

else :
    [条件不成立时执行的语句01]
    [条件不成立时执行的语句02]
```

> elif 与 else 属于可选内容

elif 就等于 else if,
但是由于 python 语法的问题，要使用 else if 就只能：

```py
else :
    if [判断条件] :
```

非常麻烦，所以还是尽量采用elif
没有大括号如何判断执行内容？看空格，行前空格决定，python 许多东西由于不要限制符，只有用空格替代。

下面是使用例子

```py
test01 = 18
if test01  == 0 :
    print("test01等于0")
    print("test01数据值不对")
elif test01 == 2 :
    print("test01等于2")
else : 
    if (test01  == 1) :
        print("test01等于1")
    # 如例，这样使用 空格就多了，非常麻烦
    elif test01 > 10 :
        print("test01大于10")
```

### while

while 是一种循环语句，当满足条件时就执行内部代码，不满足就结束循环。
使用语法为

```py
while 【条件】 : 
    【条件成立时执行的语句01】
    【条件成立时执行的语句02】
    ………………………………………………………………
```

下面是使用例子

```python
number = 11
while number > 10 :
    number = input("请输入一个数:")
    # 由于输入数默认格式为 String 类型，所以需要进行字符转换。
    number = int(number)
    if number > 10 :
        print("你输入的数据大于10")
```

由于该语句是先判断在执行，所以要实现程序先执行再判断，最简单的方式就是设置一个 boolean 数据。
> boolean ：布尔类型语句，只有两种数据，True（真），False（假）

```py
flag = True 
while flag :
    number = input("请输入一个数")
    number = int(number)
    if number > 10 :
        input("你输入的数据大于10，循环结束")
        flag = False
    else :
        print("循环跳出条件未满足，请重新输入")
```

### for

python 的 for 循环只是一个遍历循环,将后面的变量或数据传入前一个数据，每个循环传一次
当后面的数据为字符串时，就会将其拆解为字符逐个传入，当为数组的时候，就会提遍历提取每个数据。

```py
for a in "abcdefg":
    print("for遍历循环")
    print(a)
```

> 与 C 语言相同， python 的 for 循环作用域只有 for 内部，即 for 内部定义的变量外部无法访问。

**`range`**

$~~~~~$为了实现和 C 语言 for 相同的效果，python 提供了一个 range 属性，该属性 写法为：`range(x,y)` 数据类型为 int ，会生成一个从 x 到 y 的数据（不包含 y）。
该属性也可以设置步长，这样就成了等差数列，如 `range(1,10,2)` ，设置步长为 2 ，这样生成的数就变成了 1，3，5，7，9

```py
for a in range(1,20):
    print("range遍历循环")
    print(a)

for a in range(1,20,2):
    print("range步长")
    print(a)
```

## 函数与方法

### 函数

$~~~~~$ 函数，是一段能够接受外部指定数据，用来实现特定功能的代码。
$~~~~~$ py通过 def 关键字定义函数，确定函数内容依旧是靠前置空格，函数格式为

```py
def [函数名](传入参数1,传入参数2,……):
    [函数内容]
    return [返回值]
```

$~~~~~$ 如果不设置返回值，实际上也有返回值，返回值为 none ，只是不显示出来而已。
$~~~~~$ 同样，函数内部定义的变量也是局部变量，只有函数内部的代码可以去调用。

下面是使用例子

```py
def test01(data1,data2):
    data3 = data1+data2
    return data3
```

函数之间也可以嵌套

```py
def test02(data1,data2):
    data3 = data1+data2
    return data3

def test03(data1,data2):
    data3 = data1+data2+test02(data1,data2)
    return data3

print ("函数嵌套输出结果"+test03(2,3))
```

### 函数的多返回值

python 要想有多个返回值，只需要用逗号隔开就行了。
这样接受返回值也是需要用两个变量来接受 如下代码

```py
def test01():
    return 1,2
x,y = test01()
print (x,y)
```

### 传参

函数接受的外部参数可以通过以下几个方式来使用

1. 位置，如果没有定义传入参数的变量名，那么就会按传入参数的顺序来使用

    ```py
    def test02(name,age):
        print("你的名字：%s , 你的年龄：%d" %(str(name),int(age)))
    test02("aaaa",18)
    ```

2. 变量名，如果定义了变量名，就会按变量名使用

    ```py
    def test02(name,age):
        print("你的名字：%s , 你的年龄：%d" %(str(name),int(age)))
    test02(name="bbbb",age=19)
    ```

3. 缺省值，函数定义外部参数时可以通过定义缺省值来避免无输入或者让参数变成可选参数，方式为 def test01(name,age=0)

    ```py
    def test03(name,age = 0):
        print("你的名字：%s , 你的年龄：%d" %(str(name),int(age)))
    test03(name = "aaa",)
    ```

4. 不定长参数位置传递，在传入时不知道会传多少参数时使用通过 *[变量名] 来定义，传入进来的所有数据都会被这个变量收集，然后合并为以一个元组。

    ```py
    def test04(*name):
        print(name)
    test04("aaa","bbb","ccc")
    ```

5. 不定长参数变量传递，即 key:value 键值对应的参数，通过 **[变量名]来定义，传入进来的所有变量都会被这个变量收集并整合成字典。

    ```py
    def test05(**name):
        print(name)
    test05(name="aaaa",test="bbbb")
    ```

ptyhon 可以将函数作为参数进行传递，但是此时传递的不是数据而是一种逻辑，下面是使用例子

```py
def test06(value):
    number = value(3,2)
    print(number)
def test07(x,y):
    return x+y
test06(test07)
```

### lambda 函数

函数除了基础的 def 定义，还有一种 lambda 定义法，这种函数可以无名称，定义方式为

```py
lambda 传入参数：函数体(代码)
```

> lambda 定义函数的执行代码只能有一行，无法分行
> 如果函数执行代码只用写一行并且不会重复使用的话可以用 lambda 函数。

下面是使用例子

```py
def test08(value):
    number = value(3,2)
    print(number)
test08(lambda x,y:x+y)
```

### 方法

$~~~~~$ python 中的方法类似于 java 的类，定义的关键字也是 `class`
方法就是一个储存多个函数的集合，声明方式为：

```py
class [方法名]:
    def [函数1]:
        [函数内容]
    def [函数2]:
        [函数内容]
    ………………………………
```

调用方法中的函数方式为：`[方法名].[函数名]([传参数据])`

```py
class test1:
    def test01(data1,data2):
        return data1+data2
    def test02(data1,data2):
        return data1-data2

print("方法测试："+test1.test02(3,1))
```

## 数据容器

python 没有数组的概念，但是有数据容器可以达成一样且更强大的效果

### list(列表)

$~~~~~$ list（列表） 在存储时可以看作一个可变数组，在使用时，具有比数据更加多的方法，写法为：

```py
[变量名] = [数据1,数据2,……]
# 或：
[变量名]=list(数据1,数据2，……)
```

当 list内要存储多组数据时，写法为:

```py
[变量名] = [{数据1,数据2,……},
            {数据1,数据2,……},
             ………………………………………]
```

同样，list 也支持嵌套，写法为：

```py
[变量名]=[[数据1],[数据2],……]
```

提取其中某个数据可以用 `变量名[i]` ，提取嵌套数据可用 `变量名[x][y]` 方式（当 i 为负数时，就是倒序取值）
> 注意，根据计算机语言结构，第一个数据的顺序是 0，而不是 1
> 如果想要提取一段连续的数据 `a[x:y]` ， 就会将第 x 个到第 y-1 个数据提取出来。

下面是使用例子

```py
list_test01 = [['a','b','c'],['d','e','f']]
print("镶嵌 list 第二组第二个："+list_test01[1][1])
print("倒序查询"+list_test01[1][-1])
print(list_test01[1][0:3])
```

**list 的几个常用方法：**

- `len(list)` : 列表元素个数
- `max(list)` : 返回列表元素最大值。
- `min(list)` : 返回列表元素最小值
- `List.append(obj)`:在列表末尾添加新的对象
- `list.count(obj)`:统计某个元素在列表中出现的次数
- `list.extend(seq)` : 在列表末尾一次性追加另一个序列中的多个值（用新列表扩展原来的列表）
- `list.index(obj)` : 从列表中找出某个值第一个匹配项的索引位置
- `list.insert(index, obj)` : 指定位置，将对象插入列表
- `list.pop([index=-1])` : 移除列表中的一个元素（默认最后一个元素），并且返回该元素的值
- `list.remove(obj)` : 移除列表中某个值的第一个匹配项
- `list.reverse()` :反向列表中元素
- `list.sort(cmp=None, key=None, reverse=False)`: 排序
  - 如果为指定，默认正序排列，数字>字母
  - cmp -- 可选参数, 如果指定了该参数会使用该参数的方法进行排序。
  - key -- 主要是用来进行比较的元素，只有一个参数，具体的函数的参数就是取自于可迭代对象中，指定可迭代对象中的一个元素来进行排序。
  - reverse -- 排序规则，reverse = True 降序， reverse = False 升序（默认）。

```py
#List.append(obj)
list1 = ['123', 'xyz', 'zara', 'abc']
list1.append('222')
print(list1)

# list.count(obj)
list1 = ['123', 'xyz', 'zara', 'abc','123']
print(list1.count('123'))

# list.extend(seq)
list1 = ['123', 'xyz', 'zara', 'abc']
list1.extend([456, 700, 200])
print(list1)

# list.index(obj)
list1 = ['123', 'xyz', 'zara', 'abc']
print(list1.index('123'))

# list.insert(index, obj)
list1 = ['123', 'xyz', 'zara', 'abc']
print()

# list.pop([index=-1])
list1 = ['123', 'xyz', 'zara', 'abc']
print(list1.pop(1))
print(list1)

#list.remove(obj) ，只能移除第一个，如果想要多个移除，可以用循环
list1 = ['123', 'xyz', 'zara', 'abc','123']
print(list1.remove('123'))
print(list1)

# list.reverse()
list1 = ['123', 'xyz', 'zara', 'abc','123']
print(list1.reverse())
print(list1)

# list.sort(cmp=None, key=None, reverse=False)
list1 = ['123', 'xyz', 'zara', 'abc','123']
list1.sort()
print(list1)
list1.sort(reverse=True)
print(list1)
```

### tuple(元组)

元组同列表一样可以存储多个数据，但元组定义完成后就不能修改了
元组通过小括号定义

```py
[变量名] = (数据1,数据2,……)
#或
[变量名] = tuple(数据1,数据2,……)
```

$~~~~~$ 如果括号内只有一个数据，那只会视作普通元素，如果非要将其变成元组，要在后面加个逗号 ,
$~~~~~$ 元组也可以进行镶嵌，具体方法就不说了，和列表一样。
$~~~~~$ 读取元组的数据方法和列表也一样，即 [元组名].[i]

**tuple 的几个常用方法：**

- `tuple.index(obj)` : 查某个数据，如果数据存在就返回对应的位置
- `tuple.count(obj)` : 统计某个数据出现的次数。
- `len(tuple)` : 统计元组中元素的个数。

```py
tuple1 = ['123', 'xyz', 'zara', 'abc','123']

#tuple.index(obj)
print (tuple1.index('xyz'))

#tuple.count(obj)
print (tuple1.count('123'))

#len(tuple)
print (len(tuple1))
```

### String(字符串)

String 字符串同样也是以一个数据容器

**字符串可以使用以下几个方法：**

- `String.index(str)` : 查询数据在字符串中对应位置
- `String.replace(str1，str2)` : 将字符串内的所有 str1 都替换成 str2 然后返回（注意原字符串不变）
- `String.split(str)` : 将根据定义的字符串分割该字符串，并将分割后的数据以列表方式返回（分隔符会被删除）
- `String.strip(str)` ：去除字符串前后指定的字符串并返回（原字符串不变），如果值为空，就只会去除空格。
- `String.count(str)` : 统计字符串中指定数据出现的次数。
- `len(str)` ：统计字符串的长度

```py
string1 = "abcdefg"

# String.index(str)
print(string1.index("c"))

# String.replace(str1，str2)
print(string1.replace("a","1"))

# String.split(str)
print(string1.split("e"))

# String.strip(str)
print(string1.strip("a"))

# String.count(str)
print(string1.count("c"))

# len(str)
print(len(string1))
```

### set(集合)

$~~~~~$ 集合 set 属性与列表一样，但是集合不允许出现重复数据，如果发现输入数据是重复的，就会无视掉。
集合通过大括号定义，定义方式为：

```py
[变量名] = {数据1,数据2,……} 
# 或
[变量名] = set{数据1,数据2,……}
```

**set 可以使用以下几个方法：**

- `set.add(obj)` :  在集合末尾添加数据
- `set.remove(obj)` : 删除数据
- `set.pop()` : 随机取出一个元素，同时集合内的该元素会被删除。
- `set.clear()` : 清空集合
- `set1.difference(set2)` : 取出 集合1 和 集合2 的差集（1 中有而 2 中没有的数据）
- `set1.difference_update(set2)` : 消除 集合1 中和 集合2 的并集（1 和 2 共有的）
- `set1.union(set2)` : 将两个集合合并成一个新集合，原集合不变。
- `len(set)` : 返回集合内数据的个数

```py
set01 = {"111","222"}

# set.add(obj)
set01.add("333")
set01.add("222")
print(set01)

# set.remove(obj)
set01.remove("333")
print(set01)

# set.pop()
print(set01.pop())
print(set01)

# set.clear()
set01.clear()
print(set01)

# set1.difference(set2)
set02 = {"111","222","333"}
set03 = {"333"}
print(set02.difference(set03))

# set1.difference_update(set2)
set02.difference_update(set03)
print(set02)

# set1.union(set2)
set04 = {"111","222","333"}
set05 = {"333","666"}
set06 = set04.union(set05)
print(set06)

# len(set)
set07 = {"111","222","333"}
print(len(set07))
```

### dict(字典)

$~~~~~$ python 中字典的定义就是 key:value 键值对应的储存容器
$~~~~~$ 字典通过 {} 定义，但是内部的数据是键值写法，这是程序区分字典与集合的方式，定义方式为 ：

```py
[变量名] = {"key1":"value1" , "key2":"value2" , ……}
# 下面定义的是一个空字典
[变量名] = dict()
```

字典数据的写法与json 的 key:value 写法一样，即

```json
{
    "name" : "aaa",
    "mail" : "2222",
    "XXX" : "XXX"
}
```

$~~~~~$ 字典内部 key 的数据类型为 int，float，string ； value 的数据类型为 obj。
$~~~~~$ 字典不允许出现重复的 key 值，如果出现会视为替换。
$~~~~~$ 字典可以通过 `[变量名][key]` 来获取对应的 value 值。
$~~~~~$ 如果是字典嵌套字典，可以通过 `[变量名][一级key][二级key][X级key]` 来获取所需数据。
$~~~~~$ 字典增加数据可以通过 `[变量名][key] = [value]` 的方式来增加，如果 key 值重复了，就视作替换。

**dict 可以使用以下几个方法：**

- `[dict].pop([key])` : 删除该 key 键值对的数据，该过程会返回被删除的 value 值。
  > key:value 这个整体就被叫做键值对。
- `[dict].clear()` : 清空字典
- `[dict].keys()` : 获取所有 key 值，返回值为 list
- `len([dict])` : 获取字典长度。

下面是使用例子

```py
dict01 = {"001":"aaaaa","002":"bbbbb"}
print(dict01["001"])
dict01 = {
        "001":{"001":"aaaaa",
                "002":"bbbbb"
                },
        "002":{"001":"CCCCC",
                "002":"DDDDD"
                }
        }
print(dict01["001"]["001"])

# 增加
dict01["003"] = "ccccc"
print(dict01)

# [dict].pop([key])
dict01.pop("001")
print(dict01)

# [dict].clear()
dict01.clear()
print(dict01)

# [dict].keys()
dict01 = {"001":"aaaaa","002":"bbbbb"}
print(dict01.keys())

# len([dict])
print(len(dict01))
```

如果要想遍历字典的数据，可以通过两个办法：

1.通过获取 key 值，然后 `[变量名][key]` 输出。
2. 直接对字典 for 遍历，出来的结果就是 key 值，然后通过 `[变量名][key]` 输出。

### 切片

切片不是数据容器，而是数据容器的一种操作。
切片即从一组数据中一次性取出几个数据。
切片的书写规则为：

```py
[int1:int2:int3]
```

- int1与int2决定取值范围，范围为int1到int2-1。
- int3决定步长，即每个取值数的间距，间距为int3-1。
- 若int1与int2未定义，则视作从头到尾，若int3未定义，则视作无间隔。

```py
list1 = ['123', 'xyz', 'zara', 'abc','123']
print(list1[0:2])
print(list1[0:4:2])
```

### 数据容器总结

1. 数据容器都支持 for 遍历循环，
2. 列表，元组，字符串支持 whlie 循环。
3. 数据容器都支持len（获取长度），max（获取最大值），min（获取最小值）
4. 数据容器都可以转换成 list， str，tuple，set
    > 转换方式为 list([变量名])，其他几个也是这样
5. 都可以通过sorted 来排序，排序方式为     sorted([变量名],reverse = True/false)

   ```py
   dict01 = {"001":"aaaaa","002":"bbbbb"}
   sorted(dict01)
   print(dict01)
   ```

6. 所有对象都可以使用 `del` 关键字，其中自然也包含数据容器
   使用方法为

   ```py
    del(obj)
    ```

    下面是使用例子

    ```py
    list1 = ['123', 'xyz', 'zara', 'abc','123']
    del list1
    print(list1)
    ```

## 文件操作

### 打开文件

python 使用 open 函数打开文件，如果文件不存在，则创建一个文件。写法为：

```py
open([文件名],[打开方式],[编码格式（可选）])
```

打开方式有以下三种：

1. `r` : 只读（该方式无法创建文件）
2. `w` : 写入
3. `a` : 追加写入

不管时写入还是读取的方法，只有设置了对应的打开方式才能使用

### 读取文件

读取文件有以下几个操作：

- `[file].read(int)` : 读取文件中的字符，如果未定义数量则全读。
- `[file].readline(int)` : 读取文件中每行的数据，如果未定义数量则全读

```py
file01 = open("C:/test/test01.txt","w",encoding="UTF-8")
file01.close()


file02 = open("C:/test/test01.txt","r",encoding="UTF-8")
a = file02.read()
b= file02.readline()
print(a)
```

$~~~~~$ 注意，两个方法共用指针，即第一个方法读了多少，然后会在那个位置生成一个指针，另一个方法就只会从指针位置开始读。
$~~~~~$ 读取支持 for 遍历操作。
$~~~~~$ 如果完成文件使用，需用 `[变量名].close()` 关闭占用。
$~~~~~$ python 可以通过 with open 语法自动实现文件执行完毕自动关闭文件，这个语法实际上就是生成一个函数，函数自动添加了 close()
语法:

```py
with open([文件名],[打开方式],[编码格式（可选）]) as [变量名] :
    [方法体………………]
```

```py
with open("C:/test/test01.txt","r",encoding="UTF-8") as file02:
    a = file02.read()
    b= file02.readline()
    print(a)
```

### 写入文件

文件写入需要通过以下几个方法：

- `[file].write([数据])` : 在文件中写入数据
- `[file].flush()` : 刷新文件内容

```py
with open("C:/test/test01.txt","w",encoding="UTF-8") as file02:
    file02.write("hello world")
    file02.flush()

file02 = open("C:/test/test01.txt","r",encoding="UTF-8")
print(file02.read())
file01.close()
```

直接调用 write 时，内容并未写入文件，而是存入内存中，当调用 flush 时才会真正写入

### 追加写入

追加写入的方法与写入一样，只是写入方式是追加写入而已，因此不做详细介绍了。

## 异常

$~~~~~$ 在运行时总是会出现由于传入参数不规范或者运行代码不规范导致的 bug ，这些东西统一被称作异常
> 这个是 python 的定义，实际上大部分编程对于这个问题的定义分两个：1. 错误 2. 异常

在 python 中，异常捕获的语法为：

```py
try:
    [可能发生错误的代码]
except:
    [如果出现异常执行的代码]
```

下面是使用例子

```py
try:
    int01 = input("请输入数字")
    print(int(int01))
except:
    print("你输入的数据不是数字")
```

$~~~~~$ 该方法只能做到出现异常时执行代码，但是无法确定异常种类，也无法输出异常状况，要想实现这个功能，需要使用指定异常的捕获代码，代码语法为：

```py
try:
    [可能发生错误的代码]
except [异常名] as [变量名]:
    [如果出现异常执行的代码]
```

代码块会将指定的异常捕获，并将异常的相关数据传入定义的变量中，要想知道异常输出这个变量就行了。
如果是多个异常的话 异常名的写法就是 `(异常1,异常2,……)` ，具体异常名请百度。
下面是使用例子

```py
try:
    print(name)
except (NameError,ZeroDivisionError) as e:
    print(e)
```

如果需要捕获所有的异常话，异常名就是 `Exception` 。

```py
try:
    print(name)
except Exception as e:
    print(e)
```

异常处理 try 与 except ，还有 else 和 finally 关键字，其中 else 关键字确定没有异常时执行的代码内容，写法为

```py
try:
    [可能发生错误的代码]
except [异常名] as [变量名]:
    [如果出现异常执行的代码]
else:
    [没有异常时执行的代码]
```

由于这个方法看不懂作用，所以不做描述，主要介绍 finally 关键字。
finally 直译为最终，作用也一样，定义不会是否发生异常，最终都会执行的代码，写法为：

```py
try:
    [可能发生错误的代码]
except [异常名] as [变量名]:
    [如果出现异常执行的代码]
else:
    [没有异常时执行的代码]
finally:
    [无论是否有异常都会执行的代码]
```

下面是使用例子

```py
try:
    print(name)
except Exception as e:
    print(e)
finally:
    print("[无论是否有异常都会执行的代码]")
```

在整个异常代码中，关键字 else 和 finally 都是非必要的，根据情况添加。

## 模块

python 模块实际上就是一个py文件，里面包含了类，变量，函数
导入了模块后就可以使用模块中的函数或者其他可使用的代码了，导入语法为

```py
import [模块名|类|变量|函数]
# 或
import [模块名|类|变量|函数] as [别名]
# 或
from [模块名] import [类|变量|函数|*] as [别名]
```

$~~~~~$ 上述的 `[类|变量|函数]` 实际上是按等级来排的，如果要使用模块中的函数，就需要 模块.类.函数
$~~~~~$ 未定义别名的话，使用方法就需要写方法的全路径，如 模块定义的是 `import test01.test02` 那么使用 test02 方法中的 sum 函数的代码就是 `test01.test02.sum(2,3)` 。
$~~~~~$ 但是如果使用的是 `from …… import ……` 的话，使用函数的代码就只用写 import 后面的，如 `from test01 import test02` ，使用 test02 方法中的 sum 函数的代码就是 `test02.sum(2,3)` 。

```py
# 导入官方包
import time
time.sleep(50)

# 获取模块中的某个类
from time import sleep
sleep(50)

# 别名
import time as T
T.sleep(50)
```

$~~~~~$ 如果要使用自己定义的模块，也很简单，只要保证模块与运行的 py 文件在同一目录同级下，就可以直接通过 `import [文件名]` 来引入模块，如果只想要使用模块中的某个函数或者方法参考上面的教程，都一样。
$~~~~~$ python中可以通过 `__name__` 关键字来确认运行文件的名称，使用实例如: if 判断文件名，如果是该文件被调用了，文件名就会是调用文件的文件名，这样就可以实现本文件才运行某些代码，被调用就不运行这些代码。

如，我们在 py 运行文件的同目录下，创建一个 test01.py 文件，在文件中输入以下内容

```py
def A01():
    if __name__ == '__main__':
        print("本文件直接运行才看到到这段文字")
    print("调用了A01方法")
```

然后在运行文件中引用并使用该函数

```py
import test01
test01.A01()
```

### 包

$~~~~~$ 包实际上就是一个文件夹，这个文件夹中有一堆 py 文件
$~~~~~$ 导入时通过与导类一样，就是多了一级包路径而言
$~~~~~$ 由于大型包的文件过多，因此 py 专门在包中设置了一个 py 文件来管理包，这个文件的文件名固定，为：`__init__.py`

该文件中只写管理包的方法，常用以下几个：

- `__all__ = [模块名]` :  该方法用于控制哪些模块可以被使用（模块中也可以使用这个代码）
    如果要规定多个可用，就是 `__all__ = [模块1,模块2,……]` ，注意，该方法只对 from 的方法有效，对直接 import 的方法无效。

    如我们在运行文件目录下创建一个名为 mypackage 的文件夹，在文件夹中创建两个文件，分别命名为 `use01.py` 与 `use02.py` ，并在文件中输入以下代码

    ```py
    # 这是 use01 的代码
    def test001():
        print("输出1")

    # 这是 use02 的代码
    def test002():
        print("输出2")
    ```

    然后再在文件夹中创建一个 `__init__.py` 的文件，并在文件中输入以下代码

    ```py
    __all__=["use02"]
    ```

    然后，我们在运行文件中导入这个包，并分别调用 test001 ，test002

    ```py
    from mypackage import *
    use01.test001
    use02.test002
    ```

    这是我们会发现 test001 报错，原因就是我们在包管理文件中没有设置 use01 可用。

### 第三方包（待补充）

python 通过自带的 pip 包管理器下载第三方包
使用方式为在命令提示符中输入：`pip install [包名]`
由于默认的路径是国外的，速度较慢，可以通过 `pip install -i [url] [包名]` 来指定下载路径。

## json 字符串处理

json字符串是目前最流行的数据传输格式，采用键值对应的方式来确认变量属性。
python 对json 字符的处理有以下几个方法：

- `json.dumps([数据])` : 将 python 数据转换成 json 字符串
- `josn.loads([数据])` : 将 json 数据转换成 python 字典或者数组。

## 类，对象，方法

$~~~~~$ 对象数据大部分都是键值对应的形式存在的，如果使用字典来存放，没有约束，也很麻烦。python 中通过 class 关键字来设置，称为类，写法为：

```py
class [类名] :
    [name1] = [value1]
    [name2] = [value2]
    ………………………………………………
```

$~~~~~$ 这种方式不只可以约束数据，也可以在没有数据时使用默认值，且类中属性的存在是持久的，直到程序结束或者被清除才会消失
$~~~~~$ 类并不需要设置传入参数，内部属性，方法都可以直接调用,但类通常不会直接使用，为了复用，我们会将在变量中创建类，通过 `[变量名] = [类名]` ，这个过程我们称为创建对象。
$~~~~~$ 类中的属性只能单独进行输出，无法直接输出类
> 其实只是将概念切换到面向对象，把方法改名为类，把函数叫做方法。

下面是使用例子

```py
class person:
    name = None
    age = None
class01 = person
class01.name = "aaa"
class01.age = 18
print(class01.name)
```

$~~~~~$ 与之前 class 定义的方法一样，类中也可以创建函数，但是我们把这个函数叫做成员方法
> 实际上只是名字不一样了，所以具体流程就不详述了。

$~~~~~$ 但是这个有一个新的关键字，传参关键字 self ，这个关键字定义的变量可以被忽略。
> 如我们传入了三个参数，但是只定义了两个参数，那么第一个参数就会被存入 self，但是定义了三个参数的话，self 就不会存储。
> self 实际上是这个对象的内存地址，如果在方法中，就是方法的内存地址，之所以类可以创建多个对象就是内存地址不一样。

$~~~~~$ 另外，如果类被声明为了对象，那么类中也会存在传参数据，不过是 self 关键字，而一旦有了传参数据，括号就不能省，即原来调用类中的方法为 `class.fuction()` ，类变成了对象就是 `class().fuction()` 。

下面是使用例子

```py
class AD:
    def test01(self):
        print("输出结果为")

class02 = AD
class02().test01()
```

$~~~~~$ 如上我们说的，类被创建为了对象就会出现默认的传参参数，那么类自然可以自己指定传参参数，该参数会被传入到构造方法中，构造方法是直接服务于类的方法，默认是隐藏的，并且内部没有代码。
$~~~~~$ 但是如果我们想要提高效率，类中有多个方法，都要实现，那么可以直接对类传参，通过构造方法去分发参数。
> 为了避免构造方法过于臃肿，因此该方法中的代码应当只负责传参与返回。

构造方法是一个名为 `__init__` 的方法，如果我们创建了这个方法程序就不会去创建构造方法，以这个方法为构造方法，写法为

```py
def __int__(self,[传参1],[传参2],……):
    [方法体]
```

> 为什么必须要 self ，因为 python 有个非常脑血栓的问题，就算你不声明 self ，系统还会自动生成self ，但这不是重点，重点是这个 self 会挤掉你的第一个属性，而且在传参的时候这个属性虽然不用传，但是会被默认传输，这样你本来设置了两个属性，传参也设置的两个，但是会报错告诉你传了三个，就是因为 self 被默认传输了，但是你的第一个属性被挤掉了，第一个属性的参数就变成多余的了，所以会报错。
> 但是写上去就没事了，不懂什么操作
> 还有，类只要被声明对象了，那么这个对象包括其中的所有方法都有一个 self ，而且都会触发这个问题，所以**写的时候一定要加上**。
> 哪怕你没有传入参数也要加上！！！

下面是使用例子

```py
class CS:
    def __init__(self,name,age):
        CS.name = name
        CS.age = age
        
    name = None
    age = None
CS01 = CS
CS01("111",18)
print("name = "+ str(CS01.name)+", age = "+str(CS01.age))
```

$~~~~~$ 上面讲的无法直接输出类，python 也考虑到了，所以设置了一个 `__str__` 方法，直接输出类的话就会输出这个方法的返回值，因此我们可以通过该方法实现输出字符串，即 toString 方法。

```py
class CS:
    def __init__(self,name,age):
        CS.name = name
        CS.age = age
    def __str__(self):
        return "name = "+CS.name+" , age = "+CS.age
    name = None
    age = None
CS01 = CS
CS01("111",18)
print("name = "+ str(CS01.name)+", age = "+str(CS01.age))
```

另外对象还又以下几个内置方法

- `__lt__()` : 该方法在对象之间使用小于符号比较时生效。
- `__le__()` : 该方法在对象之间使用 >= , <= 符号比较时生效。
- `__eq__()` : 该方法在对象之间使用 == 符号比较时生效。

这里只说了生效，因为具体执行结果是什么，是由这些方法的返回值确定的。
由于这些方法与普通方法只有调用与概念不一样，所以不做详细叙说。

## 封装继承多态

### 封装

$~~~~~$ 封装的定义很简单，外部可以直接接触的就是开放的，外部无法直接接触的就是封装的。
$~~~~~$ 封装的方法与变量只有该类中的其他方法与属性才能去接触，等同于你的家只有有钥匙的人才能进。
$~~~~~$ 封装的使用非常简单，在方法或者变量前加 `__` 就行了，如之前见到的对象方法 `__init__` 这些就是被封装了。

### 继承

$~~~~~$ 继承的概念一样简单，这个类如果继承了另一个类，那么另一个类的方法，变量都会在这个类中存在，等同于你在这个类中敲了这些代码，这个类叫做子类，它继承的类叫做父类。
$~~~~~$ 如果这个类中与父类有相同的方法名与传入参数，那么父类的方法就不会被实现，调用这个方法只会是子类的方法，继承的写法为

```py
class [子类](父类):
    [类体]
```

下面是使用例子

```py
class father:
    def test01(self):
        print("父类的方法11111")
    def test02(self):
        print("父类的方法22222")

class son(father):
    def test01(self):
        print("子类的方法11111")

class01 = son
class01().test01()
class01().test02()
```

### 数据限制

由于面向对象的概念需要固定数据类型，所以python 引入了数据类型的定义，写法为

```py
[变量名]: [数据类型] = [value]
```

> 冒号不能省。
> 该方法适用于数据容器与类，还有方法，方法与类的数据类型就是方法/类名

下面是使用例子

```py
def test01():
    print("aaaaa")

int01: int = 18
Str01: str = "1111"
list01: list = ["1","2","3"]
test1 : test01()
```

当然，像数据容器和方法都有传入数据类型属性，这点我们也能定义，定义语句如下：

```py
[变量名]: list[obj]
[变量名]: set[obj]
[变量名]: tuple[obj1]
[变量名]: dict[str/float/int,obj] 
```

下面是使用例子

```py
list02: list[int] = [1,2,3]
set02: set[int] = {1,2,3}
turple: tuple[int,str]=(1,"asasa")
dict01: dict[int,str]={1:"aaa",2:"bbb"}
```

在设置传入参数时，也可以这样设置。
函数返回值时也可以指定返回值类型，不过写法不一样，为

```py
def [变量名]([传入参数]) -> [返回值数据类型] :
```

下面是使用例子

```py
def test01(name:str,age: int ) -> str:
    print("名字为"+name+" , 年龄为"+str(age))
test01("aaa",18)
```

当我们的数据类型不止一个时（这通常在函数与数据容器中发生），我们就需要使用 Union 关键定义，写法如下

```py
[变量名]:[obj][obj1,obj2,……] = [value]
```

$~~~~~$ 将原来传参的指定值变成 Union[………………] 就行了，该关键字适用于大部分可以指定数据类型的地方，使用方法与单数据类型限定一样。
> $~~~~~$ 该类型不能作为其他类型的子类型限制，如数据容器中就不能使用，但数据容器中本来就可以通过逗号隔开，所以无所谓
> $~~~~~$ 使用该关键字必须要导包 `from ctypes import Union` ，当然大部分智能编辑器都能自动导包。

下面是使用例子

```py
from ctypes import Union

listA: list[int ,str]
listA = [1, 123, "aaa"]
print(listA)
```

### 多态

python 没有接口，所以多态的概念非常简单，几个类共同继承一个类，这就是多态
多态用于减少代码量，限定代码规范。

下面是使用例子

```py
class father:
    def test01(self):
        print("父类的方法11111")
    def test02(self):
        print("父类的方法22222")

class son1(father):
    def test01(self):
        print("子类的方法AAAAA")

class son2(father):
    def test01(self):
        print("子类的方法BBBBB")

s1 = son1
s2 = son2
```
