# Pyinstaller py文件打包为exe

## 1. 运行命令

### 1.1. 直接运行

直接在CMD中运行

```python
pyinstaller -F `*.py`
```


> **注意**：
>
> 1. 如果是在新建的python环境中，即系统未配置环境变量，`pyinstaller` 用 `pyinstaller.exe` 的路径指定（在 `pyhon` 文件目录的 `Scripts` 文件夹下）
> 2. 在运行的过程中，缓存文件以及最后生成文件会直接生成在当前cmd目录下。因此，建议先通过 cmd命令 `cd` 到项目文件夹。
> 3. 所有文件路径，建议使用绝对路径，避免出错。
> 4. 运行时，避免使用中文路径，以防出错。

### 1.2. 相关参数

常用参数

| -F, –onefile                | 打包一个单个文件，如果你的代码都写在一个.py文件的话，可以用这个，如果是多个.py文件就别用 |
| :-------------------------- | :----------------------------------------------------------- |
| -D, –onedir                 | 打包多个文件，在dist中生成很多依赖文件，适合以框架形式编写工具代码，我个人比较推荐这样，代码易于维护 |
| -d, –debug                  | 产生debug版本的可执行文件                                    |
| **-w,–windowed,–noconsole** | 使用Windows子系统执行.当程序启动的时候不会打开命令行(只对Windows有效) |
| **-c,–nowindowed,–console** | 使用控制台子系统执行(默认)(只对Windows有效)pyinstaller -c xxxx.pypyinstaller xxxx.py –console |
| -X, –upx                    | 如果有UPX安装(执行Configure.py时检测),会压缩执行文件(Windows系统中的DLL也会)(参见note) |
| -o DIR, –out=DIR            | 指定spec文件的生成目录,如果没有指定,而且当前目录是PyInstaller的根目录,会自动创建一个用于输出(spec和生成的可执行文件)的目录.如果没有指定,而当前目录不是PyInstaller的根目录,则会输出到当前的目录下. |
| –icon=<FILE.ICO>            | 将file.ico添加为可执行文件的资源(只对Windows系统有效)，改变程序的图标 pyinstaller -i ico路径 xxxxx.py |

例子：

[Pyinstaller（Python打包为exe文件）](http://blog.itpub.net/26736162/viewspace-2644904/)

[PyInstaller打包详解](https://yujunjiex.gitee.io/2018/10/18/PyInstaller%E6%89%93%E5%8C%85%E8%AF%A6%E8%A7%A3/)

## 2. 常见问题

##### 1. **打包后exe文件太大**

1. 经过自己的测试，打包是会把安装的所有库（包括`.py`中未引入的库）都打包进去。
2. 建议新建一个python环境，只安装`.py`中引入的库，然后再运行`pyinstaller`命令打包。

##### 2. **打包过程中跳出 UnicodeDecodeError: 'utf-8' codec can't decode byte 0xce in position**

先在`cmd`中执行`chcp 65001`命令，再执行`pyinstaller`命令。[参考](https://blog.csdn.net/qq_35203425/article/details/80992870)

##### 3. **打包完成后，运行exe提示 No module named XXX**

1. 在`*.spec`文件里的`hiddenimports = []`中添加提示缺少的库。

2. 在`cmd`命令中执行`pyinstaller.exe -F *.spec`  

    [参考1](https://blog.csdn.net/qq_40587575/article/details/86500445), [参考2](https://segmentfault.com/a/1190000019632268?utm_source=tag-newest)

## 3. python虚拟环境打包exe

不建议使用Anaconda建立虚拟环境，经实测，使用Anaconda打包后exe巨大（Anacoda打包300MB+，新建Python环境打包60MB+）。



