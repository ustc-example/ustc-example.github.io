# 数字图像分析实验讲义之一——Python开发环境配置

*如果有任何错误，疑问或者建议，请随时联系助教：王云峰（wangyf11@mail.ustc.edu.cn），蒲俊福（pjh@mail.ustc.edu.cn)。*


## 1. Why Python
Python是一门脚本语言，设计优雅简洁，上手容易，而且大量的成熟的库使得用Python来完成任务异常的简单。虽然Python代码本身运行速度较慢，但是许多库底层采用C语言来实现，这样能有效地提高速度。以下是一段Python代码：
```python
from skimage import data, io, filters

image = data.coins()
# ... or any other NumPy array!
edges = filters.sobel(image)
io.imshow(edges)
io.show()
```
这段代码是用scikit-image库对下图左边的硬币图像进行边缘检测，结果如右图：

![硬币边缘检测](assets/01/example_coins.jpg)
可以看到，用很简单的几行代码就可以做到比较好的结果，这就是Python的强大之处。下面介绍具体的开发环境配置。  

## 2. Python安装
### (1). Windows环境
访问[Python官网](https://www.python.org/)， 鼠标放到首页中上位置的`Downloads`，选择`Windows`，然后选择右侧的`Python2.7.14`，就会下载一个名为`python-2.7.14.msi`的安装文件，下载好后，点击安装，安装过程中使用默认选项即可。
### (2). Linux环境
Linux环境下默认安装了Python包，不再需要单独安装
### (3). MacOS
类似Windows环境下的安装，从官网上下载安装包即可。    
安装好后，打开命令行，输入python，如果出来如下界面，就说明Python已经安装好了：

![Python界面](assets/01/python_jiemian.jpg)


**说明**
> 1. Python有2版本和3版本，这两个版本有一定的区别，具体可以看[这里](https://wiki.python.org/moin/Python2orPython3)。在这套教程里面，我们使用Python2来做展示。
> 2. 因为Linux系统下命令操作的简便性，所以以下介绍的命令都在Linux下进行的测试，大部分命令在Windows和MacOS下应该也可以正常执行，如果有问题请联系我们进行反馈。

## 3. pip
pip是Python包管理系统，2.7和3.4以上的Python版本都默认带了pip。安装python的包的方式有很多种，但是pip是官方默认的安装方式，也最容易，因此教程中我们使用pip来管理python的包，并且通过命令行的方式来安装包。常见的使用命令如下：
```bash
pip install package-name #安装包
pip install --upgrade package-name #升级已经安装的包
pip uninstall package-name #卸载包
pip list 					#列出所有安装的包
pip downalod  package-name   #下载包但是不安装
pip install package-name.whl #安装上条命令中下载的包（假设下载的包的名字为package-name.whl）
```
**说明**
> 1. 在Linux环境下，pip安装包到系统目录需要管理员权限，所以可以在前面加`sudo`来执行以上的命令，或者使用`pip install --user package-name`来安装包到自己的家目录下。  

pip详细的教程可以看[这里](https://pip.pypa.io/en/stable/)。

## 4. 可能会用到的python包
下面是本套教程里面可能会用到的Python包，每个包后面有一个简单的解释和官方网站的链接：
### (1). Pillow
Python的图像处理库，包含对众多格式图片的读写，旋转变换等操作，以及一些简单的图像处理算法，网址：<https://pillow.readthedocs.io/en/4.2.x/>，安装方式：
```bash
pip install Pillow
```
### (2). python-opencv
OpenCV的python库，跟C++版本的OpenCV在API上保持一致，除了图像基本操作外，常见的不是最新的图像处理算法和机器学习算法都包含在内，个人感觉：OpenCV的API略微有些复杂，不是很典型的Python风格，不过速度应该是这些库里面比较快的。网址：<http://docs.opencv.org/3.3.0/d6/d00/tutorial_py_root.html>，安装方式：
```bash
pip install opencv-python
```
### (3). scikit-image 
跟[Numpy](http://www.numpy.org/)兼容的Python图像处理算法库，Numpy是众多Python包的基石，Numpy提供的ndarray数组支持矩阵运算和多维数组的运算，众多的操作以及高效的性能使得其在科研领域得到广泛的应用。scikit-image提供了完善的文档以及丰富的示例，可以在这里开始学习：<http://scikit-image.org/>。安装方式：
```bash
pip install scikit-image
```
上面介绍了3种常用的图像处理python包，以后的教程里面，我们也主要采用这几个包来进行图像操作和图像算法的学习。下面是一些别的工具包：
### (4). IPython
一个比Python默认的解释环境强大很多倍的交互式解释器，在里面可以执行本地命令，Python命令和IPython自己定义的magic命令，有代码补全等功能。界面如下：

![IPython界面](assets/01/ipython_interface.jpg)
安装方式：
```bash
pip install ipython
```
### (5). Numpy
上文已经介绍过，官方网站是<http://www.numpy.org/>，安装方式：
```bash
pip install numpy
```
### (6). tensorflow
一个基于图的开源深度学习框架，由谷歌公司开源，后面我们打算写一些深度学习的图像处理教程，所以把Tensorflow也列出来了。官方网站：<https://www.tensorflow.org/>，安装方式：
```bash
pip install tensorflow
```
### (7). keras
一个tensorflow的前端框架，可以使用简单的接口来调用Tensorflow来完成深度学习任务，上手难度低，对开发者比较友好，网站：<https://keras.io/>, 安装方式：
```bash
pip install keras
```
## 5. Python的IDE（集成开发环境）
Python的IDE推荐PyCharm和Spyder，其中PyCharm是要收费的，但是有免费的学生版本[PyCharm Edu](https://www.jetbrains.com/pycharm-edu/)。Spyder的安装可以在[这里](https://github.com/spyder-ide/spyder)找到。  
另外如果你熟悉Sublime的话，安装好Python环境之后，可以使用`Ctrl-B`快捷键来调试和运行Python代码，下面是个简单的例子： 

![用Sublime Text 3来调试和运行Python](assets/01/sublime_python.jpg)
