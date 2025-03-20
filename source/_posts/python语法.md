---
title: python基础语法
date: 2025-03-20 17:03:39
tags: python学习
toc: true
---

## List

### 1. List 的创建

- **直接定义**  
  使用中括号 `[]` 创建一个列表：

```python
my_list = [1, 2, 3, 'a', 'b']
```

- 使用 `list()` 构造函数

  通过传入可迭代对象创建列表：

  ```python
  my_list = list((1, 2, 3))  # 注意：参数需要是可迭代对象
  ```

------

### 2. 列表的常见操作和方法

#### 2.1 添加元素

- **`append()`**
  在列表末尾添加单个元素。

  ```python
  lst = [1, 2, 3]
  lst.append(4)  # 结果: [1, 2, 3, 4]
  ```

- **`extend()`**
  将一个可迭代对象中的多个元素添加到列表末尾。

  ```python
  lst.extend([5, 6])  # 结果: [1, 2, 3, 4, 5, 6]
  ```

- **`insert()`**
  在指定位置插入元素，其他元素自动右移。

  ```python
  lst.insert(0, 0)  # 结果: [0, 1, 2, 3, 4, 5, 6]
  ```

#### 2.2 删除元素

- **`remove()`**
  删除列表中第一次出现的指定值。

  ```python
  lst = [0, 1, 2, 3, 4, 5, 6]
  lst.remove(3)  # 结果: [0, 1, 2, 4, 5, 6]
  ```

- **`pop()`**
  删除并返回指定索引处的元素（默认删除最后一个）。

  ```python
  last = lst.pop()  # 删除最后一个元素，last=6，lst变为[0, 1, 2, 4, 5]
  ```

- **`clear()`**
  清空整个列表。

  ```python
  lst.clear()  # 结果: []
  ```

#### 2.3 查找与统计

- **`index()`**
  返回指定值第一次出现的索引位置。

  ```python
  lst = [1, 2, 2, 3, 4, 2]
  idx = lst.index(2)  # 返回索引1（第一个2的位置）
  ```

- **`count()`**
  统计某个元素在列表中出现的次数。

  ```python
  cnt = lst.count(2)  # 结果: 3
  ```

#### 2.4 排序与反转

- **`sort()`**
  就地对列表进行排序（默认升序），也可以通过参数设置排序方式。

  ```python
  lst = [3, 1, 4, 2]
  lst.sort()  # 结果: [1, 2, 3, 4]
  
  # 使用 key 参数：按字符串长度排序
  words = ["banana", "apple", "cherry", "blueberry"]
  words.sort(key=lambda x: len(x))
  print(words)  # 输出: ['apple', 'banana', 'cherry', 'blueberry']
  
  ```

- **`sorted()`**
  返回一个新的排序后的列表，不改变原列表。

  ```python
  new_lst = sorted(lst)  # new_lst为升序排序的新列表
  ```

- **`reverse()`**
  就地将列表中的元素反转。

  ```python
  lst.reverse()  # 结果: [4, 3, 2, 1]
  ```

#### 2.5 列表推导式

列表推导式提供了一种简洁的方法来创建新列表。

```python
squares = [x**2 for x in range(10)]  # 生成0到9的平方列表
```

------

### 3. 其他

- **`copy()`**
  创建列表的浅拷贝。

  ```python
  lst = [1, 2, 3]
  lst_copy = lst.copy()  # lst_copy为lst的浅拷贝
  ```

- **`len()`**
  返回列表的长度（元素个数）。

  ```python
  length = len(lst)  # 结果: 3
  ```



## Dictionary

### 1. Dictionary 的创建

#### 1.1 直接定义
- **直接定义**  
  使用花括号 `{}` 定义一个字典，键值对之间用冒号 `:` 分隔，多个键值对之间用逗号 `,` 分隔：

```
my_dict = {'name': 'Alice', 'age': 30, 'city': 'New York'}
```

#### 1.2 使用 `dict()` 构造函数

- 使用 `dict()` 创建字典

  通过关键字参数或者可迭代对象创建字典：

  ```
  my_dict = dict(name='Bob', age=25, city='Los Angeles')
  ```

  或者：

  ```
  my_dict = dict([('name', 'Charlie'), ('age', 28), ('city', 'Chicago')])
  ```

------

### 2. 字典的常见操作和方法

#### 2.1 添加或修改元素

