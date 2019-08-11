# YAML语法
* 文件起始:三个减号标记文档的开始  ---

* 注释：“#”号，单行注释  
  > 示例：#This is a YAML comment
* 字符串：通常不需要使用引号，  
        *例外：使用 {{ string }} 用法用于变量替代*
* 布尔型：Ansible playbook中使用True和False
* 列表：即序列。使用减号“-”作为界定符  
  > 示例：
  >```  
  > -list01  
  > -list02  
  > -list03
* 字典：类似于json中的对象、Python中的字典。  
  > 示例：
  >```
  > address:railway station  
  > city:NanJing  
  > state:JiangSu
* 分行：YAML使用大于号“>”来标记分行。  
       将长的参数区段拆分成多行，同时，ansible视其为单行字符串。  
       运行时，YAML解释器会把换行符替换为空格。
     


# Playbook语法
* playbook包含一个或多个play组成
* 一个play由一组无序主机（host）和一系列有序的task组成
* 每一个task仅由一个模块组成

#### 必选项
* **hosts**：需要配置的主机
* **tasks**：需要在这组主机上执行的任务

#### 可选项
* name：描述play的注释
* become：如果为True，ansible会在运行每个任务的时候都切换为root用户
* vars：变量
    
#### 模块
* 由Ansible包装，在主机上运行的一系列操作的脚本
* 查看ansible模块文档，使用ansible-doc __<模块名>__查看。

#### 配置模板
* 使用jinja2模板引擎，使用模板功能来定义配置文件，以避免将经常变化的配置写死在文件里
* ansible中主要使用jinja2的过滤器特性

#### handler
* Ansible提供的条件控制机制之一，类似于tasks，但只用于tasks通知后来执行。
* 如果Ansible识别到tasks改变了系统状态，task会触发通知机制。
  >示例：  
  > ```yuml
  > vars:  
  >   key_file: /etc/nginx/ssl/nginx.key  
  > tasks:
  > - name: copy TLS key  
  >    copy:  
  >      src: file/nginx.key  
  >      dest={{key_file}}  
  >    notify: restart nginx
  >
  > handler:
  > - name: restart nginx    
  >    service: 
  >      name: nginx  
  >      state: restart  
  >```

#### 变量
1. 在playbook中添加var区段。使用 ***key:value*** 定义，在tasks区段使用 ***{{key}}*** 调用。
 > 示例：
 >```
 > vars:  
  >  key_file: /etc/nginx/ssl/nginx.key  
  >tasks:
  > - name: copy TLS key  
  >    copy:  
  >      src: file/nginx.key  
  >      dest={{key_file}}  
  >    notify: restart nginx
  >```
2. 使用var_files区段。将变量保存在一个 ***xxx.yml*** 文件中，通过var_files区段调用。此方法可以用来隔离敏感信息的变量。  
   如上例，将vars部分内容保存在keyFile.yml文件中。
> 示例：
 >```
 > var_filess:  
  >  keyFile.yml  
  >tasks:
  > - name: copy TLS key  
  >    copy:  
  >      src: file/nginx.key  
  >      dest={{key_file}}  
  >    notify: restart nginx
  >```
  > keyFile.yml文件内容如下：
  >```  
  >  key_file: /etc/nginx/ssl/nginx.key  
  
##### 注册变量
有时需要基于tasks执行的结果来设置变量的值。在调用模块时使用 ***register*** 来创建registered变量。
> 示例：
>```
> [root@Ansible ansible_test]# cat registerTest.yml 
>  - name: Register Test
>   hosts: ansibleTest
>   become: True
>   tasks:
>    - name: 显示hostname
>      command: cat /etc/hostname
>      register: hostname
>    - debug: var=hostname
> [root@Ansible ansible_test]# 
>```
> 输出：
>```
> [root@Ansible ansible_test]# ansible-playbook registerTest.yml 
> PLAY [Register Test] *********************************************************************************************************************************
>
> TASK [Gathering Facts] *******************************************************************************************************************************
> ok: [ansibleTest01]
>
> TASK [显示hostname] ************************************************************************************************************************************
> changed: [ansibleTest01]
>
> TASK [debug] *****************************************************************************************************************************************
> ok: [ansibleTest01] => {
>     "hostname": {
>         "changed": true, 
>         "cmd": [
>             "cat", 
>             "/etc/hostname"
>         ], 
>         "delta": "0:00:00.006889", 
>         "end": "2019-08-11 21:29:00.905789", 
>         "failed": false, 
>         "rc": 0, 
>         "start": "2019-08-11 21:29:00.898900", 
>         "stderr": "", 
>         "stderr_lines": [], 
>         "stdout": "Ansible_test", 
>         "stdout_lines": [
>             "Ansible_test"
>         ]
>     }
> }
> 
> PLAY RECAP *******************************************************************************************************************************************
> ansibleTest01              : ok=3    changed=1    unreachable=0    failed=0    skipped=0    rescued=0    ignored=0   

