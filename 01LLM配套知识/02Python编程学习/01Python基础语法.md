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
  - from fibo import fib1,fib2:将模块fibo中的函数fib1，fib2导入到其他模块中，以便其他模块可以直接调用函数fib1，fib2；
  - from fibo import *:将模块fibo中所有函数导入到其他模块；这种方式向python解释器导入了一批未知的名称，可能会覆盖一定义的名称；
  - import fibo as f，f.fib(500)： 导入模块fibo并重命名为f，后续代码直接用f代表fibo模块；
  - from fibo import fib as f：从模块fibo中导入函数fib，并重命名为f；
- 模块运行：
  - 在模块末尾添加代码if __ name__ == "__ main__":import sys
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
- 查看导入的第三方Package学习文档(pydoc packagename)：
  - 以web方式查看：在cmd命令行中输入：python -m pydoc -b;
  - 在cmd中查看包/模块/函数/变量：
    - python -m pydoc packagename/packagename.modulename/packagename.functionname/packagename.variable
    - pip show packagename --version,即可显示该包的详细信息，将该包的home-page的url在浏览器中打开即可看到官方的document。
  - 在python shell环境下，查看包/模块/函数/变量：import package    help(package/package.func)
  
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


## 输入输出

- 输出方式：print(),表达式语句，文件对象的write()方法；
- 格式化字符串：在字符串开头的单双引号/三引号前添加 f 或 F 。在字符串中的{} 之间输入引用的变量，例如：f'Results of the {year} {event}' ，year、event是变量；
  - str.format(*args, **kwargs) 调用此方法的字符串可以包含 __文本字面值或者以花括号 {} 标明的替换字段__。 每个替换字段可以包含一个 __位置参数的数字索引__，或是一个 __关键字参数的名称__。返回的字符串副本中每个替换字段都会被替换为对应参数的字符串值：

    ```
       >>>"{1} expects the {0} Inquisition!".format("Spanish", "Nobody")
          'Nobody expects the Spanish Inquisition!'
       >>>"The sum of {a} + {b} is {answer}".format(answer=1+2, a=1, b=2)
          'The sum of 1 + 2 is 3'
       >>>print('The story of {0}, {1}, and {other}.'.format('Bill', 'Manfred',other='Georg'))
          'The story of Bill, Manfred, and Georg.'
    ```
  - 输出格式调整
    print('{0:2d} {1:3d} {2:4d}'.format(x, x*x, x*x*x))
    {}中的0、1、2是format(args)的位置，d代表整数，d前面的数字（2，3，4）代表输出结果占位最小宽度，默认是右对齐。
  - 旧式字符串格式化str%values方法：
    str中的% 转换占位符将以 values 中的零个或多个元素来替换。 此操作通常称为字符串插值。

    ```
    print('%s has %d quote types.' % ('Python', 2))   #%s代表字符串占位符，%d代表十进制整数占位符
    Python has 2 quote types.
    ```
- 文件读写
  - open(filename, mode, encoding=None)：打开 file 并返回对应的 file object。
    - filename：包含路径的文件名；
    - mode：可选实参，默认为r、t,
      - w代表只能写入
      - r代表只能读取
      - r+表示打开文件进行读写
      - a代表打开文件并追加内容
      - t代表文本模式，文件内容返回为 str，使用平台默认或者指定的encoding。
      - b代表二进制模式，返回的内容为 bytes 对象，不进行任何解码
    - encoding=utf-8
  - 文件关闭
    - with open(filename,mode,encoding='utf-8')
      在处理文件对象时，**使用 with 关键字，子句体结束后，文件会正确关闭**，即便触发异常也可以。而且，使用 with 相比等效的 try-finally 代码块要简短得多;
    - 如果没有使用with关键字，则**应调用f.close()关闭文件**，即可释放文件占用的系统资源,再次使用该文件对象将会失败。
  - file读取方法
    - file.read(size)：读取并返回最多 size 个字符（文本模式）或 size 个字节（二进制模式）。如已到达文件末尾，file.read() 返回空字符串（''）。省略 size 或 size 为负数时，读取并返回整个文件的内容。
    - f.readline()：从文件中**读取单行数据**；字符串末尾保留换行符（\n），只有在文件不以换行符结尾时，文件的最后一行才会省略换行符。这种方式让返回值清晰明确；只要 f.readline() 返回空字符串，就表示已经到达了文件末尾，空行使用 '\n' 表示，该字符串只包含一个换行符。
    - file写入方法write(string)
  - 使用Json保存结构化数据：json.dumps(),json.dump()。JSON 文件必须以 UTF-8 编码。