- **直接赋值添加或修改**
  若键不存在则添加，若键已存在则更新对应的值：

  ```
  my_dict = {'name': 'Alice', 'age': 30}
  my_dict['city'] = 'New York'  # 添加新键值对
  my_dict['age'] = 31         # 更新已有键的值
  ```

- **`update()` 方法**
  使用另一个字典或键值对迭代对象更新字典：

  ```
  my_dict.update({'age': 32, 'country': 'USA'})
  ```

#### 2.2 删除元素

- **`del` 语句**
  根据键删除字典中的元素：

  ```
  del my_dict['city']  # 删除键为'city'的键值对
  ```

- **`pop()` 方法**
  删除指定键，并返回该键对应的值。如果键不存在，则可以指定默认值避免异常：

  ```
  age = my_dict.pop('age', None)  # 删除键'age'并返回其值
  ```

- **`popitem()` 方法**
  删除并返回字典中的最后一个键值对（Python 3.7+ 保证插入顺序）：

  ```
  item = my_dict.popitem()
  ```

- **`clear()` 方法**
  清空整个字典：

  ```
  my_dict.clear()  # 结果: {}
  ```

#### 2.3 访问元素

- **通过键访问**
  使用中括号直接访问键对应的值（若键不存在会引发 `KeyError`）：

  ```
  value = my_dict['name']
  ```

- **`get()` 方法**
  通过 `get()` 方法访问，键不存在时返回默认值（默认为 `None`）：

  ```
  value = my_dict.get('name', 'Unknown')
  ```

#### 2.4 获取键、值和键值对

- **`keys()` 方法**
  返回字典中所有键的视图：

  ```
  keys = my_dict.keys()
  ```

- **`values()` 方法**
  返回字典中所有值的视图：

  ```
  values = my_dict.values()
  ```

- **`items()` 方法**
  返回字典中所有键值对的视图：

  ```
  items = my_dict.items()
  ```

#### 2.5 遍历字典

- **遍历键**

  ```
  for key in my_dict:
      print(key, my_dict[key])
  ```

- **遍历键值对**

  ```
  for key, value in my_dict.items():
      print(key, value)
  ```

------

### 3. 其他

在`python3.7`及更高版本中`dictionary`是有序数据结构了，但**3.6及之前版本则为无序**。意味着在3.7及更高版本中每次循环迭代会得到一样的结果，但3.6及以前则不保证。

- **判断键是否存在**
  使用 `in` 判断键是否存在于字典中：

  ```
  if 'name' in my_dict:
      print("Key 'name' exists.")
  ```

- **字典复制**
  使用 `copy()` 方法进行浅拷贝：

  ```
  new_dict = my_dict.copy()
  ```

- **字典长度**
  使用 `len()` 函数获取字典中键值对的数量：

  ```
  length = len(my_dict)
  ```

------

## Set

### 1. set 的创建

#### 1.1 直接定义
- **直接定义**  
  使用花括号 `{}` 定义一个集合，集合中的元素是无序且唯一的：

```python
my_set = {1, 2, 3, 4}
```

注意：空集合不能用 `{}` 定义，因为那样会被认为是字典，应使用 `set()`。

#### 1.2 使用 `set()` 构造函数

- 使用 `set()` 创建集合

  可以通过传入可迭代对象来创建集合：

  ```
  my_set = set([1, 2, 3, 4])
  ```

------

### 2. set 的常见操作和方法

#### 2.1 添加和更新元素

- **`add()` 方法**
  向集合中添加单个元素：

  ```
  my_set.add(5)  # 结果: {1, 2, 3, 4, 5}
  ```

- **`update()` 方法**
  向集合中添加多个元素（传入一个可迭代对象）：

  ```
  my_set.update([6, 7, 8])  # 结果: {1, 2, 3, 4, 5, 6, 7, 8}
  ```

#### 2.2 删除元素

- **`remove()` 方法**
  删除指定元素，如果元素不存在则会抛出错误：

  ```
  my_set.remove(3)  # 删除元素 3，结果: {1, 2, 4, 5, 6, 7, 8}
  ```

- **`discard()` 方法**
  删除指定元素，如果元素不存在则不会抛出错误：

  ```
  my_set.discard(10)  # 集合不变
  ```

- **`pop()` 方法**
  随机删除并返回集合中的一个元素，注意集合是无序的：

  ```
  elem = my_set.pop()  # 返回并删除一个随机元素
  ```

