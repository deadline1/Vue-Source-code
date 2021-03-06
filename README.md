# Vue
关于Vue源码（vue2.x）的学习（从手写模仿到理解代码）

# Vue模板

使用步骤:
1. 编写页面模板
  1. 直接在HTML标签中写标签
  2. 使用template
  3. 使用单文件(<template/>)
2. 创建Vue实例
  1. 在Vue的构造函数中提供：data, methods, computed, watcher, props, ...
3. 将Vue挂在到页面中(mount)

# 数据驱动模型

Vue的执行流程

1. 获得模板：模板中有“坑”
2. 利用Vue构造函数中所提供的数据来“填坑”，得到可以在页面中显示的标签
3. 将标签替换页面中原来有坑的标签

Vue利用我们提供的数据和页面模板生成了一个HTML标签(node元素)
替换到了页面中放置模板的位置

我们该如何实现？？？

# 简单的模板渲染

目标：

1. 怎么讲真正的DOM转换为虚拟DOM
2. 怎么将虚拟DOM转换为真正的DOM

思路参考深拷贝

# 函数柯里化

概念：
1. 柯里化：一个函数原本有多个参数，只传入**一个**参数，生产一个新函数，由新函数接收剩下的函数来运行得到结构
2. 编函数： 一个函数原本有多个参数，只传入**一部分**参数，生产一个新函数，由新函数接收剩下的函数来运行得到结构
3. 高阶函数：一个函数**参数是一个函数**，该函数对参数这个函数进行加工，得到一个函数，这个加工用的函数就是高阶函数

为什么要用函数柯里化？ 为了提升性能，使用柯里化可以缓存一部分能力

使用两个案例来说明：

1. 判断元素：

Vue本质上是使用HTML的字符串作为模板的，将字符串的模板转换为AST，再转换为VNode

- 模板 => AST（抽象语法树）
- AST => VNode
- VNode => DOM

最消耗性能是字符串解析(模板 => AST)，“波兰式”表达式，栈结构运算


2. 虚拟DOM的render方法

