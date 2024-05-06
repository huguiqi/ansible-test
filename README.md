# ansible-test
ansible学习日志

## 安装

### homebrew

> brew install ansible


### pip安装

> pip install ansible


**我的pip命令是对应的pip3的软链接**

**inventory.yaml:**

```
zaxh-dev:
  hosts:
    webserver01:
      ansible_host: 192.168.1.199
    webserver02:
      ansible_host: 192.168.0.86
  vars:
    ansible_user: root
```


playbook.yaml:

```
- name: My first play
  hosts: zaxh-dev
  tasks:
   - name: Ping my hosts
     ansible.builtin.ping:

   - name: Print message
     ansible.builtin.debug:
      msg: Hello world

```

## ansible常用命令

### 指定group执行目标主体命令行

> ansible zaxh-dev -i inventory.yaml -m command -a "date"


查看docker状态

> ansible -i inventory.yaml zaxh-dev -m shell -a 'systemctl status docker'

ping

> ansible -i inventory.yaml zaxh-dev -m ping



### 查看某软件是否安装


```shell
ansible -i inventory.yaml dev1 -a 'apt list | grep mysql*'
```



## playbooks

### 运行剧本配置

> ansible-playbook -i inventory.yaml dev-playbook.yaml





参考学习：[https://juejin.cn/post/7091471589308366855](https://juejin.cn/post/7091471589308366855)


