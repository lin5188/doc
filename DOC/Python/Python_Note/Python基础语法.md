Python基础语法.md
===
全文概要
```
* 缩进、注释、命名、变量、保留字
* 数据类型、字符串、整数、浮点数、列表
* 赋值语句、分支语句、函数
* input()、print()、eval()、print()格式化
```
> 编程解决问题的6个步骤
>> 分析问题：分析问题的计算部分，`想清楚`  
>> 划分边界：划分问题的功能边界，`规划IPO（输入、处理、输出）`  
>> 设计算法：设计问题的求解算法，`关注算法`   
>> 缩写程序：编写问题的计算程序，`编程序`  
>> 调试测试：调试程序使正确运动，`运行调试`  
>> 升级维护：适应问题的升级维护，`更新完善`

实例1：温度转换
---

```python
#TempConvert.py
TempStr = input("请输入带有符号的温度值：")
if TempStr[-1] in ['F','f']:
    C = (eval(TempStr[0:-1]) - 32)/1.8
    print("转换后的温度是{:.2f}C".format(C))
elif TempStr[-1] in ['C','c']:
    F = 1.8*eval(TempStr[0:-1]) + 32
    print("转换后的温度是{:.2f}F".format(F))
else:
    print("输入格式错误")
```
> 举一反三  

- 输入输出的改变
    - 温度数值与温度标识之间关系的设计可以改变
    - 标识改变放在温度数值之前：C82，F28
    - 标识字符改变为多个字符：82Ce，28F

- 计算问题的扩展
    - 温度转换问题是各类转换问题的代表性问题
    - 货币转换、 长度转换、重量转换、面积转换…
    - 问题不同，但程序代码相似

Python程序语法元素分析
---
- 程序的格式框架
- 命名与保留字
- 数据类型
- 语句与函数
- Pyhton程序的输入输出
-  "温度转换"代码分析

### ![][A1] 程序的格式框架

---

- 高亮
- 缩进
    - 严格明确   
    缩进是语法的一部分，缩进不正确程序运行错误
    - 所属关系   
    表达代码间包含和层次关系的唯一手段
    - 长度一致   
    程序内一致即可，一般4个空格或1个TAB
