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