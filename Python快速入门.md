# 快速入门

交互式编程不需要创建脚本文件，是通过 Python 解释器的交互模式进来编写代码。


1. 在命令行中输入Python即可启动交互式编程![](https://i.imgur.com/XjX9ZyX.png)
2. Windows在安装Python时已经已经安装了默认的交互式编程客户端![](https://i.imgur.com/uSRLqWV.png)

## 一. 输出语句print

1. 在交互式解释器中，可以用print语句输出，也可以使用变量名查看变量的值。

   ``` python
	>>> print 'hello world!'
	hello world!

	>>> str = 'hello world!'
	>>> str
	'hello world!'
   ```

2. print语句与字符串格式操作符（%）结合：
   1) %s是字符串
   2) %d是有符号十进制整数，%06d表示输出的整数显示6位数，不足的地方使用0补全，超过6位则显示原数。
   3) %f浮点数，%.06f表示小数点后只显示6位
   4) %%输出%
   5) 格式：
    - print("格式化字符串" % 变量1)
    - print("格式化字符串" % (变量1, 变量2, ...))

   ``` python
	  >>> print "%s is String, %d is int, %f is float" % ("abc", 1, 1.0)
	  abc is String, 1 is int, 1.000000 is float
	  >>> print("%16d" % (2))
      2
	  >>> print("%016d" % (2))
	  0000000000000002
	  >>> print("%.06f" % (2.1))
	  2.100000
   ```
3. print输出函数会自动在内容末尾换行

- 若不希望输出换行，可增加`end=""`： 并且引号内可添加想要继续显示的内容
    ``` python
    print("hello", end="")
    ```
- 重定向输出到文件，符号 >>
	``` python
	>>> print >> filename, 'string'
	```

## 二. 输入语句 input()

1. 输入时赋值给变量，数据类型是字符串，如果需要使用整型，需要使用int()函数转换。
2. 内建函数input()读取标准输入，数据赋值给指定变量。
    ``` python
    >>> user = input('Enter your name: ')
	  Enter your name: chensiwen
	  >>> print 'Your name is: ', user
	  Your name is:  chensiwen
    ```
3. 内建函数int()将字符串转成整型值。
	``` python
	>>> num = input('Enter a number: ')
	Enter a number: 1000
	>>> print 'Your number is %d' % (int(num))
	Your number is 1000
	>>> print 'Your number is ', int(num)
	Your number is  1000
	>>> print 'Double your number is ', int(num)*2
	Double your number is  2000
	```
4. float()将字符串转成浮点型。
	```python
	>>> float('12.3')
	12.3
	>>> type(float('12.3'))
	<class 'float'>
	```

## 三. 帮组函数 help(函数名称)
   ```python
	>>> help(raw_input) #以raw_input()函数为例
	Help on built-in function raw_input in module __builtin__:
	raw_input(...)
	    raw_input([prompt]) -> string
	    
	    Read a string from standard input.  The trailing newline is stripped.
	    If the user hits EOF (Unix: Ctl-D, Windows: Ctl-Z+Return), raise EOFError.
	    On Unix, GNU readline is used if enabled.  The prompt string, if given,
	    is printed without a trailing newline before reading.
   ```

## 四. 注释
1. 单行注释：注释语句从#字符开始，可以在一行的任何地方。快捷键Ctrl+/，将选中的行变成单行注释
	
	``` python
	>>> # one comment
	```
2. 文档字符串注释，在模块、类或者函数的起始添加一个字符串，起到在线文档的功能。文档字符串可以在运行时访问，也可以用来自动生成文档。
	```python
	>>> def foo():
		"""this is a doc string"""
		return true
	```
3. Python提供一个机制，通过__doc__特别变量，动态获得文档字串。在模块、类、函数声明中第一个没有赋值的字符串可以用属性 `obj.__doc__` 来进行访问，其中 obj 是一个模块、类、函数名字，这在运行时也可以进行。	


## 五. 操作符

