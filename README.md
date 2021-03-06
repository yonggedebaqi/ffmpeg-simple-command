# ffmpeg useful command


## 格式转换

m4a转mp3
------
`
ffmpeg -i input.m4a output.mp3
`

mkv转mp4
------
`
ffmpeg -i input.m4a output.mp4
`

注意：在不指定参数的情况下所有参数都会使用默认值


## 一张图和一段音频生成视频

`
ffmpeg -loop 1 -i image.jpg -i audio.mp3 -c:a copy -c:v libx264 -shortest video.mp4
`

## 压制硬字幕

`
ffmpeg -i input.mp4 -filter_complex OPTION output.mp4
`
##### OPTION传一个字符串

如"subtitles=subtitleName.ass:force_style='PrimaryColour=&H000000,BackColour=&Hffffff,OutlineColour=&Hffffff,BorderStyle=4,Outline=1,Shadow=0,Bold=0,MarginV=30'"


##### OPTION参数解释

|Name|explanation|example|
| :------------ |:------------|:------------|
| PrimaryColour|字体颜色|&H000000|
| BackColour|背景颜色|&Hffffff|
| OutlineColour|描边颜色|&Hffffff|
| BorderStyle|边框样式|4:不透明3:透明边框|
| BorderStyle|与底部距离|30|

`
order = 'ffmpeg -i "{}"  -filter_complex "subtitles={}:force_style=\'PrimaryColour=&Hffffff,BackColour=&Hffffff,OutlineColour=&H000000,BorderStyle=2,Outline=1,Shadow=0,Bold=0,MarginV=15\'" "{}"'.format(input,subtitle_name,output)
`

## 下载线上m3u8视频并转MP4

`
ffmpeg -protocol_whitelist "file,http,https,tcp,tls" -i index.m3u8 -acodec copy -vcodec copy out.mp4
`

|parameter|explanation|
| :------------ |:------------|
|index.m3u8|m3u8索引文件|
|protocol_whitelist|请求方式白名单|
|acodec|音频编码|
|vcodec|视频编码|

#### -protocol_whitelist "file,http,https,tcp,tls" 的添加可解决如下报错

`
Protocol 'http' not on whitelist 'file,crypto'!
`



## 例子

[get_englishpod_video 一张图和一段音频生成视频的实例](https://github.com/skygongque/ffmpeg-simple-command/blob/master/get_englishpod_video_intruduction)
----
结果发布于B站：https://www.bilibili.com/video/BV1eE411a7Cm

get 6 minute english with subtitle inside 压制6 minute english硬字幕 白色背景
----

get qiyi video (single video)
----