- **`clear()` 方法**
  清空整个集合：

  ```
  my_set.clear()  # 结果: set()
  ```

------

### 3. set 的常见运算

#### 3.1 集合之间的关系运算

- **交集**
  使用 `intersection()` 或 `&` 运算符：

  ```
  python
  
  
  Copy
  a = {1, 2, 3}
  b = {2, 3, 4}
  inter = a.intersection(b)  # 或 inter = a & b，结果: {2, 3}
  ```

- **并集**
  使用 `union()` 或 `|` 运算符：

  ```
  python
  
  
  Copy
  union_set = a.union(b)  # 或 union_set = a | b，结果: {1, 2, 3, 4}
  ```

- **差集**
  使用 `difference()` 或 `-` 运算符：

  ```
  python
  
  
  Copy
  diff = a.difference(b)  # 或 diff = a - b，结果: {1}
  ```

- **对称差集**
  使用 `symmetric_difference()` 或 `^` 运算符，返回两个集合中不重复的元素：

  ```
  python
  
  
  Copy
  sym_diff = a.symmetric_difference(b)  # 或 sym_diff = a ^ b，结果: {1, 4}
  ```

#### 3.2 判断子集和超集

- **判断子集**
  使用 `issubset()` 方法或 `<=` 运算符：

  ```
  python
  
  
  Copy
  is_subset = a.issubset(b)  # 或 a <= b
  ```

- **判断超集**
  使用 `issuperset()` 方法或 `>=` 运算符：

  ```
  is_superset = a.issuperset(b)  # 或 a >= b
  ```

------

### 

## Errors

### 1. try/except 结构
- **基本用法**  
  将可能产生异常的代码放入 `try` 块中，并在 `except` 块中捕获和处理异常：

```
  try:
      num = int("abc")
  except ValueError as e:
      print("转换失败：", e)
```

如果 `try` 块中的代码发生了异常，程序会立即跳转到相应的 `except` 块执行。

------

### 2. else 块

- 无异常时执行

  当try块中的代码没有发生异常时，else块中的代码会被执行：

  ```
  try:
      num = int("123")
  except ValueError:
      print("转换失败")
  else:
      print("转换成功，数字为", num)
  ```

  else 块通常用于那些只有在没有错误发生时才需要执行的操作。

------

### 3. finally 块

- 无论是否异常都会执行

  finally块中的代码无论是否发生异常都会执行，常用于资源清理等操作：

  ```
  try:
      file = open("example.txt", "r")
      data = file.read()
  except IOError as e:
      print("文件读取错误：", e)
  finally:
      file.close()  # 确保文件最终被关闭
  ```

------

### 4. raise 主动抛出异常

#### 1.Exception

在 Python 中，可以使用 `raise` 主动抛出异常。选择合适的异常类型有助于准确描述错误原因并便于后续调试和异常处理。以下列举了一些常见的异常类型以及它们的使用场景：
- **描述**：所有内置异常的基类，最通用的异常类型。  
- **用法**：

```
raise Exception("通用异常")
```

#### 2.ValueError

- **描述**：当一个操作或函数收到具有正确类型但不适当的值时抛出。

- 用法：

  ```
  raise ValueError("无效的值")
  ```

#### 3. TypeError

- **描述**：当对不支持的操作类型进行操作时抛出。

- 用法：

  ```
  raise TypeError("类型错误")
  ```

#### 4. KeyError

- **描述**：当试图访问字典中不存在的键时抛出。

- 用法：

  ```
  raise KeyError("键不存在")
  ```

#### 5. IndexError

- **描述**：当试图访问序列中不存在的索引时抛出。

- 用法：

  ```
  raise IndexError("索引超出范围")
  ```

#### 6. ZeroDivisionError

- **描述**：当除数为零时抛出。

- 用法：

  ```
  raise ZeroDivisionError("除数不能为零")
  ```

#### 7. FileNotFoundError

- **描述**：当试图打开不存在的文件时抛出，通常出现在文件操作中。

- 用法：

  ```
  raise FileNotFoundError("文件未找到")
  ```

#### 8. NotImplementedError

- **描述**：当派生类没有实现父类中的抽象方法时，父类可以抛出该异常以提示未实现的功能。

- 用法：

  ```
  raise NotImplementedError("该方法尚未实现")
  ```

------

### 
