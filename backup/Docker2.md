# Docker2 V3 gitee库使用教程

## 阅读须知
1. 此教程虽然本着0基础搭建的宗旨，但是如果你没有一定的学习能力，或者不想去掌握一些常用的docker基础命令，再或者你甚至懒得打开某度去了解什么是docker，那么我建议你关掉教程页面转为github action
2. 在阅读此教程之前请确保你有相应的设备支持
3. 此教程所提供的方案源码为@EvineDeng编写而成能够做到每天自动运行，自动更新

## 教程主体
1.安装docker (已经安装的跳至第2步)
	
	sudo yum check-update
	curl -fsSL https://get.docker.com/ | sh
	sudo systemctl start docker
	sudo systemctl status docker
	sudo systemctl enable docker 
注①：此处强烈建议顺便安装`Portainer`(一款可视化容器管理工具)如果你不清楚什么是`Portainer`，那么我建议你回看阅读须知第一条

2.既然是0基础那么你肯定是第一次安装docker，所以这一步你并不需要清除原有的容器，如果你有洁癖可以重装你的设备

3.创建容器

	docker run -dit \
	-v /你想存放的路径/jd/config:/jd/config `# 配置保存目录，冒号左边请修改为你想存放的路径`
	-v /你想存放的路径/jd/log:/jd/log `# 日志保存目录，冒号左边请修改为你想存放的路径` \
	-p 5678:5678 \
	--name jd \
	--hostname jd \
	--restart always \
	shuye72/jd-base:gitee

注②：如果是旁路由，建议用`--network host \`代替`-p 5678:5678 \`这一行，此时控制面板为`http://<ip>:5678`
4.多容器示例

	docker run -dit \
	-v /你想存放的路径/jd1/config:/jd/config `# 配置保存目录，冒号左边请修改为你想存放的路径`
	-v /你想存放的路径/jd1/log:/jd/log `# 日志保存目录，冒号左边请修改为你想存放的路径` \
	-p 5679:5678 \
	--name jd1 \
	--hostname jd1 \
	--restart always \
	shuye72/jd-base:gitee

注③：如果是旁路由，建议用`--network host \`代替`-p 5679:5678 \`这一行，此时控制面板为`http://<ip>:5679`

5.自动更新Docker容器
安装containrrr/watchtower可以自动更新容器

	docker run -d \
	--name watchtower \
	-v /var/run/docker.sock:/var/run/docker.sock \
	containrrr/watchtower \
	jd


### 注意：
1. 请在创建后使用`docker logs -f` jd查看创建日志，直到出现容器启动成功…字样才代表启动成功（不是以此结束的请更新镜像），按`Ctrl+C`退出查看日志。
![image](https://github.com/shuye73/MyActions/blob/main/backup/docker/success.png)