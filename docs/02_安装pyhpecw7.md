1. 创建虚拟化环境： *virtualenv /xxx*
2. 进入虚拟化环境： *source /xxx"
3. 安装xlwt、gtextfsm、ncclient: *pip install xlwt gtextfsm ncclient*  
4. 下载pyhpecw7： *git clone https://github.com/HPENetworking/pyhpecw7.git*
5. 进入pyhpecw7： *cd pyhpecw7*
6. 安装pyhpecw7： *python setup.py install*
* * * 
### 遗留问题
fatal: [leaf01]: FAILED! => {"changed": false, "error": "No module named pyhpecw7.features.vlan", "msg": "There was a problem loading from the pyhpecw7 module."}
