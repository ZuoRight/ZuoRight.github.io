# iterable

## 不可变对象

> 字符串、元组、不可变集合

## 可变对象

> 列表、集合、字典

### 复制

```python
"""
对于字符串都是引用
对于元组，只有深拷贝才不是引用，否则都是引用

x = [1, 2, [31, 32]]
x  = {1,2,3}
x = {"a":1,"b":2,"c":3}
"""
```

#### 引用

```python
# id(y) == id(x)
# x赋值给y，y只是x的一个引用，会跟着x的改变而改变
y = x
```

#### 浅拷贝

- 工厂函数`.copy()`

```python
# id(y) != id(x)
# 只能拷贝父级元素，即改变x的父级元素，y的父级元素不会变
# 子级元素仍为引用，即改变x的子级元素，y的子级元素也会变
y = x.copy()
```

- `copy.copy()`函数

```python
import copy
y = copy.copy(x)
```

- 列表的切片操作也是浅拷贝：`_list[:]`

#### 深拷贝

```python
# id(y) != id(x)
# 父级与子级元素都会被拷贝，即改变x任意元素，都不会影响y的元素改变
import copy
y = copy.deepcopy(x)
```

### 增

```python
# ===列表===
l.append("x")  # 末位增一个
l.extend(seq)  # 末位增一组序列
l.insert(index,"x")  # 插入到指定位置


# ===集合===
.add(key)


# ===字典===
dic["new_key"] = new_value
```

### 删

```python
# ===列表===
l.pop()  # 删除末位
l.pop(index)  # 删除指定位置的元素

l.remove("x")  # 删除指定元素（如有重复，删除第一个）

del l[m:n]  # 删除切片


# ===集合===
.remove(key)  # 删除指定元素
.pop()  # 无法指定参数，即不能删除指定元素

# ===字典===
del dic[key]  # 删除指定键
dic.del[key]
del dic  # 删除字典
dic.clear()  # 清空字典

.pop(key)  # 删除并返回指定key的值
popitem()  # 删除并返回字典的最后一个键值对，不接受参数
```

### 清空

```python
clear()  # 清空
```

### 改

- list

```python
l[index] = "x"  # 替换指定位置元素
```

### 查

```python
# ===字典===
_dict.[key]  # key不存在会报错

_dict.get(key)  # key不存在则返回None

_dict.setdefault(key) # key不存在则自动添加{key:default}，返回None
_dict.setdefault(key, value) # key不存在则自动添加{key:value}，返回value

# 以下都不接受参数
_dict.items()  # dict_items([('k1', 'v1'), ('k2', 'v2'), ('k3', 'v3')])
_dict.keys()  # dict_keys(['k1', 'k2', 'k3'])
_dict.values()  # dict_values(['v1', 'v2', 'v3'])
```

### 切片

### 索引

元组与列表均支持索引（还可以负数索引），支持切片，支持任意嵌套。索引时性能几乎没有差别。

集合和字典不支持索引

```python
# 返回列表/元组中item第一次出现的索引
l.index("b")
```

1. d["k1"]
2. d,get("k1", "null")  #如果不存在返回默认值“null”


### 统计

```python
# ===字符串===
len('中文')  # 2


# ===bytes===
len(b'\xe4\xb8\xad\xe6\x96\x87')  # 6


# ===列表===
l = ["a", "b", "c", "c"]

# 统计列表/元组中某元素出现的次数
l.count("c")  # 2

# 返回元素最大值
max(list)
# 返回元素最小值
min(list)


# ===字典===
len(dic)
```

### 排序

列表和元组，都是有序的

集合和字典无序?

1. tuple/list/set：都可以直接用sorted(tuple/list/set) 排序即可，但元素类型要一致才可以
2. dict排序（排序后会以列表的形式返回）：
   1. 按key排：sorted(d.items(), key=lambda x: x[0])
   2. 按value排：sorted(d.items(), key=lambda x: x[1])

- str

```python
new_t = sorted(t)
```

- tuple

```python
new_t = sorted(t)
```

- list

```python
l = [2,1,3]

l_new = sorted(l)  # [1,2,3]
l_new = sorted(l, reverse=True)  # [3,2,1]

# 原列表被改变
l.sort()
l.sort(reverse=True)
```

### 反转

```python
# 反转列表，原列表变了
l.reverse()
# 反转后得到一个迭代器，需要再转化一下，原元组/元组没变
new_l = list(reversed(t))
new_t = tuple(reversed(t))

# 还可以用切片的方式反转
a[::-1]
```

zip()