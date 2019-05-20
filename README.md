###  FFmpeg-iOS (SSL)、kxmovie

#####  iOS FFmpegFFmpeg-iOS
1. At first we need to install gas-preprocessor（for ffmpeg)

```
git clone https://github.com/libav/gas-preprocessor
cp -R ~/Downloads/gas-preprocessor-master/gas-preprocessor.pl /usr/local/bin
```

2. Also grab a yasm

```
brew install yasm
```

3. Get already builded FFmpeg-iOS-build-script

> FFmpeg-iOS-build-script is a build of ffmpeg in iOS with SSL support to stream https files too。

```
git clone https://github.com/kewlbear/FFmpeg-iOS-build-script
cd FFmpeg-iOS-build-script
./build-ffmpeg.sh    （FFmpeg-iOS）
```


4. Get working an example player kxmovie

```
git clone https://github.com/applexiaohao/kxmovie
```

#### You can use current FFmpegTestDemo project
1.demo，FFmpeg-iOS kxmovie
![22](media/15211902572072/22.png)

2. Link next libs to your frameworks

```
VideoToolbox.framework
libiconv.tbd
libbz2.tbd
libz.tbd
```

#### Common errors:

> 1：'libavformat/avformat.h' file not found

```
Set a correct path in Build Settings -> Header Search Paths 
$(SRCROOT)/FFmpegDemo/FFmpeg-iOS/include
```

> 2：Use of undeclared identifier 'PIX_FMT_RGB24'; did you mean 'AV_PIX_FMT_RGB24'?


```
Just replace a string 'PIX_FMT_RGB24' with 'AV_PIX_FMT_RGB24'
```

> 3：Expected a type、Use of undeclared identifier 'UIImage'

```
In KxMovieDecoder.h add #import <UIKit/UIKit.h>
```

> 4：FFmpeg 3.0
> Undefined symbols for architecture armv7:
  "_avpicture_deinterlace", referenced from:
      -[KxMovieDecoder decodeFrames:] in KxMovieDecoder.o
ld: symbol(s) not found for architecture armv7
clang: error: linker command failed with exit code 1 (use -v to see invocation)


```
Just comment this method call 'avpicture_deinterlace（)'
```   





