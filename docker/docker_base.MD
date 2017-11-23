#创建容器：
 docker create  ／docker run  
区别：第一个创建的容器是停止的
          第二个创建的容器是启动的
         
使用docker run可以创建两种类型的容器：
交互型容器：运行在前台，通常会制定有交互的控制台
后台型容器：运行在后台，创建启动之后与终端无关。

## 启动容器

为了让容器自动重启，需要用到—restart参数。—restart标志会检查容器的退出码，并决定是否需要重启容器。

sudo docker run —restart=always —name= docker_restart -d ubuntu /bin/sh -c “while true; do echo hello world; sleep 1; done “

## 容器内执行命令

docker exec  可在容器中运行新的任务。它可以创建2中任务：后台型任务和交互型任务

-d标志要运行一个后台型任务
docker exec -d ubuntu touch /etc/new_config_file

-t -t 交互型任务
docker exec -it ubuntu touch /bin/bash


## 容器的导入导出
首先创建一个容器：
sudo docker run -it —name=ubuntu ubuntu /bin/bash
然后修改容器，安装需要的软件，配置系统环境。完成后就可以保存到本地 使用docker export
docker export ubuntu > my_ubuntu.tar
ls
my_ubuntu.tar

反过来，我们可以使用docker import 导入一个本地的tar包作为镜像：

cat ubuntu.tar |sudo docker import - imported:container

docker import url res:tag
