# python课瓦力安装包问题手册

## 检查电脑是否安装过py

### 查看电脑是否安装 Python

#### Windows

1. 按下 `Win + R`，输入 `cmd` 回车，打开命令提示符
2. 输入下面命令，回车：

```
python --version
```

或者

```
py --version
```

#### 结果说明

- 输出版本号，例如 `Python 3.11.4` → **已经安装**
- 提示 `'python' 不是内部或外部命令` → **没安装，或者没加到系统环境变量**

> 小提示：部分电脑微软商店会拦截 python 命令，优先试 `py --version`

## 安装py

Python3.7.3 的安装界面，**最重要：一定要勾选底部的 `Add Python 3.7 to PATH`**✅

### 操作步骤

1. 把方框 `Add Python 3.7 to PATH` **打上√**（图里现在是空的，必须勾选）
2. 两种安装方式二选一：

点击 **Install Now**

- 自动安装到：`C:\Users\Intel\AppData\Local\Programs\Python\Python37`
- 自动装好 IDLE、pip，安装完就可以用。

✅ **Setup was successful = Python 安装成功！**

### 操作

1. 可以点 `Disable path length limit`（推荐点一下，解除 Windows 文件路径长度限制，以后装库不容易报错，会弹管理员确认，点允许）
2. 然后点右下角 **Close** 关闭安装窗口。

### 验证是否能用（关键）

1. 关闭已经打开的 cmd 窗口（**必须重开 cmd，旧终端不会读取新环境变量**）
2. 新打开 cmd，输入：

```
python --version
```

正常输出：`Python 3.7.3`

再测试 pip（包管理器）：

```
pip --version
```

会打印 pip 版本号。

> 如果提示不是内部命令，说明刚才 PATH 勾选没生效，需要手动配置环境变量。

## 安装瓦力包

Walimaker 是**瓦力工厂的定制 Python 库**，不是 Python 官方自带的库。

> Python 本体只是基础语言，本身不会带游戏窗口、图形、动画、硬件交互这些功能。 这个 zip 压缩包里面就是课程专用的扩展模块。

### 完整操作步骤

1. 先把 `安装程序2020.2.29.zip` 全部解压出来，记住解压后的文件夹路径。

> 举例：解压到 `D:\Walimaker\安装程序2020.2.29`，这个文件夹里面能直接看到`setup.py`文件。

1. 在 cmd 里面输入 cd 命令，切换到这个解压文件夹。 示例（按你自己真实路径改）：

```
cd /d D:\Walimaker\安装程序2020.2.29
```

> `/d` 作用：如果你的压缩包解压在 D 盘，必须加这个，否则切不过去。

1. 切换完成后，再执行安装命令：

```
python setup.py install
```

### 验证 Walimaker 模块是否安装成功

#### 方法 1：cmd 里直接测试（最快）

1. **新开一个 cmd 窗口**（一定要新开，旧窗口环境不更新）
2. 输入 `python` 回车，进入 Python 交互环境，会出现 `>>>` 提示符

```
python
```

1. 在 `>>>` 后面输入导入语句，回车

```
import Walimaker
```

### 判断结果

✅ **没有任何报错、直接回到下一行 >>>** → **安装成功** ❌ 弹出 `ModuleNotFoundError: No module named 'Walimaker'` → 安装失败

输入 `exit()` 回车，可以退出 Python 交互界面。

#### 报错解析

`AttributeError: module 'pymunk' has no attribute 'constraint'` ✅ Walimaker 本体已经装上了！但是**缺少配套依赖库 pymunk，或者 pymunk 版本不对**。 Walimaker 做物理碰撞要用到 pymunk，版本错了就找不到`constraint`。

这个老版 Walimaker（2020）要求 **pymunk 5.x 版本，不能装新版 6.x**。

#### 解决步骤

1. 退出 python 交互界面，输入 `exit()` 回车回到 cmd 黑窗口（不要在 >>> 里面执行 pip）
2. 先卸载现在错误的 pymunk

```
pip uninstall pymunk
```

弹出确认输入 `y`回车。

1. 安装指定旧版本 pymunk 5.7.0（适配这个 Walimaker）

```
pip install pymunk==5.7.0
```

1. 安装完成，**新开 cmd 窗口**，再次进入 python 测试

```
python
import Walimaker
```

> 如果不再报红色报错，只打印 pygame 那行 hello 文字，就代表完全成功。

✅ pymunk‑5.7.0 已经安装成功！

> 黄色提示 pip 版本不用管，不影响 Walimaker 运行。

### 接下来操作

1. **关掉当前整个 cmd 窗口，重新打开一个新的 cmd**（关键，旧终端还缓存旧库状态）
2. 输入 `python` 回车进入交互模式
3. 执行

```
import Walimaker
```

#### 两种结果

1. 只打印 pygame 的 hello 文字，**没有红色报错** → 全部安装完成，可以写课程代码：`from Walimaker import *`
2. 如果还有红色报错，把完整报错截图发我。

测试完之后，你就可以直接运行瓦力的示例程序了。

## Vscode

### 在代码里打印版本验证（写进 py 文件运行）

```
import sys
print(sys.version)
print(sys.executable)
```

运行后输出应该看到：

- `3.7.3`
- 路径：`C:\Users\Intel\AppData\Local\Programs\Python\Python37\python.exe`

如果路径对，VSCode 环境就配置正确。

配置完，运行测试代码：

```
from Walimaker import *

# setup(宽度,高度) 创建窗口
setup(800, 600)
title("瓦力测试窗口")

# 游戏主循环
while True:
    update()

```

弹出游戏窗口 = 全部搞定。

✅完美！VSCode 现在用的就是正确的 Python3.7.3

```
版本：3.7.3
解释器路径：C:\Users\Intel\AppData\Local\Programs\Python\Python37\python.exe
```

和你 cmd 里面安装 Walimaker 的 Python 完全是同一个。