1. 标准算术操作符： 加(`+`)，减(`-`)，乘(`*`), 除（`/`, `//`)，取余(`%`)，指数(`**`)

	- 优先级：指数(`**`), 单目 `+`(正数)或 `-`(负数), 乘除法和取余，加减法
	
	```python
	>>> print -2*4+2**3
	0 
	```

	- 单斜杠 `/` ：python3.0以后，真除法，无论任何类型都会保持小数部分。
	- 双斜杠 `//` ：整除，结果只取整数部分，若操作时是浮点型，结果是浮点型整数
	
	```python
	>>> 17 / 3  # int / int -> int
	5
	>>> 17 / 3.0  # int / float -> float
	5.666666666666667
	>>> 17//3
	5
	>>> 17 // 3.0  # explicit floor division discards the fractional part
	5.0
	```

2. 标准比较操作符： `<`, `>`, `<=`, `>=`, `==`, `!=`, `<>`

	- 返回布尔类型值： **`True`**, **`False`**
	- 两种不等于：`!=`, `<>` 后者在python3.0已不可用。

3. 逻辑操作符：`and`, `or`, `not`

	- 逻辑操作符可以将任意表达式连接在一起，并得到布尔值。
	- `A < B < C` 等价与 `A < B and B < C` 
	
4. `*`用于字符串

	```python
	>>> 'abc ' * 10
        'abc abc abc abc abc abc abc abc abc abc '
	```
	
5. 转义字符

  - `\t`在控制台输出**制表符**， 使得输出文本在**垂直方向**保持对齐
    ```python
    print("1\t2\t3")
    print("12\t200\t33")
    
    1	2	3
    
    12	200	33
    ​````
    ```

  - `\n`在控制台输出**换行符**
  - `\\` 反斜杠`\`
  - `\r` 回车
  - `\'` 单引号'; `\"` 双引号"


## 六. 赋值
1. Python是动态类型语言，不需要预先声明变量的类型。变量的类型和值在赋值时被初始化
2. 赋值操作符(**`=`**)：在python中，对象是通过**引用**传递。是将对象的引用（并不是值）赋值给变量。可以链式赋值：
	```python
	y = x = x + 1
	```

3. 增量赋值：算术操作符与等号组合，结果赋值给左边变量。
	
	+=，-=，*=，/=，%=，**=，<<=，>>=，&=，^=，|=

4. python不支持自增`++`和自减`--`
5. 多重赋值

	```python
	>>> x = y = z = 1
	>>> x, y, z
	(1, 1, 1)
	```
6. 多元赋值

    - 采用这种方式赋值时，等号两边的对象都是元组。

	```python
	>>> (x, y, z, w) = (1, 2.0, 'string', True)
	>>> x, y, z, w
	(1, 2.0, 'string', True)
	```
    - 变量交换：利用多元赋值，无需临时变量

	```python
	>>> (x, y) = (1, 2.0)
	>>> x, y
	(1, 2.0)
	>>> (x, y) = (y, x)
	>>> x, y
	(2.0, 1)
	```

## 七. 标识符 ##
1. 合法的Python标识
	- 第一个字符必须是字母或下划线，不能以数字开头
	- 剩下的字符可以是由**字母、数字、下划线**组成
	- **区分大小写**
2. Python保留字符，不能用作常数或变数，或任何其他标识符名称。所有 Python 的关键字只包含小写字母。关键字33个

	***and, as, assert, break, class, continue, def, del, elif, else, except, exec, finally, for, from, global, if, import, in, is, lambda, not, or, pass, print, raise, return, try, while, with, yield, None***
3. 下划线开头的标识符具有特殊意义：python用下划线作为变量的前缀和后缀指定特殊变量。
	- 单下划线开头（_xxx）:代表不能直接访问的类属性，需通过类提供的接口进行访问，不能用 `from xxx import *` 而导入；
	- 双下划线开头（__name）:代表类的私有成员;
	- 双下划线开头和结尾（__name__）:代表 Python 里特殊方法专用的标识，如 __init__() 代表类的构造函数。
