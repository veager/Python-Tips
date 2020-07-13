# Python Tips

自己在使用Python过程中的一些总结

## 1. 多Python程序

可以通过自己安装Python，**不**设定环境变量

### 1.1. 指定Python环境运行`.py`文件

1. 首先，把带运行`.py`文件移动到与Python环境同一磁盘。

2. 然后，在`cmd`中指定python.exe 使用指定的python环境运行指定的`.py`文件

3. `cd`命令到`.py`文件目录，再使用**绝对路径**指定python.exe运行`.py`文件

4. 在`cmd`中执行命令`python_path  pyfile_path`

### 1.2. **pip**安装库

1. 首先，**cmd**窗口中运行`.\Scripts\pip.exe`
2. 然后，执行`pip`命令安装\卸载\更新库



## 2. py文件打包exe

### 2.1. pyinstaller

例子：[Pyinstaller（Python打包为exe文件）](http://blog.itpub.net/26736162/viewspace-2644904/)

### 2.1.1. 常见问题

- **打包后exe文件太大**

1. 经过自己的测试，打包是会把安装的所有库（包括`.py`中未引入的库）都打包进去。
2. 建议新建一个python环境，只安装`.py`中引入的库，然后再运行`pyinstaller`命令打包。

- **打包过程中跳出 UnicodeDecodeError: 'utf-8' codec can't decode byte 0xce in position**

先在`cmd`中执行`chcp 65001`命令，再执行`pyinstaller`命令。[参考](https://blog.csdn.net/qq_35203425/article/details/80992870)

- **打包完成后，运行exe提示 No module named XXX**
1. 先在`.spec`文件里的`hiddenimports = [ ]`中添加提示缺少的库。
2. 再在`cmd`命令中执行`pyinstaller myscript.spec`  [参考1](https://blog.csdn.net/qq_40587575/article/details/86500445), [参考2](https://segmentfault.com/a/1190000019632268?utm_source=tag-newest)



## 1. 安装包

### 1.1. conda安装包

`conda install librosa`

当出现以下错误提示时：

ackagesNotFoundError: The following packages are not available from current channels:

1. 执行`anaconda search -t conda X`，显示可用的版本 

2. 选择适合自己的版本，执行：`conda install -c https://conda.anaconda.org/X` `X`为所选择的安装的包

   如：`conda install -c https://conda.anaconda.org/conda-forge librosa`
   
   

