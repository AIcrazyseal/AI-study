# Python基础语法
> 创建：2026.2.26

## Python常见符号
- #：Python注释符号，用于阐明代码
- **：数学中的乘方，2 ** 3=8
- =：给变量赋值，name='John'
- _：有多种作用
  - 交互模式下，上次输出的表达式会赋给变量 _
  - 临时变量	for _ in range(10)	表示变量_临时或不重要变量
  - 单下划线前缀  self._protected = "请视为内部使用"
  - 避免与关键字冲突  加下划线作为后缀：class_ = "数学课"     # 可以
  - 数字中的千位分隔符，million = 1_000_000     # 等价于 million =1000000
  - 特殊方法名中的双下划线  def __ init__(self):      # 构造函数
  - 国际化/本地化中的别名   print(_("Hello World"))  # 会根据当前语言环境翻译  _被用作gettext（国际化）函数的别名

- 字符串
  - 可以用'yes'或者“yes”表示，结果一样
  - 单双引号可以嵌套使用 >>>"Isn\'t," they said.'  输出：'"Isn\'t," they said.'
  - 三重引号："""...""" 或 '''...'''，用于跨多行的字符串
  - 转义符\： \n换行符，\t制表符（Tab键），\ \代表一个'\ '字符
  - r:代表 "raw"（原始）,print(r'C:\some\name'),代表r后面是原始字符串，\不会被当作转义字符来处理。
  - f:格式化字符串，f'{who.title()} expects the {nationality} Inquisition!' {}中可以有变量等表达式
  - %：字符串的 格式化 或 插值运算符，建议用新版的f-string或者str.format()替代。
    - %s:字符串占位符
    - %d：十进制整数占位符
    - %i：整数占位符
    - %f：浮点数占位符
- 列表List：序号是从0开始的，例如s=[1,2,3,4],则s[0]=1，s[1:3]=[2] #包含s[1]、s[2]元素，但不包含s[3]元素
- 元组解包赋值（又叫多重赋值）tuple unpacking 例如：(a, b) = (0, 1)，元组是不可变量
- 字典：键值对的集合，键必须在字典内唯一，字典用{}表示；
  - 字典构建：d={}，创建空字典d；dict() 构造函数可以直接用键值对序列创建字典；
  - del d[key]：删除字典d中键值为key的键值对；
  - list(d)：返回字典d中所有键的列表；
  - key in d：检查键值key是否在字典d中，存在则返回true，否在返回false；
  - 字典循环：items()可同时提取键和对应的值； enumerate() 函数可以同时取出序列的位置索引和对应的值;