4. Python可以同一行显示多条语句，方法是用**分号(;)** 分开。


## 八. 标准数据类型

1. Python有五个标准的数据类型：
    - Numbers（数字）
    - String（字符串）
    - List（列表）
    - Tuple（元组）
    - Dictionary（字典）

2. 使用type()函数可以查看变量的类型
 ```python
	>>> age=18
	>>> type(age)
	<class 'int'>
	>>> name = 'chensiwen'
	>>> type(name)
	<class 'str'>
	>>> aDict={'Key':'Value'}
	>>> type(aDict)
	<class 'dict'>
 ```

### 1) Numbers 数字

1. int （有符号整型）
2. long （长整型，也可以表示成八进制和十六进制）：	
	- python长整型表达范围仅受限与用户计算机的虚拟内存总数
	- 整型与长整型逐步统一为一种整型类型，python 2.3开始不会报整型溢出错误，结果自动被转换成长整型。
3. float （浮点型）
4. complex（复数）
5. bool布尔值：特殊的整型，True 对应整型值`1`（非0），False 对应整型值`0`。

### 2) String 字符串

1. 支持成对的单引号(`'...'`)，双引号(`"..."`)，三引号(`'''...'''`，`"""..."""`)来包含字符串，引号的开始与结束必须的相同类型；
2. 三引号可以由多行组成，编写多行文本的快捷语法，常用于文档字符串，在文件的特定地点，被当做注释。
3. 索引操作符`[]`和切片操作符`[:]`得到子字符串，包左不包右；
4. 索引规则：第一个字符的索引是`0`，最后一个字符索引是`-1`。
	```python
	>>> str='Python ' + "is " + '''cool''' + """!"""
	>>> str[-1]
	'!'
	>>> str[0:5] #包左不包右
	'Pytho'
	>>> str[1:6]
	'ython'
	>>> str[0:6]
	'Python'
	```

4. 加号`+`用于连接字符串，星号`*`用于重复字符串

	```python
	>>> 'Python ' + "is " + '''cool''' + """!"""
	'Python is cool!'
	>>> 'Python' * 2
	'PythonPython'
	```

### 3）List 列表和 Tuple 元组

1. 可以保存**任意数量、任意类型、不同类型的Python对象**;
2. 列表用`[]`，元素的个数和值可以改变；
   ```python
     list_name = []  #空列表
     list_name = ["A", "B", "C", ...]
     list_name[index]  #取数据，数字索引index从`0`开始
   ```
3. 元组
      - 元组定义使用`()`;
      - 元组一旦定义完成，不可以更改，看成是只读的列表。
      - 获取数据：元组名[index]
      - 空元组：元组名 = ()
      - 只包含一个元素的元组：元组名 = (单元素, )
      - 常用操作方法： 统计个数count(参数), 索引位置index(参数)
      - 实际开发中，元组保存的数据类型一般是不相同的
4. 应用场景
    - 函数的参数和返回值：可以接收任意多个参数、一次返回多个数据
    - 格式化字符串：
    
        格式化字符串后面的`()`本质上就是元组，print("格式化字符串" % (变量1, 变量2, ...))
    - 让列表不可以被修改，保护数据安全 
5. 元组和列表之间的转换
   - 元组转换成列表: list(tuple_name)
   - 列表转换成元组：tuple(list_name)

### 4）Dictionary 字典

1. 字典是Python中的映射数据类型，由键值对（key-value）构成；字典是一种动态结构，可随时在其中添加键—值对

2. 键key：一般常用数字或字符串和元组；

3. 值value：可以是任何Python对象，数字、字符串、列表乃至字典

4. 字典元素使用`{}`

  ```python
  #创建空字典
  a_dict={}
  
  #创建字典
  a_dict={'Key':'Value'}
  
  #添加键值对，修改值
  a_dict['Key']='Value_Change' #修改Key的值
  a_dict['Key2']='Value2'#添加新的键值对
  
  #取所有的键
  >>> a_dict.keys() 
  ['Key2', 'Key']
  
  #取键对应的值
  >>> a_dict['Key'] 
  'Value'
  
  #删除键值对
  del a_dict['Key']
  ```

