RPM 和 DEB 是 Linux 系统下常见的两种安装包格式，本文介绍如何使用 RPM 或 DEB 文件在一台机器上快速安装{{nebula.name}}。

!!! note

    部署{{nebula.name}}集群的方式参见[使用 RPM/DEB 包部署集群](https://docs.yueshu.com.cn/{{nebula.release}}/2.quick-start/3.quick-start-on-premise/3.1add-storage-hosts/)。<!--这里用外链。-->


## 前提条件

- 安装`wget`工具。

- 已[在 LM 中加载 License Key](https://docs.yueshu.com.cn/{{nebula.release}}/9.about-license/2.license-management-suite/3.license-manager/)。


## 下载安装包




[联系我们](https://yueshu.com.cn/contact)获取{{nebula.name}}安装包。



!!! note

    - 当前仅支持在 Linux 系统下安装{{nebula.name}}，且仅支持 CentOS 7.x、CentOS 8.x、Ubuntu 16.04、Ubuntu 18.04、Ubuntu 20.04 操作系统。
  
    - 如果用户使用的是国产化的 Linux 操作系统，请[安装{{nebula.name}}](https://yueshu.com.cn/contact)。  




## 安装{{nebula.name}}

- 安装 RPM 包

  ```bash
  $ sudo rpm -ivh --prefix=<installation_path> <package_name>
  ```
  
  `--prefix`为可选项，用于指定安装路径。如不设置，系统会将{{nebula.name}}安装到默认路径`/usr/local/nebula/`。

  例如，要在默认路径下安装{{nebula.release}}版本的 RPM 包，运行如下命令：

  

  
  ```bash
  sudo rpm -ivh yueshu-graph-{{nebula.release}}.el7.x86_64.rpm
  ```  
  

- 安装 DEB 包

  ```bash
  $ sudo dpkg -i <package_name>
  ```

  !!! note
        使用 DEB 包安装{{nebula.name}}时不支持自定义安装路径。默认安装路径为`/usr/local/nebula/`。

  例如安装{{nebula.release}}版本的 DEB 包：

  

  
  ```bash
  sudo dpkg -i yueshu-graph-{{nebula.release}}.ubuntu1804.amd64.deb
  ```
  



## 配置 License 管理工具（LM）地址

1. 在{{nebula.name}}的 Meta 服务配置文件（`nebula-metad.conf`）中，设置`license_manager_url`的值为许可证管理工具所在的主机 IP 和端口号`9119`，例如`192.168.8.100:9119`。
2. 将 Meta、Storage 和 Graph 服务的配置文件（`nebula-metad.conf`、`nebula-graphd.conf`、`nebula-storaged.conf`）中的所有`local_ip`（默认`127.0.0.1`）替换为各服务所在主机的真实 IP，以及将`meta_server_addrs`地址替换为 Meta 服务所在主机 IP 地址和端口号`9559`。



## 后续操作

- [启动{{nebula.name}}](https://docs.yueshu.com.cn/{{nebula.release}}/2.quick-start/3.quick-start-on-premise/5.start-stop-service/)<!--这里用外链。-->
- [连接{{nebula.name}}](https://docs.yueshu.com.cn/{{nebula.release}}/2.quick-start/3.quick-start-on-premise/3.connect-to-nebula-graph/)<!--这里用外链。-->
