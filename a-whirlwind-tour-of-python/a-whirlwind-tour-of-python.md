# A Whirlwind Tour of Python

- [A Whirlwind Tour of Python](#a-whirlwind-tour-of-python)
  - [1. Python 簡介](#1-python-簡介)
  - [2. 執行 Python](#2-執行-python)
  - [3. 基本語法](#3-基本語法)
  - [4. 變數和物件](#4-變數和物件)
  - [5. 運算子](#5-運算子)
  - [6. 簡單型別 (Simple Types)](#6-簡單型別-simple-types)
    - [整數 (Integer)](#整數-integer)
    - [浮點數 (Float)](#浮點數-float)
    - [複數 (Complex)](#複數-complex)
    - [字串 (String)](#字串-string)
    - [None Type](#none-type)
    - [布林值 (Boolean)](#布林值-boolean)
  - [7. 複合型別 (Compound Types)](#7-複合型別-compound-types)
    - [列表 (List)](#列表-list)
    - [元組 (Tuple)](#元組-tuple)
    - [集合 (Set)](#集合-set)
    - [字典 (Dictionary)](#字典-dictionary)
    - [其他](#其他)
  - [8. 控制結構](#8-控制結構)
    - [條件語句](#條件語句)
    - [for 迴圈](#for-迴圈)
    - [while 迴圈](#while-迴圈)
    - [其他](#其他-1)
  - [9. 函式](#9-函式)
    - [調用函式](#調用函式)
    - [使用 `def` 關鍵字](#使用-def-關鍵字)
    - [使用 `lambda` 關鍵字](#使用-lambda-關鍵字)
  - [10. 例外處理 (Exception Handling)](#10-例外處理-exception-handling)
    - [捕獲例外](#捕獲例外)
    - [拋出例外](#拋出例外)
    - [訪問例外資訊](#訪問例外資訊)
    - [自定義例外](#自定義例外)
  - [11. 迭代器 (Iterator)](#11-迭代器-iterator)
    - [實用的迭代器](#實用的迭代器)
  - [12. 列表推導 (List Comprehension)](#12-列表推導-list-comprehension)
  - [13. 生成器 (Generator)](#13-生成器-generator)
    - [生成器表達式 (Generator Expression)](#生成器表達式-generator-expression)
    - [生成器函式 (Generator Function)](#生成器函式-generator-function)
  - [14. 模組和套件 (Module and Package)](#14-模組和套件-module-and-package)
    - [匯入模組](#匯入模組)
    - [匯入第三方套件](#匯入第三方套件)
    - [自定義模組](#自定義模組)
    - [自定義套件](#自定義套件)
  - [15. 字串處理和正則表示式](#15-字串處理和正則表示式)
    - [正則表示式 (Regular Expressions)](#正則表示式-regular-expressions)
  - [16. 資料科學工具概覽](#16-資料科學工具概覽)
    - [NumPy](#numpy)
    - [Pandas](#pandas)
    - [Matplotlib](#matplotlib)
    - [SciPy](#scipy)
  - [17. 更多學習資源](#17-更多學習資源)
    - [Python 語法](#python-語法)
    - [資料科學和科學計算領域](#資料科學和科學計算領域)

## 1. Python 簡介

- Python 是一種高階程式語言，其魅力在於它的語法簡潔，且龐大的生態系可以在各種不同的領域中使用
- Python 和其他程式語言的一個重要差別在於它是直譯型語言，而不是編譯型語言。這意味著 Python 的程式碼在執行時會被直譯器「逐行」解釋執行，而不是像編譯型語言一樣先編譯成機器碼再一起執行
- Python 的官方網站是 [python.org](https://www.python.org/)，在這裡可以下載到 Windows、macOS、Linux 等不同作業系統的版本
- Windows 的安裝可以參考 [在Windows底下最適當安裝Python環境的方法](https://ithelp.ithome.com.tw/articles/10210071)

## 2. 執行 Python

以下是常見的執行 Python 的方法：
1. 在命令列中執行 `python` 指令，啟動互動式直譯器
2. 在命令列中執行 `python <filename>.py` 指令，執行一個 Python 腳本
3. 透過 Jupyter Notebook 執行 Python 腳本

## 3. 基本語法

- 用 `#` 表示註解
- 用「換行」表示語句結束
- 在同一行中有多個語句時，語句之間用分號隔開，例如 `print("Hello"); print("World")` (但不推薦這種風格)
- 小括號 `()` 用來對語句分組，例如`2 * (3 + 4)`；或是用於函式呼叫，例如`print("Hello")`
- 用「縮排」表示程式區塊，習慣上縮排是使用 4 個空格

## 4. 變數和物件

- Python 是一種物件導向的程式語言，一切都是物件，每個物件擁有自己的記憶體位置
- 與 C++、Java 等語言不同，Python 的變數並不是代表某個物件本身，而是代表指向某個物件的指標 (類似於 C++、Java 的 reference)
- 變數根據指標的特性分成「可變物件 (mutable object)」和「不可變物件 (immutable object)」兩種：
  - 可變物件：變數指向的物件本身可以被修改，例如 list、dict、set 等資料類型的物件
  - 不可變物件：變數指向的物件本身不能被修改，如果需要修改，只能重新賦值給變數，例如 int、float、str、tuple 等資料類型的物件
- 當你賦值給一個指向可變物件的變數時，Python 並不是將值複製到變數中，而是讓變數指向該值所對應的物件
- 當你賦值給一個指向不可變物件的變數時，Python 會重新賦值給變數，讓變數指向新的物件

```python
# 變數 x 指向物件 [1, 2, 3]，其中 [1, 2, 3] 是可變物件(list)
x = [1, 2, 3]
# 變數 y 指向物件 [1, 2, 3]
y = x
# 修改變數 x 指向的物件，變數 y 指向的物件也會被修改
x[0] = 99
print(x)  # [99, 2, 3]
print(y)  # [99, 2, 3]
```

```python
# 變數 a 指向物件 10，10 是不可變物件(int)
a = 10
# 變數 b 指向物件 10
b = a
# 變數 a 指向新的物件 99
a = a + 10
# 此時會發現 b 的值仍然是 10，而不是 20
print(a)  # 20
print(b)  # 10
```

- Python 是有資料型別的，但型別是連結到物件，而不是變數
- 變數可以自由地指向不同的物件，即變數的型別在執行時才會被確定，因此 Python 被稱為是「動態型別 (dynamic typed)」語言
- 可以使用 `type()` 函式來查看變數的型別

```python
x = 10
print(type(x))  # <class 'int'>
x = "Hello"
print(type(x))  # <class 'str'>
x = [1, 2, 3]
print(type(x))  # <class 'list'>
```

## 5. 運算子

- 算術運算子：`+`、`-`、`*`、`/`、`% (餘數)`、`** (指數)`、`// (向下整除)`、`@ (矩陣乘法)`
- 位元運算子：`& (AND)`、`| (OR)`、`~ (NOT)`、`^ (XOR)`、`<< (左移)`、`>> (右移)`
- 賦值運算子：`=`、`+=`、`-=`、`*=`、`/=`、`%=`、`**=`、`//=`
- 比較運算子：`==`、`!=`、`>`、`<`、`>=`、`<=`
- 布林運算子：`and`、`or`、`not`
- 身份運算子：`is (為相同物件)`、`is not (不為相同物件)`
- 成員運算子：`in (是複合物件的成員)`、`not in (不是複合物件的成員)`

## 6. 簡單型別 (Simple Types)

### 整數 (Integer)

- 所有不含小數點的數字都是整數
- 整數的除法結果預設會被轉換成浮點數
- 要做到類似 C 的整數除法，可以使用 `//` 運算子

### 浮點數 (Float)

- 浮點數可以用十進制表示或是用指數表示，例如 `0.000123`、`1.23e-4`
- 在浮點數的計算中，要注意到浮點數的精確度問題，例如盡量不要直接比較兩個浮點數是否相等，而是使用 `math.isclose()` 函式

```python
import math

a = 0.1 + 0.2
print(a == 0.3)  # False
print(math.isclose(a, 0.3))  # True
```

### 複數 (Complex)

- 複數由實部和虛部組成，例如 `3 + 4j`，其中 `3` 是實部，`4` 是虛部
- 虛數的單位是 `j`，例如 `4j` 表示 `0 + 4j`
- 可以使用 `complex()` 函式來建立複數，例如 `complex(3, 4)` 表示 `3 + 4j`
- 常見的複數屬性和方法：

```python
c = 3 + 4j
print(c.real)  # 3.0
print(c.imag)  # 4.0
print(c.conjugate())  # (3-4j)
print(abs(c))  # 5.0
```

### 字串 (String)

- 字串是序列型別，可以用單引號 `'...'` 或雙引號 `"..."` 表示
- 字串的索引從 0 開始，例如 `s[0]` 表示第一個字元
- 字串的切片從 0 開始，例如 `s[0:5]` 表示第一個到第五個字元
- 常見的字串屬性和方法：

```python
s = "Hello, World!"
print(len(s))  # 13
print(s.upper())  # "HELLO, WORLD!"
print(s.lower())  # "hello, world!"
print(s + " I love Python")  # "Hello, World! I love Python"
print(s * 3)  # "Hello, World!Hello, World!Hello, World!"
print(s[0])  # "H"
print(s[0:5])  # "Hello"
print(s[0:5:2])  # "Hl"
print(s.replace("H", "J"))  # "Jello, World!"
print(s.split(","))  # ['Hello', ' World!']
```

### None Type

- `None` 通常用於表示變數沒有值，或是函式沒有回傳值

### 布林值 (Boolean)

- 布林值只有兩種：`True` 和 `False`，首字母必須大寫
- 在做型別轉換時，數字型別中的 `bool(0)` 和 `bool(0.0)` 都是 `False`，其他數字都是 `True`
- 在做型別轉換時，None 型別的 `bool(None)` 是 `False`
- 在做型別轉換時，字串型別的 `bool('')` 是 `False`，其他字串都是 `True`
- 在做型別轉換時，序列型別的 `bool([])` 是 `False`，其他序列都是 `True`

## 7. 複合型別 (Compound Types)

### 列表 (List)

- 有序且可變的型別
- 使用 `[]` 表示，元素之間用逗號隔開
- 常見的列表屬性和方法：

```python
lst = [5, 2, 1, 4, 3]
print(len(lst))  # 5
print(lst[0])  # 5
print(lst[-1])  # 3
print(lst[0:3])  # [5, 2, 1]
print(lst[::2])  # [5, 1, 3]
print(lst.append(6))  # [5, 2, 1, 4, 3, 6]
print(lst.sort())  # [1, 2, 3, 4, 5, 6]
print(lst + [7, 8, 9])  # [1, 2, 3, 4, 5, 6, 7, 8, 9]
print(lst[::-1])  # [9, 8, 7, 6, 5, 4, 3, 2, 1]
```

- 做為複合型別，列表可以包含不同型別的元素，例如 `[1, 'a', True, None, [1, 2, 3]]`

### 元組 (Tuple)

- 有序且不可變的型別，即建立後其元素不能被修改
- 元組類似於列表，但元組的元素不能被修改
- 使用 `()` 表示，元素之間用逗號隔開
- 元組也可以不用括號表示，例如 `1, 2, 3` 表示 `(1, 2, 3)`
- 元組經常被用在函式要返回多個回傳值時，例如 `numerator, denominator = x.as_integer_ratio()`
- 常見的元組屬性和方法：

```python
tup = (5, 2, 1, 4, 3)
print(len(tup))  # 5
print(tup[0])  # 5
print(tup[0:3])  # (5, 2, 1)
print(tup[::2])  # (5, 1, 3)
```

### 集合 (Set)

- 無序且可變的型別，重點在於元素的唯一性
- 使用 `{}` 表示，元素之間用逗號隔開
- 常見的集合屬性和方法：

```python
primes = {2, 3, 5, 7, 11}
odds = {1, 3, 5, 7, 9}
print(primes | odds)  # {1, 2, 3, 5, 7, 9, 11}，即聯集
print(primes.union(odds))  # {1, 2, 3, 5, 7, 9, 11}，與上式相同
print(primes & odds)  # {1, 3, 5, 7}，即交集
print(primes.intersection(odds))  # {1, 3, 5, 7}，與上式相同
print(primes - odds)  # {2, 11}，即差分
print(primes.difference(odds))  # {2, 11}，與上式相同
print(primes ^ odds)  # {2, 9, 11}，即對稱差分(只出現在兩者之一)
print(primes.symmetric_difference(odds))  # {2, 9, 11}，與上式相同
print(primes.add(13))  # {2, 3, 5, 7, 11, 13}
print(primes.remove(13))  # {2, 3, 5, 7, 11}
```

### 字典 (Dictionary)

- 有序(python 3.6+)且可變的型別
- 使用 `{}` 表示，元素之間用逗號隔開
- 字典的元素是鍵值對 (key-value pair)，例如 `{'a': 1, 'b': 2, 'c': 3}`
- 透過 `key` 來訪問 `value`，其中 `key` 必須是不可變的型別，例如 `int`、`str`、`tuple`，而 `value` 可以是任何型別
- 常見的字典屬性和方法：

```python
d = {'a': 1, 'b': 2, 'c': 3}
print(len(d))  # 3
print(d['a'])  # 1
print(d.keys())  # ['a', 'b', 'c']
print(d.values())  # [1, 2, 3]
print(d.items())  # [('a', 1), ('b', 2), ('c', 3)]
print(d['d'] = 4)  # {'a': 1, 'b': 2, 'c': 3, 'd': 4}
```

### 其他

- 可以在 `collections` 模組中找到更多複合型別，例如 `namedtuple`、`defulteDict`、`OrderedDict` 等

> 整理
>
> | type | mutable/immutable | ordered/unordered | copy by value/reference |
> | ---- | ---- | ------------ | ---- |
> | int | immutable |  | value |
> | float | immutable |  | value |
> | complex | immutable |  | value |
> | str | immutable |  | value |
> | bool | immutable |  | value |
> | list | mutable | ordered | reference |
> | tuple | immutable | ordered | value |
> | set | mutable | unordered | reference |
> | dict | mutable | ordered (python 3.6+) | reference |

## 8. 控制結構

### 條件語句

- 使用 `if`、`elif`、`else` 來表示條件語句
- 使用 `and`、`or`、`not` 來表示布林運算
- 使用 `is`、`is not` 來表示身份運算
- 使用 `in`、`not in` 來表示成員運算
- 記得加上 `:` 表示語句的結束

```python
if x > 0:
    print("x is positive")
elif x == 0:
    print("x is zero")
else:
    print("x is negative")
```

### for 迴圈

- 使用 `for` 來表示迴圈
- 可搭配 `in <迭代器>` 一起使用，例如 `for i in range(5)` 表示從 0 到 4 的數字
- 記得加上 `:` 表示語句的結束

```python
for i in range(5):
    print(i)
```

### while 迴圈

- 使用 `while` 來表示迴圈
- 記得加上 `:` 表示語句的結束

```python
i = 0
while i < 5:
    print(i)
    i += 1
```

### 其他

- 可以使用 `break` 來表示跳出迴圈
- 可以使用 `continue` 來表示跳過本次迴圈進入下一次迭代

## 9. 函式

有兩種建立函式的方法： 使用 `def` 關鍵字，或是使用 `lambda` 關鍵字。

### 調用函式

- 透過 `函式名稱(參數)` 來調用函式
- 除了普通參數，還可以用關鍵字參數(keyword argument)的方式來調用函式
- 普通參數和關鍵字參數可以混用，但關鍵字參數必須放在普通參數的後面

```python
def add(a, b):
    return a + b

print(add(1, 2))  # 3
print(add(1, b=2))  # 3
print(add(b=2, a=1))  # 3
```

### 使用 `def` 關鍵字

- 使用 `def` 關鍵字來定義函式，記得加上 `:` 表示語句的結束
- 使用 `return` 來回傳值
- 函式可以有多個回傳值，例如 `return a, b` 會回傳一個 tuple
- 函式可以有多個參數，例如 `def add(a, b): return a + b`
- 函式可以有預設參數，例如 `def add(a, b=2): return a + b`

```python
def add(a, b=2):
    return a + b
```

- 如果一開始不確定函式會有多少參數，可以用可變參數 `*args` 和 `**kwargs` 來表示
- 可變參數 `*args` 會將所有普通參數打包成一個 tuple
- 可變參數 `**kwargs` 會將所有關鍵字參數打包成一個 dictionary
- `args (arguments)`、`kwargs (keyword arguments)` 僅是慣例，可以改成其他名稱，重點是 `*` 和 `**` 的用法

```python
def add(*args, **kwargs):
    print(args)
    print(kwargs)

add(1, 2, 3, 4, 5)  # (1, 2, 3, 4, 5)
add(a=1, b=2, c=3)  # {'a': 1, 'b': 2, 'c': 3}
add(1, 2, 3, 4, 5, a=1, b=2, c=3)  # (1, 2, 3, 4, 5) {'a': 1, 'b': 2, 'c': 3}
```
- 此外 `*args` 和 `**kwargs` 還可以在函式調用時用來傳遞參數

```python
def add(a, b):
    return a + b

args = (1, 2)
kwargs = {'a': 1, 'b': 2}

add(*args)  # 3
add(**kwargs)  # 3
```

### 使用 `lambda` 關鍵字

- 用於建立較短較簡單的函式
- 語法：`lambda <參數>: <運算式>`
- 只能有一行運算式，不能有 return 語句、不能有多個回傳值、不能有 try/except 語句、不能有 while/for 語句

```python
add = lambda a, b: a + b
print(add(1, 2))  # 3
```

約等於

```python
def add(a, b):
    return a + b
```

## 10. 例外處理 (Exception Handling)

無論你的程式碼寫得多麼完美，總會有意外的情況發生，這時候就需要用到例外處理。常見的例外狀況有：

- 語法錯誤 (Syntax Error)：程式碼不符合 Python 的語法規則
- 執行時錯誤 (Runtime Error)：程式碼在執行時發生錯誤
- 語意錯誤 (Semantic Error)：程式碼的邏輯有問題，導致程式無法正常執行

### 捕獲例外

- 使用 `try`、`except`、`else`、`finally` 來捕獲例外
- `try` 語句塊中的程式碼會被執行，如果發生例外，則會跳到 `except` 語句塊中執行
- `else` 語句塊中的程式碼會在 `try` 語句塊中的程式碼沒有發生例外時執行
- `finally` 語句塊中的程式碼會在 `try` 語句塊中的程式碼執行完後執行

```python
def divide(a, b):
    try:
        return a / b
    except ZeroDivisionError:
        return "Cannot divide by zero"
    else:
        return "Division successful"
    finally:
        return "Division done"
```

> 常見的一些內建例外狀況：
>
> - `ZeroDivisionError`：除以零
> - `ValueError`：值錯誤
> - `TypeError`：型別錯誤
> - `NameError`：名稱錯誤
> - `IndexError`：索引錯誤
> - `KeyError`：鍵錯誤
> - `FileNotFoundError`：找不到檔案
> - `ImportError`：匯入錯誤

### 拋出例外

- 使用 `raise` 來拋出例外
- 拋出的例外可以被捕獲，例如：

```python
def example():
    raise ValueError

try:
    example()
except ValueError:
    print("Something went wrong")
```

### 訪問例外資訊

- 使用 `as` 來訪問例外資訊

```python
def example():
    raise ValueError("Value must be positive")

try:
    example()
except ValueError as e:
    print(f"Something went wrong: {e}")
```

### 自定義例外

- 除了使用內建的例外，還可以透過類別繼承來自定義例外
- 例如想要一個特殊的 `ValueError`，可以這樣寫：

```python
class MyException(ValueError):
    pass

try:
    raise MyException("Something went wrong")
except MyException as e:
    print(f"MyException: {e}")
```

## 11. 迭代器 (Iterator)

- 在資料分析中，一個很重要的應用是將資料以某種統一的方式重複地處理，例如對一個列表中的每個元素進行某種運算，這時候就需要用到迭代器
- 迭代器是 Python 中一種可以遍歷序列的物件
- 例如前面提到的 `for i in range(5)` 中的 `range` 函式，它產生的不是一個列表，而是一個迭代器，可以透過 `for` 迴圈來遍歷
- 可以透過 `iter()` 函式來將一個序列轉換成一個迭代器，例如 `iter([1, 2, 3, 4, 5])`

### 實用的迭代器

- `enumerate()`：將一個 list 轉換成一個迭代器，並返回一個包含「索引」和「索引對應元素」的 tuple

```python
list = [100, 200, 300, 400, 500]

for i, v in enumerate(list):
    print(i, v)

# 0 100
# 1 200
# 2 300
# 3 400
# 4 500
```

不用 `enumerate()` 的話，則要用比較繞的方式來達到相同的效果：

```python
list = [100, 200, 300, 400, 500]

for i in range(len(list)):
    print(i, list[i])
```

- `zip()`：將多個 list 轉換成一個迭代器，並返回一個包含多個 tuple 的迭代器，注意 zip 會以最短的 list 為主

```python
list1 = [2, 4, 6, 8]
list2 = [3, 6, 9, 12, 15]

for a, b in zip(list1, list2):
    print(a, b)

# 2 3
# 4 6
# 6 9
# 8 12
```

> `zip()` 也可以用來 unzip，例如：

```python
L1 = [1, 2, 3]
L2 = ['a', 'b', 'c']

zipped = zip(L1, L2)
print(zipped)  # [(1, 'a'), (2, 'b'), (3, 'c')]

L3, L4 = zip(*zipped)
print(L3)  # (1, 2, 3)
print(L4)  # ('a', 'b', 'c')
```

- `map()`：將一個函式應用到一個 list 中的每個元素

```python
def square(x):
    return x ** 2

list = [1, 2, 3, 4, 5]

for i in map(square, list):
    print(i)

# 1
# 4
# 9
# 16
# 25
```

- `filter()`：將一個函式應用到一個 list 中的每個元素，只包含那些函式回傳 True 的元素

```python
def is_even(x):
    return x % 2 == 0

list = [1, 2, 3, 4, 5]

for i in filter(is_even, list):
    print(i)

# 2
# 4
```

## 12. 列表推導 (List Comprehension)

- 列表推導是一種簡短又高效的建立列表的方式，它允許你在一個表達式中遍歷一個序列，並將每個元素進行某種運算後生成一個新的列表
- 語法：`[<運算式> for <元素> in <序列> if <條件>]`

```python
list = [1, 2, 3, 4, 5]
print([i * 2 for i in list])  # [2, 4, 6, 8, 10]
print([i for i in range(10) if i % 3 > 0])  # [1, 2, 4, 5, 7, 8, 10]
```

- 列表推導可以嵌套，例如：

```python
print([(i, j) for i in range(2) for j in range(3)])  # [(0, 0), (0, 1), (0, 2), (1, 0), (1, 1), (1, 2)]
```

- 列表推導可以模擬類似 C 語言中的三元運算子，例如：

```python
value = 10
print(value if value >= 0 else -value)  # 取絕對值
```

- 當然也有集合推導和字典推導，語法和列表推導類似，只是把 `[]` 換掉

```python
print({i for i in range(5)})  # {0, 1, 2, 3, 4}
print({i: i * 2 for i in range(5)})  # {0: 0, 1: 2, 2: 4, 3: 6, 4: 8}
```

## 13. 生成器 (Generator)

- 生成器是一種特殊的迭代器，它允許你遍歷一個序列，但不需要一次性將所有元素都存儲在記憶體中
- 生成器分成兩種：生成器表達式和生成器函式
- 列表是值的集合；而生成器是產生值的方法
- 當你建立一個列表的時候，你實際上在產生一個數值的集合，並且需要花費一定的記憶體開銷；但當你建立一個產生器的時候，你並沒有建立一個數值的集合，而是建立了一個產生這些數值的方法，這樣可以節省記憶體開銷，也能提高計算效率

### 生成器表達式 (Generator Expression)

- 相較於列表推導使用 `[]`，生成器表達式使用 `()`

```python
gen = (i for i in range(5))
print(gen)  # <generator object <genexpr> at 0x10a000000>

for i in gen:
    print(i)
```

- `itertools` 模組中有很多有用的生成器表達式，例如 `itertools.count()` 可以生成一個無限的數字序列

```python
import itertools

for i in itertools.count(start=1, step=2):
    print(i)
```

- 相較於列表可以被迭代多次，生成器只能被迭代一次，這個特性使得迭代可以被暫停並繼續

```python
G = (n ** 2 for n in range(10))

for n in G:
    print(n, end=" ")  # 0 1 4 9
    if n > 5:
        break

print("\ndo something else")

for n in G:
    print(n, end=" ")  # 16 25 36 49 64 81
```

### 生成器函式 (Generator Function)

- 生成器函式會在函式中使用 `yield` 關鍵字來生成值，用於生成更複雜的生成器

```python
def gen():
    for n in range(12):
        yield n ** 2

G1 = (n ** 2 for n in range(12))
G2 = gen()

print(list(G1))  # [0, 1, 4, 9, 16, 25, 36, 49, 64, 81, 100, 121]
print(list(G2))  # [0, 1, 4, 9, 16, 25, 36, 49, 64, 81, 100, 121]
```

下面是一個生成器函式的例子，用於生成一連串的質數：

```python
def gen_primes(N):
    primes = set()
    for n in range(2, N):
        if all(n % p > 0 for p in primes): # 檢查是否能被其他質數整除
            primes.add(n)
            yield n

# The asterisk (*) unpacks the generator, 
# passing each prime number as a separate argument to print()
print(*gen_primes(50))
```

## 14. 模組和套件 (Module and Package)

- 模組是一個包含 Python 程式碼的檔案，例如 `math.py`
- 套件是一個包含多個模組的目錄，例如 `package/`

### 匯入模組

- 使用 `import` 關鍵字來匯入模組
- 使用 `import ... as ...` 關鍵字來匯入模組並取叫好記的別名
- 使用 `from ... import ...` 關鍵字來匯入模組中的特定函式
- 使用 `from ... import *` 關鍵字來匯入模組中的所有函式(不推薦，因為可能會覆蓋掉自己定義的函式)

### 匯入第三方套件

- Python 具備豐富的第三方套件，套件的來源通常是 [Python Package Index (PyPI)](https://pypi.org/)
- 可以透過 `pip (pip installs packages)` 工具來安裝第三方套件，例如 `pip install numpy`

### 自定義模組

- 可以將自己的程式碼寫成模組，然後在其他地方匯入使用，提高程式碼的組織性和可重用性

```python
# 在 my_module.py 中定義一個函式
def my_function():
    print("Hello, World!")
```

```python
# 在其他地方匯入並使用
import my_module

my_module.my_function()  # 輸出: Hello, World!
```

### 自定義套件

- 可以將自己的程式碼寫成套件，然後在其他地方匯入使用，提高程式碼的組織性和可重用性
- 需要建立一個 `__init__.py` (可以是空的) 檔案來初始化套件

```python
# 在 my_package/my_module.py 中定義一個函式
def my_function():
    print("Hello, World!")
```

```python
# 在 my_package 目錄下建立 __init__.py 檔案
from my_package.my_module import my_function

my_function()  # 輸出: Hello, World!
```

## 15. 字串處理和正則表示式

- 除了用單引號和雙引號來表示字串，還可以用三引號來表示多行字串

```python
str1 = '''This is a multi-line string.
This is a multi-line string.
This is a multi-line string.
'''
print(str1)
```

- 常見的字串處理方法：

```python
temp = "   Hello, World ! ! !   "
print(temp.upper())  # 轉換成大寫 --> "   HELLO, WORLD ! ! !   "
print(temp.lower())  # 轉換成小寫 --> "   hello, world ! ! !   "
print(temp.strip())  # 去除字串前後的空白 --> "Hello, World ! ! !"
print(temp.lstrip())  # 去除字串左邊的空白 --> "Hello, World ! ! !   "
print(temp.rstrip())  # 去除字串右邊的空白 --> "   Hello, World ! ! !"
print(temp.replace("H", "J"))  # 替換字串 --> "Jello, World ! ! !"
print(temp.replace("!", ""))  # 去除字串中的某個字元 --> "   Hello, World    "
print(temp.split(","))  # 分割字串 --> ['Hello', ' World ! ! !']
print(temp.find("!"))  # 查詢字串位置，找不到會回傳 -1 --> 16
print(temp.index("!"))  # 查詢字串位置，找不到會回傳 ValueError 的例外 --> 16
print(temp.rfind("!"))  # 從結尾開始查詢字串位置，找不到會回傳 -1 --> 20
print(temp.rindex("!"))  # 從結尾開始查詢字串位置，找不到會回傳 ValueError 的例外 --> 20
print(temp.startswith("   He"))  # 檢查字串是否以某個字元開頭 --> True
print(temp.endswith("!"))  # 檢查字串是否以某個字元結尾 --> False
print("435".zfill(5))  # 在字串前補零 --> "00435"
```

- 拆分和合併字串的方法：

```python
line = "first;second;third;"

print(line.partition(";"))  # 拆成三個元素的 tuple --> ('first', ';', 'second;third;')
print(line.split(";"))  # 拆成 list --> ['first', 'second', 'third']
print(line.split(";", 1))  # 拆成 list，只拆一次 --> ['first', 'second;third;']

line2 = ["first", "second", "third"]
print("+".join(line2))  # 把 list2 的每個元素用 "+" 連接 --> 'first+second+third'
```

- 格式化字串的方法：

```python
name = "Alice"
age = 25

print(str(age))  # 25
print("My name is {0} and I am {1} years old.".format(name, age))
print("My name is {name} and I am {age} years old.".format(name=name, age=age))
print(f"My name is {name} and I am {age} years old.") # 此用法稱為 f-string
```

### 正則表示式 (Regular Expressions)

- 正則表示式是一種用於匹配字符串中字元組合的模式，可以用來檢索、分割和替換字符串
- 在 Python 中，可以使用 `re` 模組來處理正則表示式

```python
import re

line = "This is a test string."

# 實現與 `line.split(" ")` 相同的功能
regex = re.compile(r"\s+")
print(regex.split(line))  # 分割字串 --> ['This', 'is', 'a', 'test', 'string.']
print(line.split(" "))  # 分割字串 --> ['This', 'is', 'a', 'test', 'string.']

# 上面出現的 `\s` 是一個特殊字元，
# 表示任何空白字元 (包括空格、tab 符和換行符)，
# `+` 表示前面的字元出現一次或多次，
# 因此 `\s+` 匹配了任何包含一個或多個空格的字串
```

- 常見的幾個正則表示式特殊字元：

| 特殊字元 | 描述 |
| -------- | -------- |
| `\d` | 任何數字 (0-9) |
| `\D` | 任何非數字 |
| `\s` | 任何空白字元 (包括空格、tab 符和換行符) |
| `\S` | 任何非空白字元 |
| `\w` | 任何字母和數字字元 |
| `\W` | 任何非字母和數字字元 |
| `.` | 任何字元 (除了換行符) |

- 常見的幾個正則表示式語法：

| 語法 | 描述 |
| -------- | -------- |
| `?` | 前面的字元出現零次或一次 |
| `*` | 前面的字元出現零次或多次 |
| `+` | 前面的字元出現一次或多次 |
| `{n}` | 前面的字元出現 n 次 |
| `{n, m}` | 前面的字元出現 n 到 m 次 |

## 16. 資料科學工具概覽

以下介紹幾個資料科學中常用的 Python 套件：

### NumPy

- NumPy 提供了高效的多維陣列和相關的數學運算功能
- 安裝：`pip install numpy`
- 使用： `import numpy as np`

### Pandas

- Pandas 以 data frame 物件為基礎，提供了一個標籤化的介面訪問多維陣列
- Pandas 實際上是基於 NumPy 建立的
- 安裝：`pip install pandas`
- 使用： `import pandas as pd`

### Matplotlib

- Matplotlib 是一個受歡迎的可視化套件，可以繪製各種圖表
- 安裝：`pip install matplotlib`
- 使用： `import matplotlib.pyplot as plt`

### SciPy

- SciPy 是一個基於 NumPy 的科學計算庫，提供了各種科學計算功能
- 可以進行例如傅立葉變換、積分、插值、微分、線性代數、統計、信號處理等操作
- 安裝：`pip install scipy`
- 使用： `import scipy`

## 17. 更多學習資源

### Python 語法

- Fluent Python by Luciano Ramalho
- Dive into Python by Mark Pilgrim
- Learn Python the Hard Way by Zed Shaw
- Python Essential Reference by David Beazley

### 資料科學和科學計算領域

- The Python Data Science Handbook by Jake VanderPlas
- Effective Computation in Physics by Anthony Scopatz and Kathryn Huff
- Python for Data Analysis by Wes McKinney (Pandas 創始人)
