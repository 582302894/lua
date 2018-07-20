关键词  
`and` `break` `do` `else` `elseif` `end` `false` `for` `function` `if` `in` `local` `nil` `not` `or` `repeat` `return` `then` `true` `until` `while`  
全局变量 约定以 _+大写字母(_VERSION) 用于内部全局变量
访问一个没有初始化的变量得到 nil
删除变量将变量值设为 nil


###数据类型
nil、boolean、number、string、userdata、function、thread、table  

- number 表示双精度类型的实浮点数 
- function 由 C 或 Lua 编写的函数
- userdata 表示任意存储在变量中的C数据结构
- thread 表示执行的独立线路，用于执行协同程序
- table Lua 中的表（table）其实是一个"关联数组"（associative arrays），数组的索引可以是数字或者是字符串。在 Lua 里，table 的创建是通过"构造表达式"来完成，最简单构造表达式是{}，用来创建一个空表。  

####nil
    nil 类型表示一种没有任何有效值，它只有一个值 -- nil
    nil 还有一个"删除"作用
    nil 作比较时应该加上双引号 ",type(X)==nil 结果为 false 的原因是因为 type(type(X))==string。

####boolean
    Lua 把 false 和 nil 看作是"假"，其他的都为"真":

####number
    Lua 默认只有一种 number 类型 -- double（双精度）类型（默认类型可以修改 luaconf.h 里的定义）

####string
    字符串由一对双引号或单引号来表示
    也可以用 2 个方括号 "[[]]" 来表示"一块"字符串
    字符串连接用 .. ,左右有一个空格

```html
html = [[
<html></html>
]]
```

####table
    在 Lua 里，table 的创建是通过"构造表达式"来完成，最简单构造表达式是{}，用来创建一个空表
    Lua 里表的默认初始索引一般以 1
    没初始的 table 都是 nil

```lua
local tbl1 = {}
local tbl2 = {"apple", "pear", "orange", "grape"}
local t1={a="b",b="c"}
```

####function
    在 Lua 中，函数是被看作是"第一类值（First-Class Value）"，函数可以存在变量里,赋值给变量
    function 可以以匿名函数（anonymous function）的方式通过参数传递

```lua
function f1()
end
f2=f1
f2()

function f1(fun)
end

f1(
    function()
    end
)
```

####thread
    在 Lua 里，最主要的线程是协同程序（coroutine）。它跟线程（thread）差不多，拥有自己独立的栈、局部变量和指令指针，可以跟其他协同程序共享全局变量和其他大部分东西。
    线程跟协程的区别：线程可以同时多个运行，而协程任意时刻只能运行一个，并且处于运行状态的协程只有被挂起（suspend）时才会暂停。

####userdata
    userdata 是一种用户自定义数据，用于表示一种由应用程序或 C/C++ 语言库所创建的类型，可以将任意 C/C++ 的任意数据类型的数据（通常是 struct 和 指针）存储到 Lua 变量中调用