- [Python内置函数](https://docs.python.org/zh-cn/3.14/library/functions.html)

## Python控制流工具[复合语句](https://docs.python.org/zh-cn/3.14/reference/compound_stmts.html)
- if assignment_expression ： suite
  elif assignment_expression ： suite
  else ： suite
- while assignment_expression : suite
  else: suite
- for target_list in starred_expression_list : suite
  else: suite
- 内置函数 range() 用于生成等差数列：
- match subject_expr:
  case：case_block1：
  case：case_block2：
- def：定义函数使用的关键字，函数语句从下一行开始，并且必须缩进。
  - 函数第一行应是文档字符串，用于函数功能描述，可以生成函数文档
  - 调用函数时，可以传递比函数定义时更少的参数
  - 关键字参数：kwarg=value 形式。关键字参数的形参名称有实际意义，调用函数时，关键字参数出现的位置与顺序无关，只与形参名称赋值有关
  - 位置参数：与函数参数的位置有关，形参名称无实际意义
  - 函数注解：def f(ham: str, eggs: str = 'eggs') -> str:
    - 形参标注：形参后面加冒号+表达式
    - 返回值标注：->+表达式
- 编码风格
  - 缩进，用 4 个空格，不要用制表符（会引起混乱）。
  - 换行，一行不超过 79 个字符。
  - 用空行分隔函数和类，及函数内较大的代码块。
  - 最好把注释放到单独一行。
  - 使用文档字符串。
  - 运算符前后、逗号后要用空格，但不要直接在括号内使用： a = f(1, 2) + g(3, 4)。
  - 类和函数的命名要一致；按惯例，命名类用 UpperCamelCase，命名函数与方法用 lowercase_with_underscores。命名方法中第一个参数总是用 self 。
  - 编写用于国际多语环境的代码时，不要用生僻的编码。Python 默认的 UTF-8 或纯 ASCII 可以胜任各种情况。
  - 同理，就算多语阅读、维护代码的可能再小，也不要在标识符中使用非 ASCII 字符。

## 模块module
- 文件名是模块名加后缀名.py
- 已编译的Python文件：模块的编译版本缓存在__pycache__目录中，文件名为 module.version.pyc，version一般是 Python 的版本号。
- 模块中可以有函数、有模块内的全局变量
- 模块导入import
  - import Fibo：将模块名称fibo导入到namespace中，模块fibo中的函数和变量不会进入namespace；
  - from fibo import fib,fib2:将模块fibo中的函数fib，fib2导入到其他模块中，以便其他模块可以直接调用函数fib，fib2；
  - from fibo import *:将模块fibo中所有函数导入到其他模块；这种方式向python解释器导入了一批未知的名称，可能会覆盖一定义的名称；
  - import fibo as f，f.fib(500)： 导入模块fibo并重命名为f，后续代码直接用f代表fibo模块；
  - from fibo import fib as f：从模块fibo中导入函数fib，并重命名为f；
- 模块运行：
  - 在模块末尾添加代码if __ name__ == "__ main__":  
                       import sys
                       fib(int(sys.argv[1])) 
                       这个模块的py文件，既能被用作脚本，又可被其他模块导入、调用；
  - 当模块在python解释器中直接执行时，例如：python fibo.py 10 ，此时__name__被设置为"__ main__"，sys.argv[0]='fibo.py',sys.argv[1]='10';
  - 当模块被导入到其他模块时：__ name__ 被设置为模块的名字（如 "fibo"）,不会执行 fib(int(sys.argv[1]));
- 模块搜索路径次序：当import fib时，python解释器会
  - 在sys.builtin_module_names 中搜索是否有叫fib的内置模块；
  - 如果上一步没有找到fib模块，将在sys.path中搜索fib.py,sys.path的初始化位置如下：
    - 被命令行直接运行的脚本所在的目录（或未指定文件时的当前目录）。
    - PYTHONPATH （目录列表，与 shell 变量 PATH 的语法一样）。
    - 依赖于安装的默认值（按照惯例包括一个 site-packages 目录，由 site 模块处理）。
- dir()内置函数：
  - dir():如果没有实参，则返回当前本地作用域中的名称列表;
  - dir(object):如果有实参，它会尝试返回该对象的有效属性列表。
    - 如果对象是**模块对象**，则列表包含模块的属性名称;
    - 如果对象是**类型或类对象**，则列表包含它们的属性名称，并且递归查找所有基类的属性；
    - 否则，列表包含对象的属性名称，它的类属性名称，并且递归查找它的类的所有基类的属性。
## 包Package
- 必须有__init__.py 文件才能让 Python 将包含该文件的目录当作包来处理；
- __init __.py文件用于执行包的初始化代码或设置__all__变量，可以是一个空文件；
- 子包、模块、函数、类、变量的导入方式：import package from subpackage/module/funciton/class/variable
  - 从包中导入单个模块：import sound.effects.echo； 或者 from sound.effects import echo
  - 从包中导入函数或者变量：from sound.effects.echo import echofilter  #加载子模块echo中的echofilter()函数
  - 从包中导入*： from sound.effects import * ，不建议这种编码风格。
    - 如果包的__init__.py中定义了__all__变量， import *则表示导入了__all__变量中包含的子包、模块、函数等；
    - 如果包的__init__.py中没有定义__all__变量， import *不会把包 sound.effects 中的所有子模块都导入到当前命名空间；它只是确保包sound.effects 已被导入；
    - **__all__变量**：是一个字符串列表，用于控制模块导入时的行为，主要作用如下：
      - 控制from package import *的行为；
      - 明确并控制 API 的公共接口，防止API内部实现细节被曝光；
      - 在包（Package）的__init__.py 中使用；
