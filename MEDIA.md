# 扒素材

## you-get

### 准备工具
- 官网下载最新版本python 'https://www.python.org/downloads/'
- 打开cmd，使用pip3安装you-get 'pip3 install you-get'
- 过程中可能还需要升级pip库和更新you-get，指令分别如下 'python -m pip install --upgrade pip' 'pip3 install --upgrade you-get'

### 开始下载
- 直接下载到cmd所在目录 'you-get https://www.bilibili.com/video/BV1rL411G7Pm?spm_id_from=333.851.b_62696c695f7265706f72745f646f756761.41'
- 可以先查看当前视频的所有格式、清晰度列表 'you-get -i https://www.bilibili.com/video/BV1rL411G7Pm?spm_id_from=333.851.b_62696c695f7265706f72745f646f756761.41'
- 可以选择对应的格式进行下载 'you-get --format=flv https://www.bilibili.com/video/BV1rL411G7Pm?spm_id_from=333.851.b_62696c695f7265706f72745f646f756761.41'

## ffmpeg

### 准备工具
- 官网下载windows版本，Windows builds from gyan.dev 'https://ffmpeg.org/download.html'
- 跳到'https://www.gyan.dev/ffmpeg/builds/#release-builds'后下载'ffmpeg-release-essentials.zip'
- 下载后将bin文件目录添加到Windows环境变量Path下以便能在cmd使用 'D:\Tools\ffmpeg-4.4-essentials_build\bin' 'ffmpeg –version'

### 开始下载
- 一般用来下载blob开头的视频源，可以通过f12 -> network找到m3u8格式的链接 'https://b.baobuzz.com/m3u8/32066.m3u8?sign=41ccce6d3639cd97613e6475751290f3'

## VLC

# 录屏

## OBS Studio
- github 'https://github.com/jp9000/obs-studio'
- 官网 'https://obsproject.com/'

## ScreenToGif
- 官网 'https://www.screentogif.com/'
- github 'https://github.com/NickeManarin/ScreenToGif'

