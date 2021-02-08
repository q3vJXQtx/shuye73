# Docker2 V3 gitee库使用教程

## 阅读须知
1. 此教程虽然本着0基础搭建的宗旨，但是如果你没有一定的学习能力，或者不想去掌握一些常用的docker基础命令，再或者你甚至懒得打开某度去了解什么是docker，那么我建议你关掉教程页面转为github action
2. 在阅读此教程之前请确保你有相应的设备支持
3. 此教程所提供的方案源码为@EvineDeng编写而成能够做到每天自动运行，自动更新

## 教程主体
1. 安装docker (已经安装的跳至第二步)

	sudo yum check-update
	curl -fsSL https://get.docker.com/ | sh
	sudo systemctl start docker
	sudo systemctl status docker
	sudo systemctl enable docker 

2. 既然是0基础那么你肯定是第一次安装docker，所以这一步你并不需要清除原有的容器，如果你有洁癖可以重装你的设备

### 3.