1.  安装Python3.7（在根目录下）
>```
> [root@host]#wgethttps://www.python.org/ftp/python/3.7.0/Python-3.7.0.tgz
> 
> [root@host]#tar -zxvfPython-3.7.0.tgz
> 
> cd Python-3.7.0
> 
> [root@host]#./configure--prefix=/usr/local/python3
> 
> [root@host]#make && makeinstall
> 
> [root@host]#ln -s/usr/local/python3/bin/python3.7 /usr/bin/python3
> 
> [root@host]#ln -s/usr/local/python3/bin/pip3.7 /usr/bin/pip3

测试
>```
> [root@host]#python3
> 
> Python 3.7.0(default, Jul 28 2018, 22:47:29)
> 
> [GCC 4.8.5 20150623(Red Hat 4.8.5-28)] on linux
> 
> Type "help","copyright", "credits" or "license" for moreinformation.
> 
> >>>print("hello world!")
> 
> hello world!
> 
> >>>exit()、

[root@host]#pip3 --version

pip 10.0.1 from/usr/local/python3/lib/python3.7/site-packages/pip (python 3.7)


2. 安装pip
curl https://bootstrap.pypa.io/get-pip.py -o get-pip.py
python get-pip.py
**注意** 使用哪个版本安装pip，就会关联到那个版本的pip。如使用Python3安装，就会安装pip3。

