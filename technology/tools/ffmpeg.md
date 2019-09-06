<!-- TITLE: Ffmpeg -->
<!-- SUBTITLE: A quick summary of Ffmpeg -->

# ffmpeg工具
>ffmpeg \<global-options> \<input-options> -i \<input> \<output-options> \<output>

eg.

```
$ ffmpeg \
-y \ # global options
-c:a libfdk_aac -c:v libx264 \ # input options
-i bunny_1080p_60fps.mp4 \ # input url
-c:v libvpx-vp9 -c:a libvorbis \ # output options
bunny_1080p_60fps_vp9.webm # output url
```

## 格式

查看支持容器
>ffmpeg -formats

查看支持编解码格式
>ffmpeg -codecs
>ffmpeg -encoders

查看指定帮助
>ffmpeg -h encoder=libx264

像素格式
>ffmpeg -pix_fmts

![pix](https://pic2.zhimg.com/v2-c37be5bd4b53acbb34d9f7d45f28f025_r.jpg)

## 功能
### 裁剪
>ffmpeg -ss \<start> -i \<input> -t \<duration> -c copy \<output>
>ffmpeg -ss \<start> -i \<input> -to \<end> -c copy \<output>

eg.

>fmpeg -ss 00:01:50 -i \<input> -t 10.5 -c copy \<output>
>ffmpeg -ss 2.5 -i \<input> -to 10 -c copy \<output>

### 指定质量
**-b:v** or **-b:a** to set bitrate
eg.,-b:v 1000K = 1000 kbit/s, -b:v 8M = 8 Mbit/s

**-q:v** or **-q:a** to set fixed-quality parameter
e.g., -q:a 2 for native AAC encoder

**-crf** to set [Constant Rate Factor](https://slhck.info/video/2017/02/24/crf-guide.html) for libx264/libx265
**-vbr** to set constant quality for FDK-AAC encoder

#### Constant Bitrate (CBR)
#### Variable Bitrate (VBR)
- Average bitrate (ABR)
- Constant quantization parameter (CQP)
- Constant quality, based on psychovisual properties, e.g. CRF in x264/x265/libvpx-vp9
- Constrained bitrate (VBV)

#### 指定速度
```
ffmpeg -i <input> -c:v libx264 -crf 23 -preset ultrafast -an output.mkv
ffmpeg -i <input> -c:v libx264 -crf 23 -preset medium -an output.mkv
ffmpeg -i <input> -c:v libx264 -crf 23 -preset veryslow -an output.mkv
```

All presets: ultrafast, superfast, veryfast, faster, fast, medium, slow, slower, veryslow

eg.

- ultrafast	 4.85s	    15M
- medium	24.13s	  5.2M
- veryslow 112.23s	4.9M

## 过滤
### 缩放
Scale to 320×240:
>ffmpeg -i \<input> -vf "scale=w=320:h=240" \<output>

### 边距
Add black borders to a file, e.g. 1920×800 input to 1920×1080:
>ffmpeg -i \<input> -vf "pad=1920:1080:(ow-iw)/2:(oh-ih)/2" \<output>

### FADING
在特定时间内在特定时间内进行简单的淡入淡出和淡出
```
ffmpeg -i <input> -filter:v \
  "fade=t=in:st=0:d=5,fade=t=out:st=30:d=5" \
  <output>
```

### 绘制文本
```
ffmpeg -i <input> -vf \
drawtext="text='Test Text':x=100:y=50:\
fontsize=24:fontcolor=yellow:box=1:boxcolor=red" \
<output>
```

# ffprobe
功能参考：http://slhck.info/ffmpeg-encoding-course/#/47

```
ffprobe <input>
    [-select_streams <selection>]
    [-show_streams|-show_format|-show_frames|-show_packets]
    [-show_entries <entries>]
    [-of <output-format>]
```		