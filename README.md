# laradock
基于LaraDock/laradock LaraDock-ToolBox分支，手动补丁至4.05+多虚拟站点支持

##### 特点

- 安装了加速器，加快镜像拉取速度
- 使用国内镜像安装node
- 其它见原项目https://github.com/LaraDock/laradock#features

> 1. 操作之前需要在windows里新建个目录用于存放laradock配置及源码文件 如E:\docker，以下称为docker目录,写做docker/
> 2. 前往www.daocloud.io注册帐号，在用户中心菜单第一项找到加速器，点击进入，复制下专属加速地址

##### 第一步

> 1. 建立docker主机，建议主机名为default
> 2. 在建立好的虚拟主机上右键设置 > 共享文件夹 > 添加共享文件夹
> 3. 共享文件夹路径选择docker目录，共享文件夹名称：docker
> 4. 选中固定分配（如果有此项），不选中自动挂载

##### 第二步

> 在GIT终端中（任何支持tty的终端，如docker quickstart,mintty等）进入docker目录

```
git clone https://github.com/callect/laradock.git
cd laradock
```

##### 第三步

> SSH方式进入docker主机，为docker安装daocloud加速器

```
docker-machine ssh default
sudo sed -i "s|EXTRA_ARGS='|EXTRA_ARGS='--registry-mirror=加速地址 |g" /var/lib/boot2docker/profile
exit
docker-machine restart default
```

##### 第四步

> 1. 根据执行结果提示执行`docker-machine env` 等命令。
> 2. 确认当前目录为之前进入的docker/laradock中，建立并激活容器

```
docker-compose up -d nginx mysql
```

##### 第五步

> 将docker目录挂载于容器

```
docker-machine ssh default
sudo mount -t vboxsf docker /www
```

##### 第六步

> 安装laravel

```
docker exec -it laradock_workspace_1 bash
composer create-project laravel/laravel bms "5.3.*"
```

##### 第七步

> 重建容器

```
docker-compose down
docker-compose up -d nginx mysql
```

##### 第八步

> 在浏览器输入docker主机的IP

**Bingo!**