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
- 列表List的序号是从0开始的，例如s=[1,2,3,4],则s[0]=1
- 元组解包赋值（又叫多重赋值）tuple unpacking 例如：(a, b) = (0, 1)
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