# prototype
prototype &amp; UI design


test-message


markdown


 
  | 项目 | 实现前 | 实现后 |
|------|-------|--------|
| 代码组织方式 | 模块/包 二级结构 | 包/子包 树形结构<br>没有父包的包称为 root 包，root 包及其子包（包括子包的子包）构成的整棵树称为 module |
| 编译单元 | 包 | 包（每个子包单独编译） |
| 访问修饰符 | public：<br>可修饰顶层和非顶层成员，包内外可见<br>default（不写）：仅本包内可见<br>protected：只能修饰 class 的成员，本包内可见、本 class 及其子类可见<br>private：不能修饰 top-level 成员、仅当前作用域可见 | 以下所有访问修饰符均可修饰顶层和非顶层成员<br>public：本 module 内外可见<br>protected：本 module 和子类型内可见<br>internal：本包及其子树可见<br>private：修饰顶层声明时仅本文件内可见，修饰非顶层声明时仅当前类型或扩展定义内可见 |
| package 访问修饰符| 无 | package a.b（= public package a.b）<br>protected package a.b<br>internal package a.b |
| import 访问修饰符 | public import<br>import | public import<br>protected import<br>internal import<br>import（= private import） |
| 从 module 导入的语法 | from std import time.\* | 不再有 from 语法，只有 import std.time.\* 的语法 |
| 多导入的语法 | from std import time.\*, math.\*<br>import a.\*, b.\* | import std.{time.\*, math.\*}<br>import {a.\*, b.\*} |
| 导入的语义 | from std import time.Duration<br>可以同时看到 time 和 Duration 这两个符号 | import std.time.Duration<br>只看能看到 Duration 这一个符号 |
| 单导入 | 可以导入顶层声明，不可以导入包名<br>from std import time // error<br>from std import time.Duration // OK | 可以导入顶层声明、也可以导入包名<br>import std.time // ok<br>import std.time.Duration // OK |
| 别名导入 | from std import time.\* as stdTime.\* // OK<br>from std import time.Duration as stdDuration // OK | import std.time.\* as stdTime.\* // error<br>import std.time.Duration as stdDuration // OK |
| 别名导入的作用域 | 和当前包顶层声明处于同一作用域<br>from std import time.Duration as stdDuration<br>let stdDuration = 1 // error: redefinition | 和当前包顶层声明处于不同作用域，且优先级更低，若 shadow 则告警<br>import std.time.Duration as stdDuration // warning: shadow<br>let stdDuration = 1 // OK |
| 重复导入并取别名 | 使用 import as 对导入的声明重命名后，当前包内只能使用别名，无法使用原名<br>from std import time.Duration // error: time.Duration is renamed<br>from std import time.Duration as stdDuration | 允许使用多条导入语句分别导入原名和重命名<br>import std.time.Duration<br>import std.time.Duration as Duration1<br>import std.time.Duration as Duration2<br><br>let _ = Duration.second // OK<br>let _ = Duration1.second // OK<br>let _ = Duration2.second // OK |
  
  