5. 遍历字典

   ```python
   #a.遍历所有的键—值对
   for key,value in a_dict.items():  # key存储键,value存储值,items()方法返回一个键—值对列表
       code
       
   #b.遍历所有键
   for key in a_dict.keys(): 
       code
   #遍历字典时，会默认遍历所有的键，因此，如果将上述代码中的for key in a_dict.keys():替换为for key in a_dict: ，输出将不变
   #方法keys() 并非只能用于遍历；实际上，它返回一个列表，其中包含字典中的所有键
   
   #c.遍历字典中的所有值
   for value in a_dict.values():  #方法values() ，它返回一个值列表，但包含重复值
       code
   
   for value in set(a_dict.values()):  #通过对包含重复元素的列表调用set() ，可让Python找出列表中独一无二的元素，并使用这些元素来创建一个集合
       code
       
   #d.按顺序遍历字典中的所有键
   for key in sorted(a_dict.keys()):  #函数sorted() 来获得按特定顺序排列的键列表的副本
       code
   ```

   遍历字典时，键—值对的返回顺序也与存储顺序不同。Python不关心键—值对的添加顺序，而只关心键和值之间的关联关系

6. 嵌套

   字典存储在列表中，或将列表作为值存储在字典中，这称为嵌套。也可在字典中嵌套字典

   列表和字典的嵌套层级不应太多。如果嵌套层级比前面的示例多得多，很可能有更简单的解决问题的方案。


### 5）切片

  1. 支持的数据类型：字符串、列表、元组
  2. 格式：[开始索引:结束索引:步长] 
  3. 左闭右开

## 九. 代码组 ##

1. 代码块通过缩进对齐表达代码逻辑，而不是使用大括号{}。
2. 代码组：缩进相同的一组语句构成一个代码块。同一代码组的代码行必须严格左对齐。
3. Python对空格或者制表符都支持，但是不同文本编辑器中的制表符代表的空白宽度不一，如果代码要跨平台应用，或者被被不同编辑器编写，建议不要使用制表符。建议使用4个空格宽度。
4. 没有缩进的代码块是最高层次的，被称作脚本的“主体”main部分
5. 分号‘;’允许将多条语句写在同一行上，语句之间用分号隔开。（降低可读性，不建议使用）

## 十. 条件和循环语句 ##

1. 标准if语句。条件可以加括号(expression)，多行显示。
    ```python
    if expression:  #当表达式的值非0、布尔值True时，则执行代码组if_suite。条件表达式不需要括号
        if_suite  #代码组suite是一个Python术语，由一条或多条语句组成，表示子代码块。
    ```

    缩进时使用Tab或是4个空格，但开发中不能混合使用。

2. if-else语句、if-elif-else语句

  ```python
  if expression:
  	if_suite
  else:
  	else_suite
  ```

  ```python
  if expression1:
  	if_suite
  elif expression2:
  	elif_suite
  else:
  	else_suite
  ```

    ```python
    # if嵌套
    if expression1:
        if_suite
        if expression2:
            if_suite
        else:
        else_suite
    else:
        else_suite
    ```

3. while循环语句

  ```python
  while expression:
  	while_suite  #循环执行到表达式的值为0或False
  ```

  要在遍历列表的同时对其进行修改，可使用while 循环。

  for 循环是一种遍历列表的有效方式，但在for 循环中不应修改列表，否则将导致Python难以跟踪其中的元素。

