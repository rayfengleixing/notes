# 安装pycharm源码包

```shell
sudo tar xfz pycharm-community-2017.3.3.tar.gz -C /opt
```

bin 目录下有pycharm.sh, `./pycharm.sh`运行pycharm

运行会报错，因为没有安装jdk，`usr/lib`目录下，`mkdir java` 创建`java`目录

```
sudo tar zxf jdk-8u162-linux-x64.tar.gz -C /usr/lib/java/

sudo vim ~/.bashrc #加入一下内容

#set oracle jdk environment
unset _JAVA_OPTIONS
export JAVA_HOME=/usr/lib/java/jdk1.8.0_162
export JRE_HOME=${JAVA_HOME}/jre  
export CLASSPATH=.:${JAVA_HOME}/lib:${JRE_HOME}/lib  
export PATH=${JAVA_HOME}/bin:$PATH 

source ~/.bashrc 	#使配置生效

echo $JAVA_HOME		#测试是否成功
```

然后再回头去`/opt/pycharm/bin`目录下，`./pycharm.sh`运行pycharm吧。

记得运行之后，在菜单栏里找一个 创建桌面启动项 的选项。