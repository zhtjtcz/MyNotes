---
title: FFMEPG 相关
layout: default
nav_order: 8
---

## 视频处理命令

### 分辨率调整

```shell
ffmpeg -i input.mp4 -vf "scale=368:800" output.mp4
```

### 视频拼接

#### 相同分辨率

```shell
ffmpeg -i hc.mp4 -i hc_face.mp4 -filter_complex "[0:v]pad=iw*2:ih*1[a];[a][1:v]overlay=w" new.mp4

ffmpeg -i 0.mp4 -i 1.mp4 -filter_complex "[0:v]pad=iw*2:ih*1[a];[a][1:v]overlay=w+100" out.mp4

# iw * 2 调整画布总宽度
# overlay 可以挪动第二个视频位置，加偏移量可以右移
```

### 短视频拼接为长视频

创建`file_list.txt`，填入：

```txt
file 'result0.mp4'
file 'result1.mp4'
file 'result2.mp4'
file 'result3.mp4'
file 'result4.mp4'
file 'result5.mp4'
file 'result6.mp4'
file 'result7.mp4'
```

然后执行

```shell
ffmpeg -f concat -safe 0 -i file_list.txt -c copy output.mp4
```

### 视频切分

切前4秒：

```shell
ffmpeg -i input.mp4 -ss 00:00:00 -t 4 output.mp4
```

### 转码

```shell
ffmpeg -i input.mp4 -c:v libx264 -preset slow -crf 22 -c:a aac -b:a 128k output.mp4
ffmpeg -i 1.mov -vcodec copy -acodec copy 1.mp4
```