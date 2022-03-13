# **琐碎**

- IO 对象无拷贝或赋值（只能使用引用）

- IO 库条件状态

  ![20220313121553](https://raw.githubusercontent.com/Be-A-God/Drawing-bed/main/note/20220313121553.png)
  ![20220313121608](https://raw.githubusercontent.com/Be-A-God/Drawing-bed/main/note/20220313121608.png)

--- 

# **管理输出缓冲**

- 如果程序异常终止，输出缓冲区不会被刷新

- 每个流最多同时关联到一个流；多个流可以同时关联到同一个 `ostream`

---

# **文件输入输出**

- 文件模式

  - `in` 只读
  - `out` 只写
  - `app` 追加
  - `ate` 定位文件末尾
  - `trunc` 截断
  - `binary` 二进制方式