---
language: python3
contributors:
    - ["Louie Dinh", "http://pythonpracticeprojects.com"]
    - ["Steven Basart", "http://github.com/xksteven"]
    - ["Andre Polykanine", "https://github.com/Oire"]
    - ["Zachary Ferguson", "http://github.com/zfergus2"]
    - ["evuez", "http://github.com/evuez"]
translators:
    - ["Geoff Liu", "http://geoffliu.me"]
    - ["Shalk", "https://github.com/shalk"]
filename: learnpython3-cn.py
lang: zh-cn
---

Python是由吉多·范罗苏姆(Guido Van Rossum)在90年代早期设计。它是如今最常用的编程
语言之一。它的语法简洁且优美，几乎就是可执行的伪代码。

欢迎大家斧正。英文版原作Louie Dinh [@louiedinh](http://twitter.com/louiedinh)
或着Email louiedinh [at] [谷歌的信箱服务]。中文翻译Geoff Liu。

注意：这篇教程是特别为Python3写的。如果你想学旧版Python2，有另一篇[教程](http://learnxinyminutes.com/docs/python/).

```python

# 用井字符开头的是单行注释

""" 多行字符串用三个引号
    包裹，也常被用作多
    行注释
"""

####################################################
## 1. 原始数据类型和运算符
####################################################

# 整数
3  # => 3

# 算术没有什么出乎意料的
1 + 1   # => 2
8 - 1   # => 7
10 * 2  # => 20

# 但是除法例外，会默认返回浮点数或者实数
35 / 5  # => 7.0

# 整除运算的结果都是向下取整，无论正负
5 // 3      # => 1
5.0 // 3.0  # => 1.0 # 浮点数也可以
-5 // 3     # => -2
-5.0 // 3.0 # => -2.0

# 浮点数的运算结果也是浮点数
3 * 2.0  # => 6.0

# 求模
7 % 3  # => 1

# 乘方(x**y,x的y次方)
2**4  # => 16

# 用括号决定优先级
(1 + 3) * 2  # => 8

# 布尔值 (注: 第一个字母大写，其他小写)
True
False

# 用not取非
not True   # => False
not False  # => True

# 逻辑运算符
# 注意 and 和 or 都是小写
True and False  # => False
False or True   # => True

# 对整数使用逻辑运算
0 and 2     # => 0
-5 or 0     # => -5
0 == False  # => True
2 == True   # => False
1 == True   # => True

# == 判断相等
1 == 1  # => True
2 == 1  # => False

# != 判断不等
1 != 1  # => False
2 != 1  # => True

# 更多比较符号
1 < 10  # => True
1 > 10  # => False
2 <= 2  # => True
2 >= 2  # => True

# 大小比较可以连起来！
1 < 2 < 3  # => True
2 < 3 < 2  # => False

# (is 和 ==) is 检查两个值是否引用同一个对象, 但 == 检查
# 两个对象是否拥有相同的值
a = [1, 2, 3, 4]  # a 指向一个新列表, [1, 2, 3, 4]
b = a             # b 指向 a 所指向的列表
b is a            # => True, a 和 b 指向同一个对象
b == a            # => True, a 和 b 的对象相等
b = [1, 2, 3, 4]  # b 指向一个新列表, [1, 2, 3, 4]
b is a            # => False, a 和 b 指向的不是同一个列表
b == a            # => True, a 和 b 的对象相等

# 字符串,用单引号或双引号来创建
"这是个字符串"
'这也是个字符串'

# 字符串可以用加号连接！也可以不用。
"Hello " + "world!"  # => "Hello world!"
# 字符串可以不用加号连接
"Hello " "world!"    # => "Hello world!"

# 字符串可以被当作字符列表
"This is a string"[0]  # => 'T'

# 你可以查询字符串的长度
len("This is a string")  # => 16

# 用.format来格式化字符串
"{} can be {}".format("Strings", "interpolated")  # => "Strings can be interpolated"

# 可以重复参数以节省时间
"{0} be nimble, {0} be quick, {0} jump over the {1}".format("Jack", "candle stick")
# => "Jack be nimble, Jack be quick, Jack jump over the candle stick"

# 如果不想数参数，可以用关键字
"{name} wants to eat {food}".format(name="Bob", food="lasagna") #=> "Bob wants to eat lasagna"

# 如果你的Python3程序也要在Python2.5以下环境运行，
# 也可以用老式的格式化语法
"%s can be %s the %s way" % ("Strings", "interpolated", "old")  # => "Strings can be interpolated the old way"


# None是一个对象
None  # => None

# 当与None进行比较时不要用 ==，
# 要用is。is是用来比较两个变量是否指向同一个对象。
"etc" is None  # => False
None is None   # => True

# None，0，空字符串，空列表，空字典都算是False
# 所有其他值都是True
bool(0)   # => False
bool("")  # => False
bool([])  # => False
bool({})  # => False


####################################################
## 2. 变量和集合
####################################################

# print是内置的打印函数
print("I'm Python. Nice to meet you!")  # => I'm Python. Nice to meet you!

# 默认情况，print函数在打印结束的时候换行。
# 使用可选参数 end 可以改变结束字符。
print("Hello, World", end="!")  # => Hello, World!

# 从终端获得输入数据
input_string_var = input("Enter some data: ") # Returns the data as a string
# 注：在Python的早期版本， input() 方法原来叫做 raw_input()

# 在给变量赋值前不用提前声明
# 传统的变量命名是小写，用下划线分隔单词
some_var = 5
some_var  # => 5

# 访问未赋值的变量会抛出异常
# 参考流程控制一段来学习异常处理
some_unknown_var  # 抛出NameError

# if 可以用做表达式
# 等价于C语言中的 ?: 三元操作符
"yahoo!" if 3 > 2 else 2  # => "yahoo!"

# 用列表(list)储存序列
li = []
# 创建列表时也可以同时赋给元素
other_li = [4, 5, 6]

# 用append在列表最后追加元素
li.append(1)    # li现在是[1]
li.append(2)    # li现在是[1, 2]
li.append(4)    # li现在是[1, 2, 4]
li.append(3)    # li现在是[1, 2, 4, 3]
# 用pop从列表尾部删除
li.pop()        # => 3 且li现在是[1, 2, 4]
# 把3再放回去
li.append(3)    # li变回[1, 2, 4, 3]

# 列表存取跟数组一样
li[0]  # => 1
# 取出最后一个元素
li[-1]  # => 3

# 越界存取会造成IndexError
li[4]  # 抛出IndexError

# 列表有切片语法
# （类似于数学中的开闭区间。）
li[1:3]  # => [2, 4]
# 省略开头
li[2:]  # => [4, 3]
# 省略结尾
li[:3]  # => [1, 2, 4]
# 间隔一个选一个
li[::2]   # =>[1, 4]
# 返回一个倒排列表
li[::-1]   # => [3, 4, 2, 1]
# 可以下面三个参数的任何组合来构建高级切片
# li[start:end:step]

# 通过切片完成一层深拷贝
li2 = li[:]  # => li2 = [1, 2, 4, 3]  但 (li2 is li) 会返回False

# 用del删除任何一个元素
del li[2]   # li is now [1, 2, 3]

# 删除首次出现的值
li.remove(2)  # li 现在是 [1, 3]
li.remove(2)  # 如果2不是列表中的值，会产生异常 ValueError 

# 在特定的索引插入一个元素
li.insert(1, 2)  # li is now [1, 2, 3] again

# 返回首次和参数匹配的元素的索引 
li.index(2)  # => 1
li.index(4)  # 如果4不是元素列表中的值，会产生异常ValueError

# 列表可以相加
# 注意：li和other_li的值都不变
li + other_li  # => [1, 2, 3, 4, 5, 6]

# 用extend()拼接列表
li.extend(other_li)   # li现在是[1, 2, 3, 4, 5, 6]

# 用in测试列表是否包含值
1 in li  # => True

# 用len取列表长度
len(li)  # => 6


# 元组是不可改变的序列
tup = (1, 2, 3)
tup[0]   # => 1
tup[0] = 3  # 抛出TypeError

# 注意 长度为1的元组必须要结尾有一个逗号，其他长度的
#　元组包括长度为０的元组，不用结尾加逗号
type((1))   # => <class 'int'>
type((1,))  # => <class 'tuple'>
type(())    # => <class 'tuple'>

# 列表的操作，元组大部分也可以
len(tup)         # => 3
tup + (4, 5, 6)  # => (1, 2, 3, 4, 5, 6)
tup[:2]          # => (1, 2)
2 in tup         # => True

# 可以把元组(或列表)解包，赋值给变量
a, b, c = (1, 2, 3)     # 现在a是1，b是2，c是3
# 也可以进行扩展解包 
a, *b, c = (1, 2, 3, 4)  # a 是 1, b 是 [2, 3] 还有 c 是 4
# 元组周围的括号是可以省略的
d, e, f = 4, 5, 6
# 交换两个变量的值就这么简单
e, d = d, e     # 现在d是5，e是4


# 用字典表达映射关系
empty_dict = {}
# 初始化的字典
filled_dict = {"one": 1, "two": 2, "three": 3}

# 字典的键必须是不可变类型. 这可以保证 
# 键可以转换成哈希常量值，用于快速查询。
# 不可变类型包括 ints, floats, strings, tuples.
invalid_dict = {[1,2,3]: "123"}  # => 抛出TypeError: unhashable type: 'list'
valid_dict = {(1,2,3):[1,2,3]}   # 尽管如此,字典的值可以是任意类型。

# 用[]取值
filled_dict["one"]  # => 1

# 用keys获得所有的键。因为keys返回一个可迭代对象，所以在这里把结果包在list里。
# 我们下面会详细介绍可迭代。
# 注意：字典键的顺序是不定的，你得到的结果可能和以下不同。
list(filled_dict.keys())  # => ["three", "two", "one"]


# 用values获得所有的值。
# 跟keys一样，要用list包起来，顺序也可能不同。
list(filled_dict.values())   # => [3, 2, 1]


# 用in测试一个字典是否包含某个键
"one" in filled_dict  # => True
1 in filled_dict      # => False

# 访问不存在的键会抛出KeyError
filled_dict["four"]   # KeyError

# 用get来避免KeyError
filled_dict.get("one")    # => 1
filled_dict.get("four")   # => None
# 当键不存在的时候get方法可以返回默认值
filled_dict.get("one", 4)   # => 1
filled_dict.get("four", 4)  # => 4

# setdefault方法只有当键不存在的时候插入新值
filled_dict.setdefault("five", 5)  # filled_dict["five"]设为5
filled_dict.setdefault("five", 6)  # filled_dict["five"]还是5

# 字典增加元素
filled_dict.update({"four":4})  # => {"one": 1, "two": 2, "three": 3, "four": 4}
filled_dict["four"] = 4  # 另一种增加字典元素的方法

# 用del删除字典键
del filled_dict["one"]  # 从filled_dict中把one删除
# 从 Python 3.5 开始 你也可以使用追加解包选项(pep-0448)
{'a': 1, **{'b': 2}}  # => {'a': 1, 'b': 2}
{'a': 1, **{'a': 2}}  # => {'a': 2}



# 用set表达集合
empty_set = set()
# 初始化一个集合，语法跟字典相似。
some_set = {1, 1, 2, 2, 3, 4}   # some_set现在是{1, 2, 3, 4}

# 和字典的键相似，set的元素也必须是不可变的
invalid_set = {[1],1}
valid_set = {(1,),1}

# 可以把集合赋值于变量
filled_set = some_set

# 为集合添加元素
filled_set.add(5)   # filled_set现在是{1, 2, 3, 4, 5}

# & 取交集
other_set = {3, 4, 5, 6}
filled_set & other_set  # => {3, 4, 5}

# | 取并集
filled_set | other_set  # => {1, 2, 3, 4, 5, 6}

# - 取差集
{1, 2, 3, 4} - {2, 3, 5}  # => {1, 4}

# ^ 取对称差集
{1, 2, 3, 4} ^ {2, 3, 5}  # => {1, 4, 5}

# in 测试集合是否包含元素
2 in filled_set   # => True
10 in filled_set   # => False


####################################################
## 3. 流程控制和迭代器
####################################################

# 先随便定义一个变量
some_var = 5

# 这是个if语句。注意缩进在Python里是有意义的
# 印出"some_var比10小"
if some_var > 10:
    print("some_var比10大")
elif some_var < 10:    # elif句是可选的
    print("some_var比10小")
else:                  # else也是可选的
    print("some_var就是10")


"""
用for循环语句遍历列表
打印:
    dog is a mammal
    cat is a mammal
    mouse is a mammal
"""
for animal in ["dog", "cat", "mouse"]:
    print("{} is a mammal".format(animal))

"""
"range(number)"返回数字列表从0到给的数字
打印:
    0
    1
    2
    3
"""
for i in range(4):
    print(i)

"""
while循环直到条件不满足
打印:
    0
    1
    2
    3
"""
x = 0
while x < 4:
    print(x)
    x += 1  # x = x + 1 的简写

# 用try/except块处理异常状况
try:
    # 用raise抛出异常
    raise IndexError("This is an index error")
except IndexError as e:
    pass    # pass是无操作，但是应该在这里处理错误
except (TypeError, NameError):
    pass    # 可以同时处理不同类的错误
else:   # else语句是可选的，必须在所有的except之后
    print("All good!")   # 只有当try运行完没有错误的时候这句才会运行


# Python提供一个叫做可迭代(iterable)的基本抽象。一个可迭代对象是可以被当作序列
# 的对象。比如说上面range返回的对象就是可迭代的。

filled_dict = {"one": 1, "two": 2, "three": 3}
our_iterable = filled_dict.keys()
print(our_iterable) # => range(1,10) 是一个实现可迭代接口的对象

# 可迭代对象可以遍历
for i in our_iterable:
    print(i)    # 打印 one, two, three

# 但是不可以随机访问
our_iterable[1]  # 抛出TypeError

# 可迭代对象知道怎么生成迭代器
our_iterator = iter(our_iterable)

# 迭代器是一个可以记住遍历的位置的对象
# 用__next__可以取得下一个元素
our_iterator.__next__()  #=> "one"

# 再一次调取__next__时会记得位置
our_iterator.__next__()  #=> "two"
our_iterator.__next__()  #=> "three"

# 当迭代器所有元素都取出后，会抛出StopIteration
our_iterator.__next__() # 抛出StopIteration

# 可以用list一次取出迭代器所有的元素
list(filled_dict.keys())  #=> Returns ["one", "two", "three"]



####################################################
## 4. 函数
####################################################

# 用def定义新函数
def add(x, y):
    print("x is {} and y is {}".format(x, y))
    return x + y    # 用return语句返回

# 调用函数
add(5, 6)   # => 印出"x is 5 and y is 6"并且返回11

# 也可以用关键字参数来调用函数
add(y=6, x=5)   # 关键字参数可以用任何顺序


# 我们可以定义一个可变参数函数
def varargs(*args):
    return args

varargs(1, 2, 3)   # => (1, 2, 3)


# 我们也可以定义一个关键字可变参数函数
def keyword_args(**kwargs):
    return kwargs

# 我们来看看结果是什么：
keyword_args(big="foot", loch="ness")   # => {"big": "foot", "loch": "ness"}


# 这两种可变参数可以混着用
def all_the_args(*args, **kwargs):
    print(args)
    print(kwargs)
"""
all_the_args(1, 2, a=3, b=4) prints:
    (1, 2)
    {"a": 3, "b": 4}
"""

# 调用可变参数函数时可以做跟上面相反的，用*展开序列，用**展开字典。
args = (1, 2, 3, 4)
kwargs = {"a": 3, "b": 4}
all_the_args(*args)   # 相当于 foo(1, 2, 3, 4)
all_the_args(**kwargs)   # 相当于 foo(a=3, b=4)
all_the_args(*args, **kwargs)   # 相当于 foo(1, 2, 3, 4, a=3, b=4)


# 函数作用域
x = 5

def setX(num):
    # 局部作用域的x和全局域的x是不同的
    x = num # => 43
    print (x) # => 43

def setGlobalX(num):
    global x
    print (x) # => 5
    x = num # 现在全局域的x被赋值
    print (x) # => 6

setX(43)
setGlobalX(6)


# 函数在Python是一等公民
def create_adder(x):
    def adder(y):
        return x + y
    return adder

add_10 = create_adder(10)
add_10(3)   # => 13

# 也有匿名函数
(lambda x: x > 2)(3)   # => True

# 内置的高阶函数
map(add_10, [1, 2, 3])   # => [11, 12, 13]
filter(lambda x: x > 5, [3, 4, 5, 6, 7])   # => [6, 7]

# 用列表推导式可以简化映射和过滤。列表推导式的返回值是另一个列表。
[add_10(i) for i in [1, 2, 3]]  # => [11, 12, 13]
[x for x in [3, 4, 5, 6, 7] if x > 5]   # => [6, 7]

####################################################
## 5. 类
####################################################


# 定义一个继承object的类
class Human(object):

    # 类属性，被所有此类的实例共用。
    species = "H. sapiens"

    # 构造方法，当实例被初始化时被调用。注意名字前后的双下划线，这是表明这个属
    # 性或方法对Python有特殊意义，但是允许用户自行定义。你自己取名时不应该用这
    # 种格式。
    def __init__(self, name):
        # Assign the argument to the instance's name attribute
        self.name = name

    # 实例方法，第一个参数总是self，就是这个实例对象
    def say(self, msg):
        return "{name}: {message}".format(name=self.name, message=msg)

    # 类方法，被所有此类的实例共用。第一个参数是这个类对象。
    @classmethod
    def get_species(cls):
        return cls.species

    # 静态方法。调用时没有实例或类的绑定。
    @staticmethod
    def grunt():
        return "*grunt*"


# 构造一个实例
i = Human(name="Ian")
print(i.say("hi"))     # 印出 "Ian: hi"

j = Human("Joel")
print(j.say("hello"))  # 印出 "Joel: hello"

# 调用一个类方法
i.get_species()   # => "H. sapiens"

# 改一个共用的类属性
Human.species = "H. neanderthalensis"
i.get_species()   # => "H. neanderthalensis"
j.get_species()   # => "H. neanderthalensis"

# 调用静态方法
Human.grunt()   # => "*grunt*"


####################################################
## 6. 模块
####################################################

# 用import导入模块
import math
print(math.sqrt(16))  # => 4.0

# 也可以从模块中导入个别值
from math import ceil, floor
print(ceil(3.7))  # => 4.0
print(floor(3.7))   # => 3.0

# 可以导入一个模块中所有值
# 警告：不建议这么做
from math import *

# 如此缩写模块名字
import math as m
math.sqrt(16) == m.sqrt(16)   # => True

# Python模块其实就是普通的Python文件。你可以自己写，然后导入，
# 模块的名字就是文件的名字。

# 你可以这样列出一个模块里所有的值
import math
dir(math)
####################################################
## 6.1 多重继承
####################################################

# 另一个类定义
class Bat:

    species = 'Baty'

    def __init__(self, can_fly=True):
        self.fly = can_fly

    # 这个类包含say方法
    def say(self, msg):
        msg = '... ... ...'
        return msg

    # 也包含自己定义的方法
    def sonar(self):
        return '))) ... ((('

if __name__ == '__main__':
    b = Bat()
    print(b.say('hello'))
    print(b.fly)


# from "文件名不含后缀" import "函数名或类名"
from human import Human
from bat import Bat

# Batman 继承 Human 和 Bat
class Batman(Human, Bat):

    # Batman 的species 类属性，有自己的值
    species = 'Superhero'

    def __init__(self, *args, **kwargs):
        # 一般的，你必须调用 super来继承属性
        #super(Batman, self).__init__(*args, **kwargs)      
        # 尽管如此你现在处理的是多重继承, and super()
        # 只对MRO（Method Resolution Order）列表中的下一个基类有效 
		# 所以 我们对所有祖先明确调用__init__。 
		# 使用 *args和 **kwargs 是一种干净的方式传递参数
		# 对于每个父节点，就像剥洋葱一样。
        Human.__init__(self, 'anonymous', *args, **kwargs)
        Bat.__init__(self, *args, can_fly=False, **kwargs)
        # 重载name属性的值
        self.name = 'Sad Affleck'

    def sing(self):
        return 'nan nan nan nan nan batman!'


if __name__ == '__main__':
    sup = Batman()

    # 实例类型检查
    if isinstance(sup, Human):
        print('I am human')
    if isinstance(sup, Bat):
        print('I am bat')
    if type(sup) is Batman:
        print('I am Batman')

    # Get the Method Resolution search Order used by both getattr() and super().
    # This attribute is dynamic and can be updated
    print(Batman.__mro__)       # => (<class '__main__.Batman'>, <class 'human.Human'>, <class 'bat.Bat'>, <class 'object'>)

    # Calls parent method but uses its own class attribute
    print(sup.get_species())    # => Superhero

    # Calls overloaded method
    print(sup.sing())           # => nan nan nan nan nan batman!

    # Calls method from Human, because inheritance order matters
    sup.say('I agree')          # => Sad Affleck: I agree

    # Call method that exists only in 2nd ancestor
    print(sup.sonar())          # => ))) ... (((

    # Inherited class attribute
    sup.age = 100
    print(sup.age)

    # Inherited attribute from 2nd ancestor whose default value was overridden.
    print('Can I fly? ' + str(sup.fly))



####################################################
## 7. 高级用法
####################################################

# 用生成器(generators)方便地写惰性运算
def double_numbers(iterable):
    for i in iterable:
        yield i + i

# 生成器是高效利用内存的，因为生成器只有当迭代器中的下一个值需要处理的时候，
# 才加载数据到内存。
# 这样使得可以对相当大的一个范围进行运算。
# 注: 在python3 中，range 替代 xrange  
for i in double_numbers(range(1, 900000000)): # range 是一个生成器
    print(i)
    if i >= 30:
        break

# 你可以创建一个列表解析(list comprehension),你也可以创建
# 一个生成器解析( generator comprehensions)
values = (-x for x in [1,2,3,4,5])
for x in values:
    print(x)  # prints -1 -2 -3 -4 -5 to console/terminal

# 你也可以将生成器解析转换成列表
values = (-x for x in [1,2,3,4,5])
gen_to_list = list(values)
print(gen_to_list)  # => [-1, -2, -3, -4, -5]


# 装饰器(decorators)
# 这个例子中，beg装饰say. 如果say_please为真，beg
# 会改变返回的消息。
from functools import wraps


def beg(target_function):
    @wraps(target_function)
    def wrapper(*args, **kwargs):
        msg, say_please = target_function(*args, **kwargs)
        if say_please:
            return "{} {}".format(msg, "Please! I am poor :(")
        return msg

    return wrapper


@beg
def say(say_please=False):
    msg = "Can you buy me a beer?"
    return msg, say_please


print(say())                 # Can you buy me a beer?
print(say(say_please=True))  # Can you buy me a beer? Please! I am poor :(
```

## 想继续学吗？

### 线上免费材料（英文）

* [Automate the Boring Stuff with Python](https://automatetheboringstuff.com)
* [Learn Python The Hard Way](http://learnpythonthehardway.org/book/)
* [Dive Into Python](http://www.diveintopython.net/)
* [Ideas for Python Projects](http://pythonpracticeprojects.com)
* [The Official Docs](http://docs.python.org/3/)
* [Hitchhiker's Guide to Python](http://docs.python-guide.org/en/latest/)
* [A Crash Course in Python for Scientists](http://nbviewer.ipython.org/5920182)
* [Python Course](http://www.python-course.eu/index.php)
* [First Steps With Python](https://realpython.com/learn/python-first-steps/)
* [A curated list of awesome Python frameworks, libraries and software](https://github.com/vinta/awesome-python)
* [30 Python Language Features and Tricks You May Not Know About](http://sahandsaba.com/thirty-python-language-features-and-tricks-you-may-not-know.html)
* [Official Style Guide for Python](https://www.python.org/dev/peps/pep-0008/)
* [Python 3 Computer Science Circles](http://cscircles.cemc.uwaterloo.ca/)

### 书籍（也是英文）

* [Programming Python](http://www.amazon.com/gp/product/0596158106/ref=as_li_qf_sp_asin_tl?ie=UTF8&camp=1789&creative=9325&creativeASIN=0596158106&linkCode=as2&tag=homebits04-20)
* [Dive Into Python](http://www.amazon.com/gp/product/1441413022/ref=as_li_tf_tl?ie=UTF8&camp=1789&creative=9325&creativeASIN=1441413022&linkCode=as2&tag=homebits04-20)
* [Python Essential Reference](http://www.amazon.com/gp/product/0672329786/ref=as_li_tf_tl?ie=UTF8&camp=1789&creative=9325&creativeASIN=0672329786&linkCode=as2&tag=homebits04-20)
