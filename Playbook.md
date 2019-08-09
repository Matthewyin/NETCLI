# YAML语法
##### 文件起始
        三个减号标记文档的开始  ---

##### 注释：
        “#”号，单行注释
          示例：
            #This is a YAML comment
##### 字符串：
        通常不需要使用引号，
          例外：使用
            {{ string }}
            用法用于变量替代
##### 布尔型：
        Ansible playbook中使用True和False
##### 列表：
        即序列。使用减号“-”作为界定符
          示例：
            -list01
            -list02
            -list03
##### 字典：
        类似于json中的对象、Python中的字典。
          示例：
            address:railway station
            city:NanJing
            state:JiangSu
##### 分行：
        将长的参数区段拆分成多行，同时，ansible视其为单行字符串。
        YAML使用大于号“>”来标记分行。
        运行时，YAML解释器会把换行符替换为空格。
     


# Playbook语法
* playbook包含一个或多个play组成
* 一个play由一组无序主机（host）和一系列有序的task组成
* 每一个task仅由一个模块组成

#### 必选项
* hosts：需要配置的主机
* tasks：需要在这组主机上执行的任务

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
  示例：  
  > ```yuml
  > vars:  
  >   key_file: /etc/nginx/ssl/nginx.key  
  >  
  > - name: copy TLS key  
  >    copy:  
  >      src: file/nginx.key  
  >      dest={{key_file}}  
  >    notify: restart nginx
  >
  > handler  
  > - name: restart nginx    
  >    service: 
  >      name: nginx  
  >      state: restart  
  >```
  

    