4. for循环

    - python中的for接受可迭代对象作为其参数，类似于foreach。注意：for语句的**冒号`:`**

    ```python
    >>> for item in ['Python', 'is', 'cool', '!']:
    	print item,  #print语句默认会给每一行添加一个换行符，添加逗号`,`可以不换行。并且在输出的元素之间自动添加一个空格
    	
    Python is cool !
    
    >>> str='Python'
    >>> for each in str: #获取字符串每个字符
    	print each,
    		
    P y t h o n
    
    >>> for each in range(len(str)): #rang()函数和len()函数用于字符串索引
    	print str[each],
    
    	
    P y t h o n
    ```

    - Python2.3新增enumerate()函数，可同时获得字符串的索引和字符

    ```python
    >>> for i, char in enumerate(str):
    	print i, char
    
    	
    0 P
    1 y
    2 t
    3 h
    4 o
    5 n
    ```

    - 内建函数range()生成数值范围内的序列

    ```python
    >>> for each in range(10):
    	print each,
    
    	
    0 1 2 3 4 5 6 7 8 9
    ```

    - 完整的for循环语句：一般用于判断某个字典中是否存在指定的值 

     ```python
     for 变量 in 集合：
         循环体代码
         (break)
     else:
         只有在for循环全部执行完毕后，才会执行该部分代码；若是for循环中使用break推出循环，该部分代码将不会执行。
     ```



## 十一. 继续 \ ##

1. 过长的语句可以使用反斜杠分解成几行。

	```python
	if (weather_is_not == 1) and \
		(shark_warnings == 0):
			send_goto_beach_mesg_to_paper()
	```

2. 在使用闭合操作符 (), [], {}, 单一语句可以多行书写。（推荐使用）

	```python	
	# 给一些变量赋值
	a, b, c, d = (1,
		      'string', 20.0, -1.00)
	```

3. 三引号包括下的字符串可以多行书写。
	
	```python
	>>> print '''Hi there, this is a long message
	for you that gose over multiple lines!'''

	Hi there, this is a long message
	for you that gose over multiple lines!
	```

## 十二. 模块 ##
1. 导入整个模块
   - 每一个以`.py`结尾的Python脚本文件都是一个模块，模块名也是标识符: module_name.py

   - 模块中定义的**全局变量，函数**可提供外部使用

   - 模块里的代码可以是直接执行的脚本，也可以是类似库函数的代码，从而可以被别的模块导入使用。

   - 当一个模块变得过大，并且驱动太多功能的话，应该考虑拆些代码出来另建模块。

   - 模块以磁盘文件的形式存在；

   - 每个模块也都应包含一个文档字符串，对其中的类可用于做什么进行描述。

   - 导入模块:
        ```python
        import module_name
        ```

   - 调用模块中任意的函数：
        ```python
        module_name.function_name()
        ```

   - 模块指定别名
        ```python
        import module_name as mn
        ```
2. 导入特定的函数	
   - 单个函数：
   	
   	```python
   	from module_name import function_name  # 这里的函数名不加()
   	```
   	
   - 多个函数：逗号分隔函数名，从模块中导入任意数量的函数
     ```python
     from module_name import function_0,function_1,...  # 这里的函数名不加()
     ```

   - 这种语法，调用函数只需指定名称即可：function_name()
   - 函数别名：导入的函数的名称可能与程序中现有的名称冲突，或者函数的名称太长，可指定简短而独一无二的别名
     ```python
     from module_name import function_name as fun
     ```

3. 导入模块中的所有函数
  - 使用星号（* ）运算符可让Python导入模块中的所有函数：
       ```python
       	from module_name import *
       ```
  - 这种语法，调用函数只需指定名称即可：function_name()
  - 注：使用并非自己编写的大型模块时，最好不要采用这种导入方法：如果模块中有函数的名称与你的项目中使用的名称相同，可能导致意想不到的结果：Python可能遇到多个名称相同的函
    数或变量，进而覆盖函数，而不是分别导入所有的函数。

