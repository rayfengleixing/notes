# ubuntu解决网易云音乐桌面图标无法打开

网易云音乐官网搜索下载Linux版本,Ubuntu安装包

```shell
cd ~/Downloads/
sudo dpkg -i neteTAB.deb
# 中间会提示安装vlc, So:
sudo apt install -f

cd /usr/share/applications/
subl netease-cloud-music.desktop
```

change:

`Exec=netease-cloud-music %U`

to:

`Exec=sh -c "unset SESSION_MANAGER && netease-cloud-music %U"`

就是给执行命令前面,多加了句命令,是什么我也不清楚,反正加上以后,桌面图标就可以正常打开了.