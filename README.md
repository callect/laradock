# LaraDock


![](https://s31.postimg.org/nbettdki3/lara_dock_poster_new.jpg)



此版本laradock是基于[原作者](https://github.com/LaraDock/laradock)的代码，修改后以适用中国境内。

### 环境要求

> windows10专业版、旗舰版、教育版等支持Microsoft Hyper-V的版本，并更新到10586以上

### 配置加速器

> [docker官网](https://www.docker.com/products/docker#/windows)下载最新的docker安装程序，并安装完成。
>
> [daocloud](https://www.daocloud.io/)注册并登录，在控制台导航上点击进入加速器页面，点击windows标签，并按提示操作

### 配置共享卷
在桌面右下角状态栏中右键 docker 图标 Setting > Shared Drivers，选中你想要存放volumes和laradock的硬盘盘符，点击右下角apply

> 注意如果你的windows没有为administrator配置密码需要先行配置（或许其它用户也可以，但我没有试过，如果你当前不是administrator用户，可以试一下）

### 安装容器

> 拉取laradock库：

```powershell
git clone https://github.com/callect/laradock.git
```

> 进入到laradock文件夹内，运行容器

```powershell
docker-compose up -d  nginx mysql
```

> 进入容器，Do what you want

```powershell
docker exec -it --user=laradock laradock_workspace_1 bash
```

至此，laradock容器已经激活运行了

注：nginx站点配置laravel.conf中站点根路径请自行修改

其它laradock配置见[原文档](https://github.com/LaraDock/laradock/blob/master/README.md)