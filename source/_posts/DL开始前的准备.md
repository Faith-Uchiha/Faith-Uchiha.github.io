---
title: DL开始前的准备
date: 2017-11-07 15:13:37
update: 2017-11-07 15:13:37
categories: 机器学习
tags: 环境配置

---

## 环境配置

1. Anaconda下载和安装。

   - [下载网址](https://mirrors.tuna.tsinghua.edu.cn/anaconda/archive/) ，选择最新版本。   安装一路默认。
   - 安装完后，**为了快速下载各种Python包**，使用下列命令，添加Anaconda仓库镜像

   ```
   conda config --add channels https://mirrors.tuna.tsinghua.edu.cn/anaconda/pkgs/main/

   conda config --add channels https://mirrors.tuna.tsinghua.edu.cn/anaconda/pkgs/free/

   conda config --set show_channel_urls yes	
   ```

   <!-- more -->

    然后，比如你输入

   ``` python
   conda install numpy
   ```

   就可以安装 numpy包。

   - 添加第三方镜像/源

     [教程网站](https://mirrors.tuna.tsinghua.edu.cn/help/anaconda/)

   - 更新 所有包

     ```
     conda upgrade --all
     ```

2. Anaconda基础命令

      - 管理包

        - conda install name——安装包

          可以通过"="来**指定版本**，

          ```
           eg：conda install numpy=1.0
          ```

          ​ 可以同时安装多个包；安装某个包会自动安装它的依赖项

        - conda remove name——删除包

        - conda upgrade --all——更新所有包    conda uprade name——更新某个包

        - conda list——列出已安装的包

        - conda search name——不知道要安装的包的确切名字，可以搜索

      - 管理环境

        - conda create -n env_name list_of_packages ——创建环境

          ​   -n env_name表示**指定**环境的**名称**     后面跟着的是**要安装**在环境**的包列表（即一次安装多个包）名称** 

          **创建环境**对使用**不同版本的Python**很有利，可以在Python2.x和Python3.x中自由切换。例子如下

                ```
          conda create -n py2 python=2
          conda create -n py3 python=3
                ```

          ​ 上面的写法，安装的是Python2和Python3**最新版**，如果想安装具体的，要写=2.x

        - activate env_name——进入环境

          在环境中，也可以用包管理的基础命令（conda install/list等）		

        - deactivate——离开环境

        - conda info -e/conda env list ——列出所有环境

          当前正在使用的环境，会有一个*

        - conda env remove -n name/conda remove -n name --all ——删除环境。name是环境名称

        - conda env export > environment.yaml——把**环境**以及已经安装的包**导出**到.yaml文件

        - conda env create -n name -f xxx.yaml——**通过环境文件**来创建环境

          以上env均为必要，原样输入即可，不是指的环境名称

3. Jupyter Notebook操作

      - 在Anaconda Prompt中输入

      ```
      jupyter notebook
      ```

      ​	就会在浏览器中打开

      - 改变打开的路径

        输入命令：

      ```
      jupyter notebook --generate-config
      ```

      ​	会 显示jupyter_notebook_config.py文件路径，打开并找到

      ```
      ## The directory to use for notebooks and kernels. 
      #c.NotebookApp.notebook_dir = ''
      ```

      ​	改为

      ```
      ## The directory to use for notebooks and kernels. 
      c.NotebookApp.notebook_dir = '你要设置的Notebook路径'
      ```
      - 关闭正在运行的notebook

        在tab里的Running中 关闭

      - notebook的操作：

        - shift + enter：一步一步执行
        - 菜单的Cell->Run All：一次全部执行

      - 创建、使用Notebook

        - 界面右侧，New->Python3 创建自己的Notebook
        - 主要工作区被称为单元格（cell），**代码单元格(Code cell)，以[]开头**，**按下shift + enter运行**，并且光标移动到新的单元格。
        - 一个强大的特性：可以**修改旧的**单元格，再次shift + enter运行，会得出**新的结果**。
        - 插入别的类型的单元格：insert插入单元格，**选择类型Heading(标题)/Markdown**，就可以使用markdown语法。
        - 单元格高级操作：Edit菜单，单元格可以，删除、移动、剪贴、合并（把两段代码合并一起 ）
        - markdown单元格**支持Latex**语法。可以写些数学公式。
        - 支持matplotlib。要先用**%matplotlib inline**告诉Jupyter Notebook我们要用这个库，后面该怎么画怎么画


​          