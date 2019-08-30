1. 安装wget, git
> yum install -y wget git
2. 设置yum源
>```
> wget -O /etc/yum.repos.d/CentOS-Base.repo http://mirrors.aliyun.com/repo/Centos-7.repo
> yum clean all
> yum makecache
> yum install -y epel-release
> yum clean all
> yum makecache

3. 安装setuptools
>```
> cd setuptools-41.0.1
> chmod 777 setup.py
> python setup.py install

4. 安装pip
> easy_install pip
> (卸载pip方法：python -m pip uninstall pip)

5. 安装pyhpecw7
>```
> 下载pyhpecw7： git clone https://github.com/HPENetworking/pyhpecw7.git
> Best match: paramiko 2.6.0
> Processing paramiko-2.6.0-py2.py3-none-any.whl
> 
> Best match: ipaddr 2.2.0
> Processing ipaddr-2.2.0.tar.gz
> 
> Best match: scp 0.13.2
> Processing scp-0.13.2-py2.py3-none-any.whl
> 
> Best match: ncclient 0.6.6
> Processing ncclient-0.6.6.tar.gz
> 
> Best match: lxml 4.2.3
> Processing lxml-4.2.3-cp27-cp27mu-manylinux1_x86_64.whl
> 
> Best match: gtextfsm 0.2.1
> Processing gtextfsm-0.2.1.tar.gz
> 
> Best match: PyNaCl 1.3.0
> Processing PyNaCl-1.3.0-cp27-cp27mu-manylinux1_x86_64.whl
> 
> Best match: cryptography 2.7
> Processing cryptography-2.7-cp27-cp27mu-manylinux1_x86_64.whl
> 
> Best match: bcrypt 3.1.7
> Processing bcrypt-3.1.7-cp27-cp27mu-manylinux1_x86_64.whl
> 
> Best match: selectors2 2.0.1
> Processing selectors2-2.0.1-py2.py3-none-any.whl
> 
> Best match: six 1.12.0
> Processing six-1.12.0-py2.py3-none-any.whl
> 
> Best match: cffi 1.12.3
> Processing cffi-1.12.3-cp27-cp27mu-manylinux1_x86_64.whl
> 
> Best match: ipaddress 1.0.22
> Processing ipaddress-1.0.22-py2.py3-none-any.whl
> 
> Best match: enum34 1.1.6
> Processing enum34-1.1.6-py2-none-any.whl
> 
> Best match: asn1crypto 0.24.0
> Processing asn1crypto-0.24.0-py2.py3-none-any.whl
> 
> Best match: pycparser 2.19
> Processing pycparser-2.19.tar.gz
> 
> Best match: setuptools 41.2.0
> Adding setuptools 41.2.0 to easy-install.pth file




3. 安装Python依赖包
>```
>[root@Ansible ~]# [root@netc2c ~]# yum -y install gcczlib-devel bzip2-devel \
> >  openssl-devel ncurses-devel sqlite-devel \
> >  readline-develtk-devel gdbm-devel db4-devel libpcap-devel \
> >  xz-devel libffi-devel glibc-develrpm-build openssl-devel
>```

2. 安装pip
>```
> [root@Ansible ~]#curl https://bootstrap.pypa.io/get-pip.py -o get-pip.py
> [root@Ansible ~]#python get-pip.py
> [root@Ansible ~]#pip install --upgrade pip
> [root@Ansible ~]#pip -V
> pip 19.2.2 from /ansibleTest/lib/python2.7/site-packages/pip (python 2.7)
**注意** 使用哪个版本安装pip，就会关联到那个版本的pip。如使用Python3安装，就会安装pip3。


3. 安装ansible
>```
>yum install –y ansible
验证
>```
> [root@Ansible ~]# ansible –version
> 
> ansible 2.8.2
> 
>   config file = /etc/ansible/ansible.cfg
> 
>   configured module search path =[u'/root/.ansible/plugins/modules', u'/usr/share/ansible/plugins/modules']
> 
>   ansible python module location =/usr/lib/python2.7/site-packages/ansible
> 
>   executable location = /usr/local/bin/ansible
> 
>   python version = 2.7.5 (default, Jun 20 2019,20:27:34) [GCC 4.8.5 20150623 (Red Hat 4.8.5-36)]
> 
 

4. 安装独立的Python虚拟化环境

Virtualenv是在工作目录中虚拟完整的Python环境来实现多Python多环境并存。
>```
> [root@Ansible~]# pip install virtualenv
> 
> Collectingvirtualenv
> 
>   Downloadinghttps://files.pythonhosted.org/packages/db/9e/df208b2baad146fe3fbe750eacadd6e49bcf2f2c3c1117b7192a7b28aec4/virtualenv-16.7.2-py2.py3-none-any.whl(3.3MB)
> 
>      |████████████████████████████████| 3.3MB 65kB/s
> 
> Installingcollected packages: virtualenv
> 
> Successfully installed virtualenv-16.7.2

 

5. 创建虚拟化将目录
>```
> virtualenv /testPython3/ansible
> 
> source /testPython3/ansible/bin/activate
> 
> (ansible) [root@Ansible ~]#
 

6. Ansible主要目录及文件
>```
> 配置文件：/etc/ansible/ansible.cfg，包含inventory主机信息配置、ansible工具功能配置
> 
> 执行文件目录：/usr/bin/，ansible所有的可执行命令所在的目录。
> 
> 内置的lib库文件：/usr/lib/python2.7/site-packages/
> 
> Man文档目录：/usr/share/man/man1