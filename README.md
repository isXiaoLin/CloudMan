<h1 align="center">CloudMan</h1>
用来为 Sony WalkMan 播放器生成播放列表的小程序

🎆for and by Music Lovers

![Lisence](https://img.shields.io/badge/license-MIT-blue.svg) [![Codacy Badge](https://app.codacy.com/project/badge/Grade/bc1e4b82b99148aca374b22108847f47)](https://www.codacy.com/manual/isXiaoLin/CloudMan) [![CHANGELOG](https://img.shields.io/badge/%F0%9F%A4%96-release%20notes-00B2EE.svg)](https://github.com/isXiaoLin/CloudMan/blob/node/CHANGELOG.md)

## 简介

本来是只想写一个下载网易云歌单并自动添加元数据 (曲名、专辑名、封面图等) 的小程序的, 歌词由某位 dalao 写的 `ZonyLrcToolsX` 来处理, 但是发现这个程序的逻辑有点小问题 (大概也不算小, 翻译基本上没对上过原文, 除了少数几首开头没有作词作曲信息的曲子), 导致翻译与原文对不上, 于是就顺带把歌词处理也给加上了

~~之前没用过 Python, 使用 Py 是为了使用 `mutagen` 库, 代码不精还请多多指教~~

用熟悉的 Node.js 重构了一遍, 旧功能已基本实现, 因为熟悉所以后续可能会加更多新功能

经测试现在的代码应该已经基本稳定了，如果还是有 BUG 或者有可以改进的地方欢迎提 IS 或 PR 嗷 (小声

## Features / TODOs

- [x] 下载用户歌单
- [x] 填充音乐元数据
- [x] 下载并格式化歌词及翻译
- [x] 允许排除 / 附加歌单
- [x] 为本地文件夹生成列表
- [x] 登陆后下载无损格式音乐
- [x] 自定义下载质量 (默认最高[若未开通会员仅可下载少量无损歌曲])
- [x] 多线程下载
- [x] 下载错误自动重试
- [x] 处理云端歌单变动
- [x] 合并歌词原文与翻译
- [x] 本地化 NeteaseCloudMusicApi
- [ ] 处理播放器端列表变动
- [ ] 指定为某几个歌单生成组合列表

## 依赖

- Node.js 10+
- ~~[Binaryify/NeteaseCloudMusicApi](https://github.com/Binaryify/NeteaseCloudMusicApi)~~
  - 感谢项目原作者支持 Node.js 调用

## 配置

```ini
# 日志等级
cm_logLevel = info

# 是否为 /MUSIC 目录中的文件夹生成播放列表
cm_generatePlaylistFile = true

# 网易云手机账号
cm_phone = 13912345678
# 网易云密码
cm_password = 123456

# 附加的歌单 (用,分割)
cm_extraPlaylist = 
# 排除的歌单 (用,分割)
cm_excludePlaylist = 

# 是否下载收藏的专辑
cm_downloadSubAlbum = false
# 附加的专辑 (用,分割)
cm_extraAlbum = 
# 排除的专辑 (用,分割)
cm_excludeAlbum = 

# 下载音质
cm_bitRate = 999000

# 是否将歌词与翻译合并为一行
cm_mergeTranslation = false

# 处理/下载歌曲的并发数
cm_playlistConcurrency = 3
```

## 食用方法

1.  在 WalkMan 根目录输入 `git clone https://github.com/isXiaoLin/CloudMan.git -b node`
2.  进入 `CloudMan` 目录, 输入 `npm i`
3.  将 `.env.example` 重命名为 `.env` 并按需修改
4.  输入 `npm start` 即可

## 运行方式

程序运行时自动在根目录的 `/MUSIC` 中生成 `CloudMan` 文件夹, 该文件夹中 `MUSIC` 文件夹用于存放歌曲文件及歌词文件, 父目录用于存放播放列表文件

所有歌曲文件均以歌曲 ID 命名并统一存放至 `MUSIC` 文件夹中, 以便于不同播放列表引用同一文件

## SensMe 及 Music Center for PC

这几天试用了一下 Sony 官方的 Music Center for PC, 发现其实还算好用，尤其是元数据补充得非常齐并且准确率也很高 (这也太高了吧 (碎碎念

这个项目是用网易云得数据所以没法比得嘛 (自我安慰

但是依然是可以进行 SensMe 分析的！只用打开 Music Center for PC，在`文件->导入文件夹`中选择 WALKMAN-SD 中的`MUSIC/CloudMan`文件夹，然后全选右键点击`获取未知元素`就可以啦！

## Author

**CloudMan** © [XiaoLin](https://github.com/isXiaoLin), Released under the [MIT](./LICENSE) License.<br>

> Blog [@xiaolin](https://www.xiaolin.in) · GitHub [@isXiaoLin](https://github.com/isXiaoLin) · Twitter [@isXiaoLin](https://twitter.com/isXiaoLin)
