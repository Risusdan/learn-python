# 型別提示 (Type Hints)

## 參考資料

- [typing --- 支援型別提示](https://docs.python.org/zh-tw/3/library/typing.html)
- [使用 Python typing 模組對你的同事好一點](https://myapollo.com.tw/blog/python-typing-module/)
- [Type hints cheat sheet](https://mypy.readthedocs.io/en/stable/cheat_sheet_py3.html)

## 前言

- Python 的型別提示(type hint)是一種在程式碼中透過型別註釋(type annotation)標註變數、函式參數和返回值的資料型別的方式
- 這是 Python 3.5+ 引入的功能，可以提升程式碼的可讀性和可維護性

> Type Hints 是一個概念，指的是在程式碼中提供型別資訊的做法；Type Annotations 是這個概念的具體實現，指的是在程式碼中實際寫下的型別標註。

> 型別註釋只是註解般的存在，沒有任何強迫必須使用特定型別的效果，但即使如此，型別註釋也為 Python 帶來更好的可維護性

## 為什麼要使用型別提示？

1. **提升程式碼可讀性**：
   - 清楚地表明變數或函式預期的資料型別
   - 讓其他開發者更容易理解程式碼

2. **更好的開發體驗**：
   - IDE 可以提供更準確的程式碼補全
   - 可以及早發現型別相關的錯誤

3. **文件化的效果**：
   - 型別提示本身就是一種文件
   - 減少撰寫額外文件的需求

## 型別提示的基本用法

以下是沒有使用型別提示的範例：

```python
def add(a, b):
    return a + b
```

以下是使用型別提示的範例：

```python
def add(a: int, b: int) -> int:
    return a + b
```

## `typing` 模組

Python 內建的型別（例如： int, float, dict, list, …）可以直接使用型別註釋，但如果是較複雜的資料型別就需要 typing 模組的輔助。

例如當我們想定義一個包含多個整數的列表作為函式參數時，在 Python 3.9(不含 3.9) 之前這樣寫會有語法錯誤：

```python
def add(numbers: list[int]) -> int:
    return sum(numbers)
```

應該改寫成這樣：

```python
from typing import List

def add(numbers: List[int]) -> int:
    return sum(numbers)
```

在 Python 3.9 之後，則可以直接這樣寫：

```python
def add(numbers: list[int]) -> int:
    return sum(numbers)
```

## 型別檢查器


