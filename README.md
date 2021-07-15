# OpenGrok 
搭建openGrok需要3个工具一个环境:
工具：
1.tomcat作为容器
2.openGrok搭建索引的主要工具
3.ctags创建tag工具
环境:
jave jdk环境


用以下的命令克隆仓库，这个仓库里面已经有了tomcat和openGrok.
```
git clone https://github.com/JoeNero/OpenGrok.git
```
ctags用ctags --version命令检查是否下载了.
ctags有两个版本.我用过觉得都没啥太大差别。
所以这边推荐直接命令安装,这边会自己选中对应的ctags,敲命令就完事了.
```
sudo apt install ctags
```
装完ctags再用ctags--version检查下下载的版本吧.

下载完成,打开.bashrc环境配置文件
```
vim ~/.bashrc
```
添加如下内容,路劲为你文件下载的对应路劲
```
#tomcat 
export CATALINA_HOME="/home/xtt/OpenGrok/apache-tomcat-8.5.55"

#opengrok
export OPENGROK_TOMCAT_BASE=$CATALINA_HOME
```
保存后，source一下.
```
source ~/.bashrc
```
终端进入到apache-tomcat-8.5.55/bin路径下
首先要对catalina.sh 执行可运行的操作
```
chmod +x catalina.sh
```
当然你也可以偷懒
```
chmod +x *
```
添加可执行权限后.运行打开脚本
```
sudo sh startup.sh
```
打开本地浏览器,在 搜索栏 输入端口8080测试（就是把下面的内容复制到搜索框上）
```
http://localhost:8080
```
部署opengrok
进入opengrok bin目录
```
./OpenGrok deploy
```
测试部署是否成功,部署不成功也无所谓啦.肯定是没装好ctags.往下走，这一部分不影响.
```
http://localhost:8080/source
```
建立索引
```
sudo ./OpenGrok index /root/chrome  #代码存放的位置:ps,项目的代码都很大.像.repo 还有out文件这些，你不用建立对应的索引,没有用的.挪出去.建完再挪回来
```
然后喝口水放着，索引会建立一阵子，一般几个小时到一个下午时间，看项目代码大小，所以我建议先挪用不到的.
最终生成的索引默认会存放在
```
/var/opengrok
```

# 常见的操作
```
sudo sh startup.sh #开启本地端口
sudo sh shutdown.sh #关闭本地端口
```