## 错误和异常

- 错误分为语法错误和异常。语法错误又称解析错误。异常是指语法正确但执行时检测到的错误。错误信息的最后一行说明程序遇到了什么类型的错误。标准的异常类型是内置的标识符（不是保留关键字）详见[内置异常](https://docs.python.org/zh-cn/3.14/library/exceptions.html#bltin-exceptions)。
- 异常处理：可以编写try……except程序处理选定的异常。
  - try 语句的工作原理如下：
    - 首先，执行 try 子句 （try 和 except 关键字之间的（多行）语句）。
    - 如果没有触发异常，则跳过 except 子句，try 语句执行完毕。
    - 如果在执行 try 子句时发生了异常，则跳过该子句中剩下的部分。如果异常的类型与 except 关键字后指定的异常相匹配，则会执行 except 子句，然后跳到 try/except 代码块之后继续执行。
    - 如果发生的异常与 except 子句 中指定的异常不匹配，则它会被传递到外层的 try 语句中；如果没有找到处理器，则它是一个 未处理异常 且执行将停止并输出一条错误消息。
- try 语句可以有多个 except 子句来为不同的异常指定处理程序。
- except 子句 可以用带圆括号的元组来指定多个异常，例如：
  `... except (RuntimeError, TypeError, NameError):`
  `...     pass`
- 异常触发：raise 语句支持强制触发指定的异常。
- [异常链](https://docs.python.org/zh-cn/3.14/library/exceptions.html#bltin-exceptions)
  - 如果一个未处理的异常发生在 except 部分内，它将会有被处理的异常附加到它上面，并包括在错误信息中;
  - 一个异常是另一个异常的直接后果,用raise……from表示
    `# exc 必须为异常实例或为 None。None表示禁用自动异常链`
    `raise RuntimeError from exc`
- 用户自定义的异常都应从 Exception 类派生。
- 定义清理操作：try 语句还有一个可选的finally子句，不论 try 语句是否触发异常，都会执行 finally 子句。几种比较复杂的触发异常情景如下：
  - 如果执行 try 子句期间触发了某个异常，则某个 except 子句应处理该异常。如果该异常没有 except 子句处理，在 finally 子句执行后会被重新触发。
  - except 或 else 子句执行期间也会触发异常。同样，该异常会在 finally 子句执行之后被重新触发。
  - 如果 finally 子句执行 break、 continue 或 return 语句，异常不重新引发。这可能会引起混淆，因此不鼓励使用。从 3.14 版开始，编译器会为它发出一个 SyntaxWarning (参见 PEP 765)。
  - 如果执行 try 语句时遇到 break、continue 或 return 语句，则 finally 子句在执行 break、continue 或 return 语句之前执行。
  - 如果一个 finally 子句包含一个 return 语句，返回的值将是来自 finally 子句的 return 语句，而不是来自 try 子句的 return 语句。这可能会引起混淆，因此不提倡使用。从 3.14 版开始，编译器会为它发出一个 SyntaxWarning （参见 PEP 765）。

## 类Class

- 类提供了把数据和功能绑定在一起的方法，可以在运行中创建和修改。实例具有能维持和修改自身状态的属性。
- 类的继承机制：类可以继承多个基类，派生类能覆盖基类的方法、调用基类中的同名方法。
- 类Class、对象Object、实体Instance关系：**类是"概念"，实例是"实物"，对象≈实例。**
  - 类：定义了一组对象的共同特征和行为（就像"人"这个概念）
  - 实例：根据类创建的具体实体（就像具体的"张三"这个人）
  - 对象：通常指实例，是类的具体表现（"张三"这个人就是一个对象）
  - 关系：类是模板，实例是根据模板创建的具体产品
- Python的**命名空间namespace**
  - namespace（命名空间）是从名称到对象的映射，一般使用 Python 字典实现；
  - 命名空间的例子有：内置名称集合（包括 abs() 函数以及内置异常的名称等）、一个模块的全局名称、一个函数调用中的局部名称、对象的属性集合；
  - 不同命名空间中的名称之间绝对没有关系；
  - 对模块中名称的引用是属性引用，模块属性和模块中定义的全局名称之间存在直接的映射：它们共享相同的命名空间！
  - **命名空间是在不同时刻创建的，且拥有不同的生命周期。**
    - **内置名称**的命名空间是在 Python 解释器启动时创建的，永远不会被删除。
    - **模块**的全局命名空间在读取模块定义时创建，续到解释器退出。
    - 从**脚本文件读取或交互式读取**的，由解释器顶层调用执行的语句是__main__ 模块调用的一部分，也拥有自己的全局命名空间。内置名称实际上也在模块里，即 builtins 。
    - **函数**的局部命名空间在函数被调用时被创建，并在函数返回或抛出未在函数内被处理的异常时，被遗忘。
- **命名空间的作用域** 是 Python 代码中的一段文本区域，从这个区域可直接访问该命名空间。执行期间的任何时刻，都会有3或4个“命名空间可直接访问”的嵌套作用域：
  - 最内层作用域，包含局部名称，并首先在其中进行搜索；
  - 外层**闭包函数**的作用域，包含“非局部、非全局”的名称，从最靠内层的那个作用域开始，逐层向外搜索；
  - 倒数第二层作用域，包含**当前模块**的全局名称；
  - 最外层（最后搜索）的作用域，是**内置名称**的命名空间。
- **命名空间的作用域从内到外的个人总结**如下：
  - 局部作用域 (Local)：     函数或方法内部的最内层作用域；
  - 嵌套作用域 (Enclosing)： 嵌套函数中外层函数的作用域，内层函数可以访问外层函数的变量；
  - 全局作用域 (Global)：    当前模块（或.py文件）顶层的名字；
  - 类作用域 (Class)：       定义类时创建的局部命名空间，但它不会影响类内部方法的作用域；
  - 内置作用域 (Built-in)：  Python预定义的名字（如print、len）
- **globle和nonlocal变量作用域？**
- 类的继承
  - class DerivedClassName(BaseClassName)
  - 类的多重继承class DerivedClassName(Base1, Base2, Base3)
  - 搜索从父类所继承属性的操作是深度优先、从左到右的，当层次结构存在重叠时不会在同一个类中搜索两次。
  - [method方法的解析顺序](https://docs.python.org/3.14/howto/mro.html#python-2-3-mro)
- 私有变量：带有一个下划线的名称 (例如 _spam) 应该被当作是 API 的非公有部分 (无论它是函数、方法或是数据成员)。
- 迭代器会调用iter()和next()方法
- 生成器可以用来创建迭代器，当它们要返回数据时会使用 yield 语句；yield 表达式和语句仅用于生成器的函数体内。

## 标准库Standard Library

- 操作系统接口：模块os、shutil
- 文件通配符glob：import glob
- 命令行参数：模块sys.argv,sys.stdin,sys.stdout,sys.stderr,sys.exit();
- 字符串模式匹配：模块re为高级字符串处理的正则表达式工具；
- 数学：math模块提供浮点数数学运算方法；random模块是随机选择工具；统计模块statistics(均值、中位数、方差等);[详见SciPy项目：数值计算](https://scipy.org/)
- 互联网访问：urllib.request(从URL检索数据)、smtplib(用于发邮件)
- 日期和时间：datatime模块是日期和时间的类
- 数据压缩：数据存档和压缩模块zlib,gzip,bz2,lzma,zipfile,tarfile
- 性能测量timeit模块：from timeit import Timer,可快速测量代码运行耗时；
- 质量控制：doctest模块提供了一个测试功能，import doctest,doctest.testmod() #自动验证嵌入式测试；unittest模块可以在一个单独的文件中维护更全面的测试集。
- Standard library 第二部分涵盖了专业编程所需要的更高级的模块。略。

## 虚拟环境和包

- 虚拟环境：
  - venv:创建和管理虚拟环境的模块
  - 创建虚拟环境：python -m venv t-env #创建了一个名叫t-env的虚拟环境；
  - 激活虚拟环境：t-env\Scripts\activate
  - 撤销激活虚拟环境：deactivate。
- 使用pip管理包
  - pip安装、升级包，是从[Python Package Index:pypi](https://pypi.org/)安装软件包。
  - 安装包：
    - python -m pip install packagename  #安装最新版本的包；
    - python -m pip install packagename==2.6.0  #安装2.6.0版本的包；
    - python -m pip install --upgrade packagename  #将包升级到最新版本的包；
  - 删除包：python -m pip uninstall packagename
  - 查询包的信息：python -m pip show packagename;
  - 查询所有在虚拟环境中安装的包:python -m pip list;
  - 导出当前程序运行所需的依赖包到requestment.txt文件：python -m pip freeze > requirements.txt
  - 安装配置当前程序运行所需要的依赖包：python -m pip install -r requirements.txt
