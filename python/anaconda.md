# Anaconda

## windows中安装anaconda手动设置环境变量

* 新建环境变量`ANACONDA_HOME`，值为`D:\Develop\Anaconda3`
* 在path中添加环境变量：`%ANACONDA_HOME%;%ANACONDA_HOME%\Scripts;%ANACONDA_HOME%\Library\bin`

## **更改jupyter的工作目录**

* 命令终端执行：`jupyter notebook --generate-config`
* 在原工作目录下生成文件：`C:\Users\Barry\.jupyter\jupyter_notebook_config.py`
* 用编辑器打开该文件修改：`c.NotebookApp.notebook_dir = ''`

## **Anaconda更改包管理源至国内源**

```text
conda config --add channels https://mirrors.tuna.tsinghua.edu.cn/anaconda/pkgs/free/
conda config --set show_channel_urls yes
```

## **conda 基本命令**

* 更新所有库：`conda update --all`
* 更新conda：`conda update conda`
* 更新anaconda：`conda update anaconda`
* 更新pip：`python -m pip install --upgrade pip`
* 更新指定库：`pip install 库名 --upgrade`
* 卸载指定库：`pip uninstall 库名`

