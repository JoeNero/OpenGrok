# OpenGrok
克隆仓库
```
https://github.com/JoeNero/OpenGrok.git
```
```
vim ~/.bashrc
```
添加如下内容
```
#tomcat 
export CATALINA_HOME="/home/xtt/OpenGrok/apache-tomcat-8.5.55"

#opengrok
export OPENGROK_TOMCAT_BASE=$CATALINA_HOME
```
保存后
```
source ~/.bashrc
```
打开本地端口8080测试
```
http://localhost:8080
```
部署opengrok
进入opengrok bin目录
```
./OpenGrok deploy
```
测试部署是否成功
```
http://localhost:8080/source
```
建立索引
```
./OpenGrok index /root/chrome  #代码存放的位置
```
最终生成的索引默认会存放在
```
/var/opengrok
```
