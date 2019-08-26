### hosts文件
>```
> localhost ansible_connection=local  
> [ansibleTest] #设置组ansibleTest，与playbook中hosts内容一致  
> ansibleTest01 ansible_host=104.255.237.105 #主机信息，适用于单独对主机进行操作
> [ansibleTest:vars] #设置组变量  
> ansible_ssh_user=root   
> ansible_ssh_pass=default 
>```
>>#ansibleTest01：指被操作主机的别名  
#行为参数：  
#ansible_host：指目标主机IP  
#ansible_port：指目标主机端口  
#也可以使用<ip地址>:<端口号>来替代ansible_host和ansible_port，但不建议  
#ansible_ssh_user=root：登录用户名  
#ansible_ssh_pass=default：登录用户密码  
- - -
### 隔离主机和组变量
在当前目录下创建group_vars目录和hosts_vars目录，可以把组变量和主机变量分别保存。  
这两个变量目录下的变量文件使用yaml格式编写。  
**hosts文件内容：**
>```
> localhost ansible_connection=local  
> [ansibleTest] #设置组ansibleTest，与playbook中hosts内容一致  
> ansibleTest01 ansible_host=104.255.237.105 #主机信息，适用于单独对主机进行操作

**group_vars/ansibleTest.yml，以字典格式编写**
>```
> ---
> ansible_ssh_user: root
> ansible_ssh_pass: default

* * *
## 动态hosts
### 一个动态hosts脚本必须支持两个命令行参数
**--host=<hostname>：列出主机的详细信息**  
**--list： 列出群组**

##### 主机详细信息展示
Ansible会安装如下形式调用hosts脚本来获取单台主机的详细信息；
> ```
> $./dynamic.py --host=<hostname>
>```
输出包含所有主机特定的变量、行为参数。为JSON格式。

##### 列出群组
动态hosts脚本需要列出素有的群组以及每台主机的详细信息。
>```
> $./dynamic.py --list
>```
输出所有群组以及每台主机的详细信息。为JSON格式。JSON对象的名字为群组名，值为由主机的名字组成的数组。

### 编写动态hosts脚本
思路： 收集目前运行的主机的信息  
1.对于服务器，通过VC/KVM收集  
2.对于网络设备  
   - 通过探测网络设备的管理接口。---设备厂商、型号分类
   - 通过网管系统收集。

