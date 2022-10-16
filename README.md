# Python Portfolio

###### tags: `Python`

Python 學習歷程

推薦學習網站：[Python 慣用語](http://seanlin.logdown.com/)

[TOC]

## 命名規則與命名風格
遵守規範：[PEP8 – Style Guide for Python Code](https://peps.python.org/pep-0008/)
| 對象     | 風格範例                        | 說明                              |
| -------- | ------------------------------- | --------------------------------- |
| 虛擬環境 | venv-name                       | 自訂 , PEP8無相關建議             |
| 專案     | project-name                    | 自訂 , PEP8無相關建議             |
| 套件     | package_name                    | 短名稱，全小寫，必要時使用底線(_) |
| 模組     | module_name.py                  | 短名稱，全小寫，必要時使用底線(_) |
| 類別     | class ClassName(object):        | 每個英文單字的第一個字大寫        |
| 例外類別 | class ExceptionName(Exception): | 每個英文單字的第一個字大寫        |
| 函式     | def function_name():            | 全小寫，可使用底線                |
| 方法     | def method_name(self):          | 全小寫，可使用底線                |
| 常數     | GLOBAL_CONSTANT_NAME = 1        | 全大寫，單字間加底線              |
| 變數     | var_name = 1                    | 全小寫，可使用底線                |
| 參數     | param_name = 1                  | 全小寫，可使用底線                |

參考資料：[Python 慣用語 - 24 遵循 PEP 8 的命名規則](http://seanlin.logdown.com/posts/238789-python-idioms-24-pep-8-naming-convension)

## 命名空間與可視範圍
```
- 套件層級 , 定義在 __init__.py
- 模組層級 , 定義在 module_file.py
- 類別層級 , 定義在 class_suite
- 實例層級 , 定義在 __init__(self) , 使用 self. 定義
```

---

Name (also called identifier) is simply a name given to objects. Everything in Python is an object. Name is a way to access the underlying object.

To simply put it, namespace is a collection of names.

Different namespaces can co-exist at a given time but are completely isolated.

- Built-in Namespace
- Module: Global Namespace
- Function: Local Namespace

Although there are various unique namespaces defined, we may not be able to access all of them from every part of the program. The concept of scope comes into play. Scope is the portion of the program from where a namespace can be accessed directly without any prefix. At any given moment, there are at least three nested scopes.

Scope of the current function which has local names
Scope of the module which has global names

Outermost scope which has built-in names
We have seen that multiple namespaces can exist independently from each other and that they can contain the same variable names on different hierachy levels. The “scope” defines on which hierarchy level Python searches for a particular “variable name” for its associated object. Now, the next question is: “In which order does Python search the different levels of namespaces before it finds the name-to-object’ mapping?”

To answer is: It uses the LEGB-rule, which stands for Local -> Enclosed -> Global -> Built-in, where the arrows should denote the direction of the namespace-hierarchy search order.

- Local can be inside a function or class method, for example.
- Enclosed can be its enclosing function, e.g., if a function is wrapped inside another function.
- Global refers to the uppermost level of the executing script itself, and
- Built-in are special names that Python reserves for itself.

參考資料：[Python Namespace and Scope](https://www.programiz.com/python-programming/namespace)

## Python BIFs

BIF 是 Built-in Function 的縮寫，Python 提供許多好用內建函數可以使用，避免重複造輪

> 舉例：

```python=
prices = [100, 300, 50, 600]
total = sum(prices)
```

> 非慣用：
```python=
prices = [100, 300, 50, 600]
total = 0
for price in prices:
    total += price
```

參考資料：[Python Built-in Functions](https://docs.python.org/3/library/functions.html)

---

**避免覆蓋 BIFs!**

寫程式慣用的變數名稱可能會跟內建函式衝突，儘管這是合法的，但有可能是 bug 的來源，要儘量避免

> 錯誤舉例 (Error Example)：
```python=
def list():
    return [1, 2, 3]


s = list('test')
```

```
常用的命名方式是在變數後頭加上 _，也可以用同樣的命名方式避免使用到保留字，例如 class_
```

以下是常常不小心會沖到的變數名稱，除了加上底線外，也可考慮使用同義字或是縮寫，不過必須確保是大家都懂的用法
```python=
id
object
type
len
```

## 變數特殊命名方法：底線開頭或結尾

|   情境   | 風格範例                        | 說明                              |
| -------- | ------------------------------- | --------------------------------- |
| 前單底線 | _var                       | 模組的私有成員，無法匯入以底線開頭的名稱。
| 前雙底線 | __var | 類別或物件的私有屬性，外部無法存取 |
| 前後雙底線 | ```__var__``` | 保留給 Python 內部使用，程式設計師盡量避免使用
| 後單底線 | var_  | 與關鍵字衝突時使用     |
| 底線     | _     | 不存取的免洗變數名稱，用完即棄      |