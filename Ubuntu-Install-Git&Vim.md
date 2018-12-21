# ubuntu install git&vim

### 安装git

```
sudo apt-get install git
git config --global user.name "rayfengleixing"
git config --global user.email "290844480@qq.com"
ssh-keygen -C '290844480@qq.com' -t rsa     # 一路回车
```

复制 ～/.ssh/id_rsa.pub 中的所有内容
登录github.com,个人设置中选中ssh× 项
选SSH title随便取
下面粘贴刚才复制的内容
就可以用git安装了

### 安装vundle

```
git clone https://github.com/gmarik/Vundle.vim.git ~/.vim/bundle/Vundle.vim
```

##### vim安装前准备

```sh
sudo apt install libncurses5-dev libgnome2-dev libgnomeui-dev libgtk2.0-dev libatk1.0-dev libbonoboui2-dev libcairo2-dev libx11-dev libxpm-dev libxt-dev python-dev python3-dev ruby-dev lua5.1 liblua5.1-dev libperl-dev
```

移除你已经安装的vim

```shell
sudo apt-get remove --purge vi vim-tiny vim vim-runtime gvim vim-common vim-gui-common vim-nox
```

或者是下面的

```shell
dpkg -l | grep vim
sudo dpkg -P vim vim-common vim-run
```

执行完卸载命令之后，强烈建议全局查找包含 vim 字样的文件和文件夹，手动删除，以免有漏网之鱼。如果卸载不干净，之后编译安装完了之后，很可能某种特性开启失败，导致又要重装，在任意文件夹下执行：

```shell
sudo find / -name "*vim*" > ~/find_vim_result
```

查找的结果都会在 ~/find_vim_result 中记录，你需要对照着这个记录，一个个手动去删除，但是要注意，有些是不可删除的文件，比如：

/usr/share/libquvi-scripts/0.9.20131130/media/vimeo.lua 
/usr/lib/modules/4.18.3-arch1-1-ARCH/kernel/drivers/media/platform/vimc/vimc_sensor.ko.xz 
/usr/lib/modules/4.18.3-arch1-1-ARCH/kernel/drivers/media/platform/vimc/vimc-debayer.ko.xz 
/usr/lib/modules/4.18.3-arch1-1-ARCH/kernel/drivers/media/platform/vimc/vimc_scaler.ko.xz

### 安装vim

```sh
cd ~
git clone https://github.com/vim/vim.git

cd vim
./configure --with-features=huge \
            --enable-multibyte \
            --enable-rubyinterp=yes \
            --enable-python3interp=yes \
            --with-python3-config-dir=/usr/lib/python3.6/config \
            --enable-perlinterp=yes \
            --enable-luainterp=yes \
            --enable-gui=gtk3 --enable-cscope --prefix=/usr/local
            
make VIMRUNTIMEDIR=/usr/local/share/vim/vim81

sudo make install

vim --version
```

