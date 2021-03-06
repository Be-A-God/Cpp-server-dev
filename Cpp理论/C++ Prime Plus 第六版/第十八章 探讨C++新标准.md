# **C++11 回顾**

- 新类型

  - `long long`
  - `unsigned long long`
  - `char16_t`
  - `char32_t`

- 列表初始化

  - 窄缩：禁止将数值赋给无法存储它的数值变量
  - `std::initializer_list` ：用于构造函数的参数，使其支持列表初始化

- 声明

  - `auto` ：自动类型推断
  - `decltype` ：将变量的类型声明为表达式指定的类型
  - 尾置返回类型：`auto 函数名（参数） -> decltype(exp);`
  - 模板别名的新方法：使用 `using`
  - 空指针 `nullptr`

- 智能指针：自动释放管理内存

- `noexcept` 关键字：声明结尾处，表明函数不会抛出异常

- 作用域内枚举（强类型枚举）：使用 `class` 或 `struct` 限定其作用域

- 类的修改

  - 显式转换运算符 `explicit` 禁止单参数构造函数导致的自动转换（从数值到类类型）
  - 类内成员支持初始化（除静态成员变量）：使用等号或大括号，不能使用圆括号

- 模板和STL

  - 基于范围的 `for`  循环支持
  - 新的 STL 容器：`forward_list` `unordered_map` `unordered_set` `unordered_multimap` `unordered_multiset`
  - 新模板：`array`
  - 新的 STL 方法：`cbegin()` `cend()`
  - `valarray` 升级（暂无资料）
  - 弃用 `export`
  - 声明嵌套模板不再需要空格隔开两个尖括号

- 移动语义与右值引用

  - 移动构造函数：使用右值引用作为形参
  - 强制移动：使用 `static_cast<>` 或者 `std::move()` 将左值对象变为右值对象

---

# **新的类功能**

- 特殊成员函数

  - 默认构造函数
  - 复制构造函数
  - 复制赋值运算符
  - 折构函数
  - 移动构造函数
  - 移动赋值运算符

- 默认的方法和禁用的方法

  - `default` 显式声明方法的默认版本，指定编译器生成（声明结尾处加上 `= default` ）
  - `delete` 禁止使用特定的方法（声明结尾处加上 `= delete` ）

- 委托构造函数：在一个构造函数初始化列表中使用另一个构造函数（不可以同时使用初始化列表为成员变量赋初值）

- 继承构造函数：使用 `using` 声明继承基类的构造函数

- 管理虚方法

  - 虚方法特征标不同时隐藏旧版本而不是覆盖
  - 虚说明符 `override` 指明覆盖一个虚函数，要求编译器检查，放在声明尾部
  - 虚说明符 `final` 禁止派生类覆盖特定的虚方法；禁止该类被继承

---

# **Lambda函数**

- 本身是匿名函数

- 仅当 lambda 表达式完全由一条返回语句组成时，自动类型推断才管用（返回类型）

- lambda 可以访问作用域内的任何动态变量

- lambda 表达式使用值捕获，在定义的时候捕获的值已经确定下来

---

# **包装器**

- 模板 `function` ：用于包装调用特征标相同的函数指针、函数对象或 lambda 对象

---

# **可变参数模板**

- 元运算符 `...` 与任意数量（包括零）的类型匹配，不同于模板只和一种类型匹配

- 展开参数包：不能使用索引访问

- 使用递归解包
  
---

# **其他功能**

- 并行编程：`thread_local` 使变量成为静态，与线程生命周期有关

- 新增库：`random` `chrono` `tuple` `ratio` `regex`

- 低级编程支持

  - 允许共用体有构造函数和折构函数，但不能有虚函数
  - 使用 `alignas` 控制对齐方式
  - 使用 `constexpr` 在编译阶段确定常量

- 杂项

  - 字面量运算符
  - 调试工具宏 `assert` 在运行时进行断言检查
  - `static_assert` 在编译阶段对断言进行测试

- STL

- Boost库