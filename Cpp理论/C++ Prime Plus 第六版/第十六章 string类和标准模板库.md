# **string类**

- 构造函数

  ![20220313120702](https://raw.githubusercontent.com/Be-A-God/Drawing-bed/main/note/20220313120702.png)
  ![20220313120732](https://raw.githubusercontent.com/Be-A-God/Drawing-bed/main/note/20220313120732.png)


- 读取输入时遇到空白字符停止并将其留在输入队列中

- 重载的 `find()` 成员方法

  ![20220313120810](https://raw.githubusercontent.com/Be-A-God/Drawing-bed/main/note/20220313120810.png)

- 其他

  - 方法 `capacity()` 返回当前分配给字符串的内存块的大小
  - 方法 `reserve()` 能够请求内存块的最小长度
  - 方法 `c_str()` 返回一个指向 C 风格字符串的指针
  - 字符类型：`char` `wchar_t` `char16_t` `char32_t` `char8_t`（最后一个C++20提出）

---

# **智能指针模板类**

- 概念：行为类似于指针的类对象，可以帮助管理动态内存分配

- 智能指针类别：`unique_ptr` `shared_ptr` `weak_ptr`

- `unique_ptr` 有别于 `auto_ptr` ：能够在编译阶段检测到对象所有权转移的情况

- 只有 `unique_ptr` 能够使用 `delete []`

- 多个指向同一对象的指针使用 `shared_ptr` ，其他使用 `unique_shared`

---

# **标准模板库STL**

- 模板类 `vector`

- 常用成员函数

  - `size()` 元素数目
  - `swap()` 交换容器内容
  - `begin()` 返回容器中第一个元素的迭代器
  - `end()` 返回一个超过容器尾的迭代器
  - `push_back` 向末尾添加元素
  - `erase()` 删除给定区间的元素
  - `insert()` 在指定位置插入区间

- 迭代器：类型为 `iterator` 或 `const_iterator`

- 支持基于范围的 `for` 循环

- 其他通用非成员函数（STL函数）

  - `for_each()` ：将被指向的函数应用于容器区间中的各个元素，被指向的函数不能修改容器元素的值
  - `random_shuffie()` ：随机排列给定区间的元素
  - `sort()` ：要求容器支持随机访问

---

# **泛型编程**

- `++` 运算符的重载

  - 前缀版本语法：`operator++()`
  - 后缀版本语法：`operator++(int)`

- 迭代器类型

  - 输入迭代器：单向迭代器，只能递增不能倒退，只读
  - 输出迭代器：单向只写
  - 正向迭代器：总是按相同顺序遍历，支持读写数据
  - 双向迭代器：具有正向迭代器的特性，同时支持递减运算符

- 迭代器

  - `rbegin()` ：返回超尾（类同 `end()` ），但类型为 `reverse_iterator`
  - `rend()` ：返回第一个元素的迭代器（类同 `begin()` ），但类型为 `reverse_iterator`

- 容器

  - 概念：存储其他对象的对象，必须是同一种类型，且该类型是可复制构造和可赋值的
  - 操作的复杂度：编译时间、固定时间、线性时间
  - 类型：`vector` `deque list` `forward_list` `queue` `priority_queue` `stack`
  - 关联容器：将值 `value` 和键 `key` 关联一起，提供对元素的快速访问，基于树结构
  - 无序关联容器：基于数据结构哈希表

---

# **函数对象（函数符）**

- 概念：可以与函数方式 () 结合使用的任意对象

- 函数符类别

  - 生成器（无参数）
  - 一元函数（一个参数可以调用）
  - 二元函数（两个参数可以调用）

- 其他（缺少资料）