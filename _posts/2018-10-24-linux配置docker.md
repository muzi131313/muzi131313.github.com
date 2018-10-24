## 配置zsh
- [linux设置on-my-zsh](https://blog.csdn.net/gatieme/article/details/52741221)
    ````
    sh -c "$(curl -fsSL https://raw.githubusercontent.com/robbyrussell/oh-my-zsh/master/tools/install.sh)"
    ````

## 安装docker
- [linux下安装docker](https://www.linuxidc.com/Linux/2018-08/153632.htm)
    ````
    # 安装依赖包
    yum install -y yum-utils device-mapper-persistent-data lvm2
    # 添加Docker软件包源
    yum-config-manager --add-repo https://download.docker.com/linux/centos/docker-ce.repo
    # 安装Docker CE
    yum install docker-ce -y
    # 启动
    systemctl start docker
    # 开机启动
    systemctl enable docker
    # 查看Docker信息
    docker info
    ````
