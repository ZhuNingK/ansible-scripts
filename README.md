## 脚本简介
当前版本涉及centOS7、openEuler-22.03 LTS、Kylin Linux Advanced Server V10 (Lance)以下内容：
- ttd上所有服务器初始化操作
- openssl编译安装
- openssh编译安装
- cmake编译安装
- mysql57安装
- lua环境安装（ttd中涉及内容）
- lua-nginx安装（ttd中涉及内容）
- nginx（不引入lua）

ansible中roles执行顺序：
baseEnv > openssl(迄今为止c7需要安装) > openssh > cmake > mysql ; lua>lua_nginx ; nginx

** 注意 **
```yaml
- hosts: test
  remote_user: root
  gather_facts: yes
  vars:
    - pkgs_path: "/root/asb_pkgs"
  roles:
    #- baseEnv
    #- { role: openSSL, when: ansible_distribution == "CentOS" }
    #- openSSH
    #- cmake
    #- mysql
    #- lua
    #- lua_nginx
    - nginx
```
> `pkgs_path` 为安装存放路径，所以安装包均需要提前下载，且命名固定

## 所需软件包
- baseEnv
- openssl
    - openssl-1.1.1t.tar.gz
- openssh
    - openssh-9.3p1.tar.gz
- cmake
    - cmake-3.27.0.tar.gz
- lua
    - luajit-2.1.tar.gz
    - lua-nginx-module-0.10.24.tar.gz
    - lua-resty-core-0.1.26.tar.gz
    - lua-resty-lrucache-0.13.tar.gz
    - ngx_devel_kit-0.3.2.tar.gz
- lua-nginx
    - nginx-1.24.0.tar.gz
- nginx
    - nginx-1.24.0.tar.gz

> 注意： 以上的安装包均为ttd中对应安装文档中的安装包
