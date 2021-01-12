# Anaconda 基本命令

1.

在安装完Anaconda之后，建议修改源为[conda-forge](https://conda-forge.org/)，并设为主要的源：

```cmd
conda config --add channels conda-forge
conda config --set channel_priority strict
conda upgrade --all

conda install <package-name>
conda install -c <channel-name> <package-name>
```

