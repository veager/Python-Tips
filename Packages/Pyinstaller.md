# Pyinstaller py文件打包为exe

## 1. 运行命令

### 1.1. 直接运行

直接在CMD中运行

```cmd
pyinstaller -F `*.py` -i="*.ico" --upx-dir="*\upx.exe" --distpath="*folder"
```


> **注意**：
>
> 1. 如果是在新建的python环境中，即系统未配置环境变量，`pyinstaller` 用 `pyinstaller.exe` 的路径指定（在 `pyhon` 文件目录的 `Scripts` 文件夹下）
> 2. 在运行的过程中，缓存文件以及最后生成文件会直接生成在当前cmd目录下。因此，建议先通过 cmd命令 `cd` 到项目文件夹。
> 3. 所有文件路径，建议使用绝对路径，避免出错。
> 4. 运行时，避免使用中文路径，以防出错。

### 1.2. 相关参数

>- `-F` 可替换为
>- `*.py` 带打包`py`文件路径，可替换为`*.spec`文件路径
>
>- `-i=` 指定图标路径
>- `--upx-dir=` 指定`upx.exe` 路径。实测UPX压缩无效果
>- `--distpath=` 指定存放打包生成的`exe`文件的文件夹。

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



