# FAQ

## win10上已存在pthon2，安装python3

1. 下载并安装Python3
2. 手动配置环境变量
3. 将python3文件夹下的python.exe和pythonw.exe更名为python3.exe和pythonw3.exe
4. 对照第3步，将python2下的相应文件改名为python2
5. 两个版本python的pip共存：分别重新安装
    - ``python3 -m pip install --upgrade pip --force-reinstall``
    - ``python2 -m pip install --upgrade pip --force-reinstall``
6. 验证：
    - ``python3 -V``
    - ``pip3 -V``
    - ``python2 -V``
    - ``pip2 -V``

## python2手动更新安装pip

- 下载pip包（pypi）
- 解压
- 终端进入到解压目录
- 执行命令：
    - ``python2 setup.py build``
    - ``python2 setup.py install``
- 验证：``pip2 -V``

## numpy库安装

1. 下载numpy源
2. 终端切换到numpy文件所在目录
3. 执行命令：``pip install [numpy文件名]``

## Python任意数量关键字实参声明
> **

## 数据存储

- ``json.dump()``
- ``json.load()``

## 测试unitest

- 创建一个测试类，必须继承unittest.TestCase类
- 测试方法名必须以test_开头，这样在测试的时候才会自动执行

## 变量作用域

- L、E、G、B
- 查找规则：L -> E -> G -> B
- python中只有module、class及函数（def、lambda）才会引入新的作用域

## 类方法

- 装饰器 ``@classmethod`` 可以将方法标识为类方法。类方法的第一个参数必须为``cls``，而不再是``self``。

## 静态方法

- 装饰器``@staticmethod``可以将方法标识为静态方法。静态方法的第一个参数不再指定。

## 构造方法

- ``__init__``：初始化操作可放入其中

## 变量

- 类变量：共享的
- 对象变量：每一个独立的对象或实例所拥有
> __xxxx__：特殊变量，可直接访问，不是private变量

## 访问控制

- ``__private_attr``：私有属性
- ``__private_method``：私有方法
- 以一个下划线开头的属性或方法为：protected