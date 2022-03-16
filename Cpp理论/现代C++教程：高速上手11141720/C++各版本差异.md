# **被弃用特性**

- 不允许字符串字面值常量赋给一个 `char *` ，而应该是 `const char *`
- C++98异常说明、`unexpected_handler` 、`set_unexpected()` 等被 `noexcept` 取代
- 使用 `unique_ptr` 取代 `auto_ptr`
- `register` 关键字被弃用，无任何含义
- `bool` 类型的 `++` 操作被弃用
- 类有折构函数时，为其生成拷贝构造函数和拷贝赋值运算符的特性被弃用
- C风格类型转换被弃用，使用四种强制类型转换运算符
- `C++17` 弃用一些C标准库， `<ccomplex>` `<cstdalign>` `<cstdbool>` `<ctgmath>`
- 参数绑定等特性被弃用

---

# **琐碎**

- 使用 `extern "C"` 实现对C的兼容

- 使用 `nullptr` 区分0和空指针， `NULL` 尽量不用

- `constexpr` 

  - 该关键字表示编译期间就确定为常量表达式
  - 使用该关键字的函数可以使用递归
  - `C++14` 开始， `constexpr` 函数内部可以使用局部变量、循环和分支等简单语句
  - `C++11` 只能有单条返回语句

- 变量及其初始化

  - `C++17` 开始， `if` 和 `switch` 语句中可以声明局部变量
  - 例如： `if (int i = 1; i != 3) {}`

- 初始化列表：使用 `std::initializer_list` 允许构造函数和其他函数参数一样使用初始化列表

- `C++17` 结构化绑定

  - `C++11` 使用 `std::tuple` 返回多个值
  - `C++17` 使用形如 `auto [x, y, ...] = fun();` 接受多个返回值

---

# **类型推导**

- `auto` 不能用于函数传参，不能推导数组类型

- `decltype` 针对表达式进行类型推导

- `std::is_same<T, U>` 判断 T 和 U 两个类型是否一样

