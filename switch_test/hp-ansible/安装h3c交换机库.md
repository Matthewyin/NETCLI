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

3. 安装ansible
>```
> yum install –y ansible
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
 

4. 安装setuptools
>```
> cd setuptools-41.0.1
> chmod 777 setup.py
> python setup.py install

5. 安装pip
> 方法1：python get-pip.py
> 方法2：easy_install pip
> (卸载pip方法：python -m pip uninstall pip)

6. 安装pyhpecw7(***含运行pyhpecw7所需的python库***）
>```
> easy_install pyhpecw7
> 
> ansible                      2.8.4  
> Babel                        0.9.6  
> backports.ssl-match-hostname 3.5.0.1
> cffi                         1.6.0  
> chardet                      2.2.1  
> configobj                    4.7.2  
> cryptography                 1.7.2  
> decorator                    3.4.0  
> enum34                       1.0.4  
> gtextfsm                     0.2.1  
> httplib2                     0.9.2  
> idna                         2.4    
> iniparse                     0.4    
> ipaddr                       2.2.0  
> ipaddress                    1.0.16 
> Jinja2                       2.7.2  
> jmespath                     0.9.0  
> kitchen                      1.1.1  
> langtable                    0.0.31 
> lxml                         4.4.1  
> MarkupSafe                   0.11   
> ncclient                     0.6.6  
> paramiko                     2.1.1  
> perf                         0.1    
> pip                          18.0   
> ply                          3.4    
> pyasn1                       0.1.9  
> pycparser                    2.14   
> pycurl                       7.19.0 
> pygobject                    3.22.0 
> pygpgme                      0.3    
> pyhpecw7                     0.0.11 
> pyliblzma                    0.5.3  
> python-augeas                0.5.0  
> python-dmidecode             3.10.13
> python-linux-procfs          0.4.9  
> pyudev                       0.15   
> pyxattr                      0.5.1  
> PyYAML                       3.10   
> schedutils                   0.4    
> scp                          0.13.2 
> selectors2                   2.0.1  
> setuptools                   41.0.1 
> six                          1.9.0  
> slip                         0.4.0  
> slip.dbus                    0.4.0  
> urlgrabber                   3.10   
> yum-langpacks                0.4.2  
> yum-metadata-parser          1.1.4

7. 安装独立的Python虚拟化环境(可选)

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

 

8. 创建虚拟化将目录（可选）
>```
> virtualenv /testPython3/ansible
> 
> source /testPython3/ansible/bin/activate
> 
> (ansible) [root@Ansible ~]#
 

9. Ansible主要目录及文件
>```
> 配置文件：/etc/ansible/ansible.cfg，包含inventory主机信息配置、ansible工具功能配置
> 
> 执行文件目录：/usr/bin/，ansible所有的可执行命令所在的目录。
> 
> 内置的lib库文件：/usr/lib/python2.7/site-packages/
> 
> Man文档目录：/usr/share/man/man1