4. 最佳的做法：

  - 导入整个模块并使用句点表示法

    ```python
    import module_name
    	module_name.function_name()
    ```


  - 只导入需要使用的函数
     ```python
     from module_name import function_0,function_1,... # 这里的函数名不加()
     from module_name import function_0 as fun_0, function_1 as fun_1, ...#给多个函数指定别名
     #函数调用
     function_name()
     ```
  - import 语句都应放在文件开头，唯一例外的情形是，在文件开头使用了注释来描述整个程序
  - 给模块指定描述性名称，且只在其中使用小写字母和下划线

## 十三. 内存管理 ##

1. 变量名，变量类型无需事先声明。对象的类型和内存占用都是运行时确定的。
2. 变量分配内存时是在借用系统资源。Python解释器承担内存管理的任务。
3. 引用计数：追踪内存中的对象，Python使用了引用计数技术，记录所有使用中的对象有多少引用。
    - 增加引用计数：

        1). 对象被创建并赋值给变量；    

        ```python 
        x=3.14 
        ```
        2). 同一对象又被赋值给其他变量；
    
        ```python 
        y = x 
        ```

        3). 作为参数传递给函数或类实例；
    
        ```python 
        funtion(x)
        ```
    
        4). 成为容器对象的一个元素。
    
        ```python 
        myList = [123, x, 'yz']
        ```
    - 减少引用计数：
    
        1). 引用离开其作用范围（函数运行结束，所有局部变量自动销毁）；
    
        2). 变量被赋值给另外一个对象时；
    
        ```python 
        x=3.14
        x=123  #此时对象3.14引用计数减1
        ```
    
        3). 对象的别名被显示销毁；
    
        ```python 
        del x 
        ```
    
        4). 对象被从一个窗口对象中移除
    
        ```python 
        myList.remove(x)
        ```
    
        5). 窗口对象本身被销毁
    
        ```python 
        del myList 
        ```
4. del语句del语句会删除对象的一个引用

  ```python
  >>> a = [-1, 1, 66.25, 333, 333, 1234.5]
  >>> del a[0]
  >>> a
  [1, 66.25, 333, 333, 1234.5]
  >>> del a[2:4]
  >>> a
  [1, 66.25, 1234.5]
  >>> del a[:]
  >>> a
  []
  >>> del a
  ```

5. 垃圾收集

    垃圾收集器实际是一个引用计数器和一个循环垃圾收集器，用来寻找引用计数为0的对象，也负责引用计数大于0但应该被销毁的对象。

## 十四.函数

- 每个函数都应只负责一项具体的工作
- 编写函数时，可以以各种方式混合使用位置实参、关键字实参和任意数量的实参
- 给函数指定描述性名称，且只在其中使用小写字母和下划线

1. ##### 函数格式

    ```python
    def function(parameters):
        """注释"""
        code...
    ```
   - Python的代码块不使用大括号 {} 来控制类、函数以及其他逻辑判断。python是用缩进来写模块。
      缩进的空白数量是可变的，但是所有代码块语句必须包含相同的缩进空白数量，这个必须严格执行。

      **IndentationError: unindent does not match any outer indentation level** 错误表明，你使用的缩进方式不一致

   - 多行语句：使用**斜杠(\\)**将多行语句连接成一条Python语句。语句中包含 **[]**, **{}** 或 **()** 括号就不需要使用多行连接符(\\)。

   - PyCharm添加函数参数说明的方式：选中函数名，点击💡，选择"Add parameters to docstring"。
2. ##### 函数参数

###### 1) 位置实参

​	可根据需要使用任意数量的位置实参，Python将按顺序将函数调用中的实参关联到函数定义中相应的形参.

  ```python
   def function(parameter1, parameter2,... ):
        code
  ```
###### 	2) 关键字实参

​	名称=值，等号两边不要有空格，与实参的顺序无关。

   ```python
    #函数定义方式
    def function(parameter1, parameter2,... ):
        code
    
    #函数调用时，指定名称=值
    function(parameter1='value1', parameter2='value2', ...)
   ```
###### 3) 设置默认值

​	编写函数时，可给任意形参指定默认值。

```python
  def function(parameter1, parameter2='Default2', ...):
      code
```

