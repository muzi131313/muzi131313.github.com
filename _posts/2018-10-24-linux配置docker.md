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

    # 配置加速器 ===== start ======
    curl -sSL https://get.daocloud.io/daotools/set_mirror.sh | sh -s http://bc437cce.m.daocloud.io docker version >= 1.12
    # 重启docker
    systemctl restart docker
    # 关闭docker
    systemctl stop docker
    # 查看docker服务
    ps -ef|grep docker
    # 启动docker
    systemctl  start docker
    # 查看docker服务是否启动
    ps -ef|grep docker
    ````
- [docker started](https://docs.docker.com/v17.09/get-started/)

## [安装compose](https://docs.docker.com/compose/install/)

- [compose版本号查看地址](https://github.com/docker/compose/releases)

````
# 下载安装
sudo curl -L "https://github.com/docker/compose/releases/download/1.23.1/docker-compose-$(uname -s)-$(uname -m)" -o /usr/local/bin/docker-compose
# 赋权限
sudo chmod +x /usr/local/bin/docker-compose
# 查看版本号
docker-compose --version
````
- [docker compose started](https://docs.docker.com/compose/gettingstarted/)

### 参考来源:
- [Linux下Docker配置](https://www.linuxidc.com/Linux/2018-08/153632.htm)
- [docker入门](http://www.ruanyifeng.com/blog/2018/02/docker-tutorial.html)
- [docker微服务教程](http://www.ruanyifeng.com/blog/2018/02/docker-wordpress-tutorial.html)
- [systemd常用教程](http://www.ruanyifeng.com/blog/2016/03/systemd-tutorial-commands.html)
- [docker教程](https://yeasy.gitbooks.io/)
