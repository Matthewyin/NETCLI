1.  安装Python3.7（在根目录下）
>```
> [root@host]#yum install -y zlib-devel bzip2-devel openssl-devel ncurses-devel sqlite-devel readline-devel tk-devel gcc make libffi-devel wget vim gcc-c++ mysql-devel python-devel
> [root@host]#wget https://www.python.org/ftp/python/3.7.0/Python-3.7.0.tgz
> 
> [root@host]#tar -zxvf Python-3.7.0.tgz
> 
> cd Python-3.7.0
> 
> [root@host]#./configure --prefix=/usr/local/python3
> 
> [root@host]#make && make install
> [root@ansible Python-3.7.0]# mv /usr/bin/python /usr/bin/python.bak
> [root@ansible Python-3.7.0]# ln -s /usr/local/python3/bin/python3.7 /usr/bin/python
> [root@host]#curl https://bootstrap.pypa.io/get-pip.py -o get-pip.py
> [root@host]#python get-pip.py
> [root@ansible Python-3.7.0]# mv /usr/bin/pip /usr/bin/pip.bak
> [root@ansible Python-3.7.0]# ln -s /usr/local/python3/bin/pip3.7 /usr/bin/pip

2. 安装pip
>```
> curl https://bootstrap.pypa.io/get-pip.py -o get-pip.py
> python get-pip.py
**注意:** 使用哪个版本安装pip，就会关联到那个版本的pip。如使用Python3安装，就会安装pip3。  
**验证:**
>```
> [root@ansible Python-3.7.0]# pip -V
> pip 19.2.3 from /usr/local/python3/lib/python3.7/site-packages/pip (python 3.7)
> [root@ansible Python-3.7.0]# python -V
> Python 3.7.0

**配置yum**

安装完Python3.7后，yum不能使用，主要是因为yum是依赖python2.7的，你把python改成了3.7了，自然不好使了。只要修改一下yum里的相关依赖即可。
> vim /usr/libexec/urlgrabber-ext-down

打开以后，找到一个/usr/bin/python的，后面加上2.7就可以了！也就是/usr/bin/python2.7
然后输入  
> vim /usr/bin/yum
也改成python2.7