a. 在形参列表中必须先列出没有默认值的形参，**python依然将这个实参视为位置实参**，再列出有默认值的实参。
b. 使用默认值来让实参变成可选的，只需在必要时才提供额外的信息，
c. 一般默认值设置为空字符串，Python将非空字符串解读为True
d. 给形参指定默认值时，等号两边不要有空格

###### 4) 等效的函数调用

​	可混合使用位置实参、关键字实参和默认值

```python
def function(parameter1, parameter2='Default2', ...):
	code
	
#函数参数传递方式:
function(vlaue1, value2, ...) #位置实参
function(parameter1='value1', parameter2='value2', ...) #关键字实参
function(vlaue1, ...) #parameter2使用默认值Default2
```
###### 5) 返回值

1. return 语句将值返回到调用函数的代码行
2. 函数可返回任何类型的值，包括列表和字典等较复杂的数据结构了；
	

###### 6) 传递列表

1. 向函数传递列表，列表可包含字符串、数字或复杂的对象（如字典）
2. 函数可对其进行修改。在函数中对这个列表所做的任何修改都是永久性的，能够高效地处理大量的数据。
3. 可向函数传递列表的副本`function_name(list_name[:])`，函数所做的任何修改只影响副本
4. 但是让函数使用原列表可避免花时间和内存创建副本，从而提高效率，在处理大型列表时尤其如此。

###### 7) 传递任意数量的实参

   1. Python允许函数从调用语句中收集任意数量的实参
       ```python
       	def make_pizza(*toppings):
       		"""打印顾客点的所有配料,无法预先确定顾客要多少种配料"""
       		print(toppings)
       		
       	make_pizza('pepperoni')
       	make_pizza('mushrooms', 'green peppers', 'extra cheese')
       ```
       ***toppings** 中的星号让Python创建一个名为toppings的空元组，并将所有实参都封装到元组toppings中。
       元组中可以包含不同类型的数据，所以参数可以使不同数据类型。但是不利于批量处理，通常传递同一类型。

   2. 位置实参&任意数量实参：	
          - 传递位置实参和任意数量实参，必须在函数定义中将接纳任意数量实参的形参放在最后。

          - Python先匹配位置实参和关键字实参，再将余下的实参都收集到最后一个形参中。

           ```python
           def make_pizza(size, *toppings):
           	"""size是位置实参（不可为空），传递的余下参数都收集到最后一个形参toppings中，可为空"""
           	code
           	
           make_pizza(16, 'pepperoni')
           make_pizza(12, 'mushrooms', 'green peppers', 'extra cheese')
           ```

   3. 任意数量的关键字实参：
        - 传递任意数量的关键字实参，接受任意数量的键—值对：
        - 形参**user_info 中的两个星号让Python创建一个名为user_info的空字典，并将收到的所有名称—值对都封装到这个字典中。

```python
 def build_profile(first, last, **user_info):
    """定义要求提供名和姓, 同时允许用户根据需要提供任意数量的名称—值对"""
	profile = {} #创建空字典
	profile['first_name'] = first
	profile['last_name'] = last
		
	#遍历字典，要使用字典方法：items()
	for key, value in user_info.items():
		profile[key] = value

	return profile
		
user_profile = build_profile('albert','einstein',location='princeton',field='physics')
print(user_profile)
```

###### 8) 关键字、函数和方法的区别 

- 关键字（python 3.7 已有35个）
  
  ```python
    >>> import keyword
    >>> print(keyword.kwlist)
    ['False', 'None', 'True', 'and', 'as', 'assert', 'async', 'await', 'break', 'class', 'continue', 'def', 'del', 'elif', 'else', 'except', 'finally', 'for', 'from', 'global', 'if', 'import', 'in', 'is', 'lambda', 'nonlocal', 'not', 'or', 'pass', 'raise', 'return', 'try', 'while', 'with', 'yield']
    >>> print(len(keyword.kwlist))
    35
  ```
  