- 尾置返回类型

  - `C++11` 引入

      ![20220316200345](https://raw.githubusercontent.com/Be-A-God/Drawing-bed/main/note/20220316200345.png)

  - `C++14` 完善，直接使用 `auto` 即可

      ![20220316200355](https://raw.githubusercontent.com/Be-A-God/Drawing-bed/main/note/20220316200355.png)

- `C++14` 使用 `decltype(auto)` 主要用于对转发函数或封装的返回类型进行推导

---

# **控制流**

- `C++17` 将 `constexpr` 关键字引入 `if` 语句： `if constexpr ()` 编译时判断

- `C++11` 基于范围的 `for` 循环

- 模板

  - `C++11` 引入外部模板

      ![20220316200829](https://raw.githubusercontent.com/Be-A-God/Drawing-bed/main/note/20220316200829.png)

  - `C++11` 模板中连续右尖括号变得合法

  - `C++11` 使用 `using` 为模板定义一个新名称， `typedef` 不支持模板别名

  - `C++11` 可以为模板参数指定默认值

  - `C++11` 允许定义多个参数（包含0个）的模板，使用 `typename... Args` ，函数和类都支持

  - 对参数解包

    - 使用递归解包

    - `C++17` 使用变参模板解包

      ![20220316201129](https://raw.githubusercontent.com/Be-A-God/Drawing-bed/main/note/20220316201129.png)

    - 初始化列表展开

      ![20220316201158](https://raw.githubusercontent.com/Be-A-God/Drawing-bed/main/note/20220316201158.png)

- `C++17` 支持折叠表达式

  ![20220316201237](https://raw.githubusercontent.com/Be-A-God/Drawing-bed/main/note/20220316201237.png)

- `C++17` 引入非类型模板参数推导：使用 `auto` 占位符，编译器辅助完成类型推导

    ![20220316201336](https://raw.githubusercontent.com/Be-A-God/Drawing-bed/main/note/20220316201336.png)

---

# **面向对象**

- `C++11` 引入委托构造：同一个类中一个构造函数调用另一个构造函数（不支持同时使用初始化列表）
- `C++11` 使用关键字 `using` 引入继承构造
- 显式虚函数重载： `override` 关键字显式重载（基类已有的虚函数）， `final` 防止类被继承和虚函数重载
- 显式禁用默认函数： `= default` 显式声明使用编译器生成的构造； `= delete` 显式拒绝编译器生成构造
- `C++11` 引入强类型枚举：使用 `enum class` 语法声明，可以在枚举类型后使用冒号及类型关键字指定枚举值的类型（强类型默认 `int` ，非强无默认）

---

# **`lambda` 表达式**

- 基本语法： `[捕获列表](参数列表) multable(可选) 异常属性 -> 返回类型 {函数体}`
- 捕获：值捕获（ `lambda` 表达式创建时值就确定）、引用捕获、隐式捕获（ `=` `&` ）
- `c++14` 允许右值捕获，允许捕获成员任意表达式进行初始化
- `C++14` 引入泛型 `lambda` ，支持形参使用 `auto` 关键字

---

# **函数对象包装器**

- `C++11` 使用 `std::function` 作为函数容器

- `std::bind` `std::placeholder` ：前者绑定函数调用的参数，后者表示第x个参数的占位符

  ![20220316203329](https://raw.githubusercontent.com/Be-A-God/Drawing-bed/main/note/20220316203329.png)

---

# **右值引用**

- 左值：表达式之后依然存在的持久对象

- 右值：表达式结束后就不再存在的临时对象

- 纯右值：纯字面量或者求值结果相当于字面量或匿名临时对象

- `C++11` 引入将亡值：即将销毁、却能够被移动的值

- 右值引用使得临时值的生命周期得以延长

- `C++11` 引入 `std::move` ，将左值转换为右值；右值引用变量实际是一个左值

- 移动语义：将资源转移，记得原资源置空（指针）

- 完美转发：使用 `std::forward`

  ![20220316203708](https://raw.githubusercontent.com/Be-A-God/Drawing-bed/main/note/20220316203708.png)

---

# **容器**

- 线性容器

  - `std::array` 为固定大小的数组对象，使用时指定类型和大小（常量表达式），不会退化为指针类型
  - `std::forward_list` 列表容器，方法和 `std::list` 基本类似，不提供 `size()` 方法

- 无序容器

  - `C++11` 引入 `std::unordered_map/std::unordered_multimap` 和 `std::unordered_set/std::unordered_multiset`

- 元组

  - 核心函数： `std::make_tuple` 构造元组； `std::get` 获得元组某位置的值； `std::tie` 元组拆包
  - `C++14` 新增使用类型来获取元组中的对象（使用 `std::get` ）
  - `C++17` 引入运行时索引（索引值可以是变量）： `std::variant<>`
  - 使用 `std::tuple_cat` 进行元组合并

---

# **智能指针与内存管理**

- `C++11` 引入智能指针对象

- `std::shared_ptr` ：允许多个智能指针指向同一个对象，引用计数为零时将对象删除

  - 使用 `std::make_shared` 返回对象的 `std::shared_ptr` 指针
  - 使用 `get()` 方法获取原指针
  - 使用 `reset()` 方法减少引用计数
  - 使用 `use_count()` 方法查看对象的引用计数

- `std::unique_ptr` ：独占的智能指针

  - `C++14` 引入 `std::make_unique` 方法

- `std::weak_ptr` ：弱引用指针

  - 不增加引用计数
  - 没有 `*` `->` 运算符
  - 只能用于检查 `std::shared_ptr` 是否存在
  - `expired()` 方法查看资源是否被释放

---

# **正则表达式**

- `C++11` 引入正则表达式操作库 `std::regex` 

- 方法： `std::regex` 生成正则表达式； `std::regex_match` 匹配表达式和内容； `std::smatch` 获取匹配结果

- 规则

    ![20220316204857](https://raw.githubusercontent.com/Be-A-God/Drawing-bed/main/note/20220316204857.png)
    ![20220316204908](https://raw.githubusercontent.com/Be-A-God/Drawing-bed/main/note/20220316204908.png)

---

# **并行与并发**

- 方法： `std::thread` 用于创建线程； `get_id()` 获取线程ID； `join` 加入一个线程

- `C++11` 引入 `std::mutex` 类；成员函数 `lock()` 上锁， `unlock()` 解锁

- `C++11` 提供RAII语法的模板类 `std::lock_guard` ，互斥量只需要上锁，离开作用域会自动解锁释放

- `std::unique_lock` 的对象会以独占所有权的方式管理 `mutex` 上的对象的上锁和解锁操作

- 期物 `std::future`

  - `C++11` 提供访问异步操作结果的途径
  - 条件变量 `std::condition_variable` 实例被创建时唤醒等待线程避免死锁
  - `notify_one()` 唤醒一个线程； `notify_all()` 通知所有线程

- `C++11` 引入 `std::atomic` 模板能够实例化一个原子类型，将读写最小化到单个CPU值令

  - 通过 `std::atomic<T>::is_lock_free` 检查原子类型是否需要支持原子操作

- 一致性模型

  - 线性一致性：所有线程的操作顺序与全局时钟下的顺序一致
  - 顺序一致性：只要求任何一次读操作都能读到数据最近一次写入的数据，之前的写顺序并无保障
  - 因果一致性：只需要因果关系的操作顺序得到保障即可
  - 最终一致性：只保障某个操作在未来的某个时间节点上会被观察到

- 内存顺序（ `C++11` 引入）

  - 宽松模型： 通过 `std::memory_order_relaxed` 指定，单线程内原子操作顺序执行
  - 释放/消费模型：通过 `std::memory_order_release` 指定，限制进程间操作顺序
  - 释放/获取模型：在释放和获取之间规定时序
  - 顺序一致性模型：通过 `std::memory_order_seq_cst` 指定

---

# **其他杂项**

- `C++11` 将 `long long int` 至少64位的类型纳入标准库

- `C++11` 引入 `noexcept` 函数不能抛出异常，能够封锁异常不会在外部触发

- 字面量

  - `C++11` 引入原始字符串字面量（无需转义）；同时支持自定义分割符

      ![20220316211334](https://raw.githubusercontent.com/Be-A-God/Drawing-bed/main/note/20220316211334.png)

  - `C++11` 自定义字面量：通过重载 `""` 运算符；支持整型、浮点型、字符串、字符

      ![20220316211344](https://raw.githubusercontent.com/Be-A-God/Drawing-bed/main/note/20220316211344.png)
      ![20220316211352](https://raw.githubusercontent.com/Be-A-God/Drawing-bed/main/note/20220316211352.png)

- 内存对齐

  - `C++11` 引入关键字 `alignof` 和 `alignas` 
  - `alignof` 获得与平台对齐相关的值
  - `alignas` 能够自定义对齐方式