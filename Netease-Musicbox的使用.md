## Netease-Musicbox的使用

```
$ musicbox
```

Enjoy it !

### 键盘快捷键

| J     | Down            | 下移               |
| ----- | --------------- | ------------------ |
| K     | Up              | 上移               |
| H     | Back            | 后退               |
| L     | Forword         | 前进               |
| U     | Prev page       | 上一页             |
| D     | Next page       | 下一页             |
| F     | Search          | 快速搜索           |
| [     | Prev song       | 上一曲             |
| ]     | Next song       | 下一曲             |
| =     | Volume +        | 音量增加           |
| -     | Volume -        | 音量减少           |
| Space | Play/Pause      | 播放/暂停          |
| ?     | Shuffle         | 手气不错           |
| M     | Menu            | 主菜单             |
| P     | Present/History | 当前/历史播放列表  |
| I     | Music Info      | 当前音乐信息       |
| ⇧+P   | Playing Mode    | 播放模式切换       |
| A     | Add             | 添加曲目到打碟     |
| ⇧+A   | Enter album     | 进入专辑           |
| G     | To the first    | 跳至首项           |
| ⇧+G   | To the end      | 跳至尾项           |
| Z     | DJ list         | 打碟列表           |
| S     | Star            | 添加到收藏         |
| C     | Collection      | 收藏列表           |
| R     | Remove          | 删除当前条目       |
| ⇧+J   | Move Down       | 向下移动当前项目   |
| ⇧+K   | Move Up         | 向上移动当前项目   |
| ⇧+C   | Cache           | 缓存歌曲到本地     |
| ,     | Like            | 喜爱               |
| .     | Trash FM        | 删除 FM            |
| /     | Next FM         | 下一FM             |
| Q     | Quit            | 退出               |
| T     | Timing Exit     | 定时退出           |
| W     | Quit&Clear      | 退出并清除用户信息 |

#### Ubuntu/Debian

```
$ sudo pip3 install NetEase-MusicBox
$ sudo apt install mpg123
```

配置文件地址: `~/.netease-musicbox/config.json` 可配置缓存，快捷键，消息，桌面歌词。 由于歌曲 API 只接受中国大陆地区访问，港澳台及海外用户请自行设置代理：

```
export http_proxy=http://ip:port
curl ip.cn
```

显示IP属于中国大陆地区即可。

### 错误处理

当某些歌曲不能播放时，总时长为 00:01 时，请检查是否为版权问题导致。

如遇到在特定终端下不能播放问题，首先检查**此终端**下mpg123能否正常使用，其次检查**其他终端**下musicbox能否正常使用，报告issue的时候请告知以上使用情况以及出问题终端的报错信息。

同时，您可以通过`tail -f ~/.netease-musicbox/musicbox.log`自行查看日志。 mpg123 最新的版本可能会报找不到声音硬件的错误，测试了1.25.6版本可以正常使用。