- 函数

    封装了独立的功能，可以直接调用：函数名(参数)。例如：print函数、input函数、len函数等，不需要对象调用。
  
- 方法

    **类中的函数成为方法**，需要对象调用，针对对象要做的操作：**对象.方法名(参数)**

## 十五. 类

##### 1. 创建类

- 类名应采用驼峰命名法，而不使用下划线
- 实例名和模块名都采用小写格式，并在单词之间加上下划线
- 每个类，都应紧跟在类定义后面包含一个文档字符串，简要地描述类的功能

```python
class Class_name():  #类名的首字母大写，()中可传递参数
    """文档字符串，对这个类的功能作描述"""
    def __init__(self，形参1, 形参2, ...):  #self是指向实例本身的引用，让实例能够访问类中的属性和方法
       """初始化属性，类中的每个属性都必须有初始值"""
        self.属性1 = 形参1
        self.属性2 = 形参2
        ...
        self.属性 = 默认值
        code
        
     def function(self):
        code
        #在类中访问属性，使用 self.属性
```

##### 2.创建实例

```python
instance_name = Class_name(实参1，实参2，...) # 方法__init__()使用实参的值来设置属性，返回一个实例存在变量instance_name中。
```

##### 3. 继承

创建子类时，父类必须包含在当前文件中，且位于子类前面

```python
"""模块级文档字符串，对该模块的内容做了简要的描述: 一个可用于表示汽车的类"""

class Car:  # 父类

    def __init__(self, maker, model, year):
        self.maker = maker
        self.model = model
        self.year = year
        self.distance = 0  # 给属性指定默认值

    def get_info(self):
        full_name = str(self.maker)+' '+str(self.model)+' '+str(self.year)+' '+str(self.distance)
        return full_name.title()

    def update_distance(self, miles):
        self.distance = miles

#子类
class ElectricCar(Car):  # 继承父类的方式

    def __init__(self, maker, model, year):
        """初始化父类的属性"""
        super().__init__(maker, model, year)
		self.battery = battery  # 子类的新属性

    def get_battery(self):  # 子类的新方法
        print('This car has a ' + str(self.battery) + '-kWh battery')

my_car = ElectricCar('Audi', 'RS7', '2019', 70)
# my_car.distance = '100 miles'      # 直接修改属性的值
my_car.update_distance('101 miles')  # 通过方法修改属性的值
print(my_car.get_info())
my_car.get_battery()
```

##### 4.重写

在子类中定义一个与父类方法同名的函数，即重写。

##### 5.将实例用作属性

```python
class Car:
    --snip--


class Battery:
    def __init__(self, battery_size=70):
        self.battery_size = battery_size

    def get_battery(self):
        print('This car has a ' + str(self.battery_size) + '-kWh battery')


class ElectricCar(Car):

    def __init__(self, maker, model, year):
        super().__init__(maker, model, year)
        self.battery = Battery()  # Battery实例作为属性


my_car = ElectricCar('Audi', 'RS7', '2019')
my_car.battery.get_battery()  # 调用Battery类的方法
```

##### 6.导入类

1. ###### 导入单个类

   在一个模块中可以存储多个类

   ```python
   from module import Class
   ```

2. ###### 从一个模块中导入多个类

   ```python
   from module import Class1，Class2, ...
   ```

3. ###### 导入整个模块

   - 导入整个模块，使用句点表示法访问需要的类。
   - 创建类实例的代码都包含模块名，不会与当前文件使用的任何名称发生冲突。
   - 需要从一个模块中导入很多类时，最好导入整个模块，并使用 module_name.class_name 语法来访问类。

   ```python
   import module
   class_instance = module.Class()  # 创建实例
   class_instance.function()  # 实例调用方法
   ```

4. ###### 导入模块中的所有类

   ```python
   from module_name import *  # 不推荐使用
   ```

##### 7. Python标准库

-   Python标准库是一组模块，安装的Python都包含
-  先编写导入标准库模块的import 语句，再添加一个空行，然后编写导入你自己编写的模块的import 语句