- 注释  
不被程序执行的辅助性说明信息

    - 单行注释  
    以#开头，其后内容为注释  

    - 多行注释  
    以'''开头和结尾(双引号键）

### ![][A1] 变量命名与保留字（关键字）

---

   - 变量命名  
       - __*规则：*__ 大小写字母、数字、下划线和汉字等字符及组合  
        如：TempStr，Python_Great，这是门Python好课
    
       - __*注意事项：*__ 大小写敏感、首字符不能是数字、不与保留字相同  
        Python和python是不同变量，123Python是不合法的
    
   - 保留字（关键字）
        - Python语言有33个保留字（也叫关键字）
        ![][1]
            
        - 在Python基础语法不涉及的保留字有下面7个：  
            assert、class、is、raise、with、yield、nonlocal


### ![][A1] 数据类型  

---

程序设计语言不允许存在语法歧义，需要定义数据的形式，让计算机可以理解的表达形式

``10,011,101``

#### 字符串类型及操作

----

由0个或多个字符组成的有序字符序列  

- 字符串有 2类共4种 表示方法    
    - 单行字符串：有一对单引号或一对双引号表示    
    
    ```"请输入带有符号的温度值：" 或者 'C'```
    - 多行字符串：有一对三单引号或三双引号表示
    ```
    '''python  
                语言'''
    ```            
    - 如果希望在字符串中包含双引号或单引号呢？  
    ``` '这里有个双引号(")'  或者 "这里有个单引号(')"``` 

    - 如果希望在字符串中既包含双引号又包含单引号呢？  
    ``` '''这里有个双引号(")又有个单引号(')'''``` 
              
- 字符串是字符的有序序列，可以对其中的字符进行索引


    "请"是"请输入带有符号的温度值："的第0个字符

- 字符串的序号

![][2]

> 字符串的使用

使用[]获取字符串中一个或多个字符

- 索引：返回字符串中单个字符 `<字符串>[M]`

   
    "请输入带有符号的温度值："[0]  或者  TempStr[-1]

- 切片：返回字符串中一段字符子串  `<字符串>[M:N]`或`<字符串>[M:N:K]`根据步长对字符串切片

    `"请输入带有符号的温度值："[1:3]  或者  TempStr[0:-1]`  
    - <字符串>[M:N] ，M缺失表示至开头，N缺失表示至结尾  
    `"0123456789"[:3]` 结果是`"012"`  
    
   -  <字符串>[M:N:K],根据步长K对字符串切片
   `"0123456789"[1:8:2]` 结果是`"1357"`
    - **字符串倒序输出**
    "0123456789"[::-1] 结果是"9876543210"
- 特殊字符
    - 转义符\
        - 转义符表达特定字符的本意  
        `"这里有个双引号(\")"` 结果是 `这里有个双引号(")`  
        -  转义符形成一些组合，表达一些不可打印的含义  
        `\b回退，\n换行（光标移动到下行首），\r回车（光标移动到本行首）`     
         
- 字符串操作符  
![][9]

- 例子：获取星期字符串  
```python
#WeekNamePrintV1.py
weekStr = "星期一星期二星期三星期四星期五星期六星期日"
weekID = eval(input("请输入星期数字（1-7）："))
pos = (weekID - 1) * 3
print(weekStr[pos:pos+3])
```
```python
#WeekNamePrintV2.py
weekStr = "一二三四五六日"
weekID = eval(input("请输入星期数字（1-7）："))
print("星期" + weekStr[weekID-1])
```
- **字符串处理函数**  
![][10]
![][11]
![][12]  
`end=""` 表示在同一行输出
- **字符串处理方法**  
一些以方法形式提供的字符串处理功能
![][13]
![][14]
![][15]

- **字符串类型的格式化**  
格式化是对字符串进行格式表达的方法
    - 字符串格式化使用`.format()`方法，用法如下：  
    `<模板字符串>.format(<逗号分隔的参数>)`
    - 槽
    ![默认][16]
    ![][17]
        - 槽内部对格式化的配置方式  
        `{<参数序号>:<格式控制标记>}`  
        ![][18]
        - 例如：  
        ![][19]


#### 数字类型及操作

---
- 整数  
    - 与数学中的整数一致，可正可负，没有取值范围限制
    - 32 或者 -89
    - 4种进制表示形式：
        - 十进制：1010，99，-217
        - 二进制，以0b或0B开头：0b010,-0B101(零B)
        - 八进制，以0o或0O开头：0o123,-0O456（零欧）
        - 十六进制，以0x或0X开头：0x9a,-0X89(零x)

- 浮点数  
   - 与数学中的实数一致，带有小数部分
   - 1.8 或者 -1.8  或者 -1.0
   - 取值范围和小数精度都存在限制，但常规计算可忽略
   - 取值范围数量级约-10^308至10^308，精度数量级10^-16
   - 浮点数间运算存在不确定尾数，但不是bug。需要用`round()`取值。
        - `>>>0.1 + 0.2 == 0.3
            False
        - `>>>round(0.1+0.2,1) == 0.3
            True
   - 浮点数可以采用科学计算法表示
        - 使用字母e或E作为幂的符号，以10为基数，格式如下  
        `<a>e<b>`   表示a*10^b    
        - 例如：4.3e-3 值为0.0043  
        9.6E5 值为960000.0

                     
- 复数
    - 与数学中复数的概念一致
    - 定义 *j* = $\sqrt -1$,以此为基础，构建数学体系
    - a+b*j*被称为复数，其中，a是实部，b是虚部
    - 实例：z = 1.23e-4 + 5.6e+89*j*
        - 实部是什么？`z.real`获得实部
        - 虚部是什么？ `z.imag`获得虚部
        
- **数值运算操作符**  
    - 操作符是完成运算的一种符号体系
    ![][3]  
    ![][4]
    - 二元操作符有对应的增强赋值操作符
    ![][5]
    - 类型间可进行混合运算，生成结果为“最宽”类型
        - 三种类型存在一种逐渐“扩展”或“变宽”的关系  
        `整数 -> 浮点数 -> 复数`
        - 例如：123 + 4.0 = 127.0 （整数+浮点数=浮点数）

-  **数字运算函数**  
一些以函数形式提供的数值运算功能  
![][6]  
![][7]  
![][8]  
 

#### 列表类型

---
由0个或多个数据组成的有序序列

- 列表使用[]表示，采用逗号(,)分隔各元素


    ['F','f']表示两个元素'F','f'
    
- 使用保留字 in 判断一个元素是否在列表中


    TempStr[-1] in ['C','c']判断前者是否与列表中某个元素相同
    
### ![][A1] 语句与函数

---

#### 赋值语句  

---
由赋值符号构成的一行代码

- 赋值语句用来给变量赋予新的数据值


    C = (eval(TempStr[0:-1]-32)/1.8
    
- 赋值语句右侧的数据类型同时作用于变量


    TempStr = imput("") 
    
    #imput()返回一个字符串，TempStr也是字符串

#### 分支结构

---
由判断条件决定程序运行方向的语句

- 使用保留字if elif else构成条件判断的分支结构


    if TempStr[-1] in ['F','f']:
    
    #如果条件为True则执行冒号后语句
- 每个保留字所在行最后存在一个冒号（:）,语法的一部分，不能省略

** 冒号及后续缩进用来表示后续语句与条件的所属关系

#### 函数


---
根据输入参数产生不同输出的功能过程

- 类似数学中的函数，y = f(x)


    print("输入格式错误") 
    
    #打印输出“输入格式错误”

- 函数采用`<函数名>(<参数>)`方式使用


    eval(TempStr[0:-1])  其中TempStr[0:-1]是参数


### ![][A1] Python程序的输入输出

---
#### _**输入函数：input()**_  

`从控制台获得用户输入的函数`

- input()函数的使用格式：


    <变量> = input(<提示信息字符串>)

- 用户输入的信息以字符串类型保存在<变量>中


    TempStr = input("请输入")     
    #TempStr保存用户输入的信息


#### _**输出函数：print()**_
`以字符形式向控制台输出结果的函数`

- print()函数的基本使用格式：


    print(<拟输出字符串或字符串变量>)

- 字符串类型的一对引号仅在程序内部使用，输出无引号


    print("输入格式错误")
    
    # 向控制台输出:  输入格式错误

- >print()函数的格式化：


    print("转换后的温度是{:.2f}C".format(C))
    
    # {}表示槽，将后续的变量填充到槽中
    # {:.2f} 表示将变量C填充到这个位置时取小数点后2位
    如果C的值是123.456789，则输出结果为：
    
    转换后的温度是123.45C

#### _**评估函数 eval()**_
`去掉参数最外侧引号并执行余下语句的函数`

- >eval()函数的基本使用格式： 

 
    eval(<字符串或字符串变量>)
    
    eval(TempStr[0:-1])
    # 如果TempStr[0:-1]值是"12.3"，输出是：12.3
>> 例：

    >>>eval("1")
    1
    >>>eval("1+2")
    3
    >>>eval('"1+2"')
    '1+2'
    >>>eval('print("Hello")')
    Hello





[1]:
https://github.com/lin5188/XH_Notes/blob/master/DOC/Python/Python_Note/%E5%9B%BE%E7%89%87/Python%E8%AF%AD%E8%A8%80%E7%A8%8B%E5%BA%8F%E8%AE%BE%E8%AE%A1/1.png

[2]:
https://github.com/lin5188/XH_Notes/blob/master/DOC/Python/Python_Note/%E5%9B%BE%E7%89%87/Python%E8%AF%AD%E8%A8%80%E7%A8%8B%E5%BA%8F%E8%AE%BE%E8%AE%A1/2.png

[3]:
https://github.com/lin5188/XH_Notes/blob/master/DOC/Python/Python_Note/%E5%9B%BE%E7%89%87/Python%E8%AF%AD%E8%A8%80%E7%A8%8B%E5%BA%8F%E8%AE%BE%E8%AE%A1/3.png

[4]:
https://github.com/lin5188/XH_Notes/blob/master/DOC/Python/Python_Note/%E5%9B%BE%E7%89%87/Python%E8%AF%AD%E8%A8%80%E7%A8%8B%E5%BA%8F%E8%AE%BE%E8%AE%A1/4.png  
[5]:
https://github.com/lin5188/XH_Notes/blob/master/DOC/Python/Python_Note/%E5%9B%BE%E7%89%87/Python%E8%AF%AD%E8%A8%80%E7%A8%8B%E5%BA%8F%E8%AE%BE%E8%AE%A1/5.png  
[6]:
https://github.com/lin5188/XH_Notes/blob/master/DOC/Python/Python_Note/%E5%9B%BE%E7%89%87/Python%E8%AF%AD%E8%A8%80%E7%A8%8B%E5%BA%8F%E8%AE%BE%E8%AE%A1/6.png  
[7]:
https://github.com/lin5188/XH_Notes/blob/master/DOC/Python/Python_Note/%E5%9B%BE%E7%89%87/Python%E8%AF%AD%E8%A8%80%E7%A8%8B%E5%BA%8F%E8%AE%BE%E8%AE%A1/7.png  
[8]:
https://github.com/lin5188/XH_Notes/blob/master/DOC/Python/Python_Note/%E5%9B%BE%E7%89%87/Python%E8%AF%AD%E8%A8%80%E7%A8%8B%E5%BA%8F%E8%AE%BE%E8%AE%A1/8.png  
[9]:
https://github.com/lin5188/XH_Notes/blob/master/DOC/Python/Python_Note/%E5%9B%BE%E7%89%87/Python%E8%AF%AD%E8%A8%80%E7%A8%8B%E5%BA%8F%E8%AE%BE%E8%AE%A1/9.png  
[10]:
https://github.com/lin5188/XH_Notes/blob/master/DOC/Python/Python_Note/%E5%9B%BE%E7%89%87/Python%E8%AF%AD%E8%A8%80%E7%A8%8B%E5%BA%8F%E8%AE%BE%E8%AE%A1/10.png  
[11]:
https://github.com/lin5188/XH_Notes/blob/master/DOC/Python/Python_Note/%E5%9B%BE%E7%89%87/Python%E8%AF%AD%E8%A8%80%E7%A8%8B%E5%BA%8F%E8%AE%BE%E8%AE%A1/11.png  
[12]:
https://github.com/lin5188/XH_Notes/blob/master/DOC/Python/Python_Note/%E5%9B%BE%E7%89%87/Python%E8%AF%AD%E8%A8%80%E7%A8%8B%E5%BA%8F%E8%AE%BE%E8%AE%A1/12.png  
[13]:
https://github.com/lin5188/XH_Notes/blob/master/DOC/Python/Python_Note/%E5%9B%BE%E7%89%87/Python%E8%AF%AD%E8%A8%80%E7%A8%8B%E5%BA%8F%E8%AE%BE%E8%AE%A1/13.png  
[14]:
https://github.com/lin5188/XH_Notes/blob/master/DOC/Python/Python_Note/%E5%9B%BE%E7%89%87/Python%E8%AF%AD%E8%A8%80%E7%A8%8B%E5%BA%8F%E8%AE%BE%E8%AE%A1/14.png  
[15]:
https://github.com/lin5188/XH_Notes/blob/master/DOC/Python/Python_Note/%E5%9B%BE%E7%89%87/Python%E8%AF%AD%E8%A8%80%E7%A8%8B%E5%BA%8F%E8%AE%BE%E8%AE%A1/15.png  
[16]:
https://github.com/lin5188/XH_Notes/blob/master/DOC/Python/Python_Note/%E5%9B%BE%E7%89%87/Python%E8%AF%AD%E8%A8%80%E7%A8%8B%E5%BA%8F%E8%AE%BE%E8%AE%A1/16.png  
[17]:
https://github.com/lin5188/XH_Notes/blob/master/DOC/Python/Python_Note/%E5%9B%BE%E7%89%87/Python%E8%AF%AD%E8%A8%80%E7%A8%8B%E5%BA%8F%E8%AE%BE%E8%AE%A1/17.png  
[18]:
https://github.com/lin5188/XH_Notes/blob/master/DOC/Python/Python_Note/%E5%9B%BE%E7%89%87/Python%E8%AF%AD%E8%A8%80%E7%A8%8B%E5%BA%8F%E8%AE%BE%E8%AE%A1/18.png  
[19]:
https://github.com/lin5188/XH_Notes/blob/master/DOC/Python/Python_Note/%E5%9B%BE%E7%89%87/Python%E8%AF%AD%E8%A8%80%E7%A8%8B%E5%BA%8F%E8%AE%BE%E8%AE%A1/19.png  


[A1]:
https://github.com/lin5188/XH_Notes/blob/master/DOC/others/icons/%E6%B0%B4%E6%9E%9Cicon/%E8%A5%BF%E7%93%9C-16.png
