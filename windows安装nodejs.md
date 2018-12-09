# windows安装nodejs
## 安装nodejs
1. [官网](http://nodejs.cn/)下载，傻瓜式安装(别手贱点那个安装 chocolatey 什么的选项)
- 这里安装路径选到D盘，`D:\Program Files\nodejs`
- 安装好后命令行查看`npm -v`安装成功的话会显示版本号。
2. 改变原有的环境变量
- 我们要先配置npm的全局模块的存放路径以及cache的路径，例如我希望将以上两个文件夹放在NodeJS的主目录下，输入以下命令改变npm配置

```js      
npm config set prefix "D:\Program Files\nodejs\node_global"
npm config set cache "D:\Program Files\nodejs\node_cache"
```

- 在系统环境变量添加系统变量NODE_PATH，输入路径`D:\Program Files\nodejs\node_global\node_modules`，此后所安装的模块都会安装到改路径下
- 在命令行输入以下命令试着安装cnpm（注：“-g”这个参数意思是装到global目录下，也就是上面说设置的“D:\Program Files\nodejs\node_global”里面。）

```js
npm install -g cnpm --registry=https://registry.npm.taobao.org
```

- - 安装完毕后可以看到.\node_global\node_modules\cnpm 已经有内容，之后`cnpm -v`查看是否安装成功。
- 安装express模块，测试是否能正常加载模块

```js
cnpm install express -g
```

- - 在命令行输入node进入编辑模式

```js
require('express')
```

假设成功，可以看到有输出。假设出错，检查NODE_PATH的路径

