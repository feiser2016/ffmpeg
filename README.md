# Automated FFMPEG Compilation script for Ubuntu

Before Proceeding with the FFMPEG compilation script, please make sure the check the [Wiki](https://github.com/stoyanovgeorge/ffmpeg/wiki "Wiki") section for different usage examples of FFMPEG. Another good source of information is the [Ubuntu compilation guide for FFMPEG](https://trac.ffmpeg.org/wiki/CompilationGuide/Ubuntu)

Automated scripts for compilation of [FFMPEG v.4.1](https://ffmpeg.org/ "FFMPEG Official Page") and its most popular librarires for Ubuntu based systems. The script is tested and working on Ubuntu 16.04 LTS Xenial Xerus and Ubuntu 18.04 LTS Bionic Beaver. After compilation the FFMPEG configuration should be:

```
ffmpeg version 4.1 Copyright (c) 2000-2018 the FFmpeg developers
  built with gcc 7 (Ubuntu 7.3.0-27ubuntu1~18.04)
  configuration: --pkg-config-flags=--static --extra-libs='-lpthread -lm' --toolchain=hardened --enable-gpl --enable-nonfree --enable-version3 --disable-stripping --enable-avisynth --enable-libass --enable-libfontconfig --enable-libfreetype --enable-libfribidi --enable-libgme --enable-libgsm --enable-librubberband --enable-libshine --enable-libsnappy --enable-libssh --enable-libtwolame --enable-libwavpack --enable-libzvbi --enable-openal --enable-sdl2 --enable-libdrm --enable-frei0r --enable-ladspa --enable-libpulse --enable-libsoxr --enable-libspeex --enable-avfilter --enable-postproc --enable-pthreads --enable-libfdk-aac --enable-libmp3lame --enable-libopus --enable-libtheora --enable-libvorbis --enable-libvpx --enable-libx264 --enable-libx265 --disable-ffplay --enable-libopenjpeg --enable-libsrt --enable-libwebp --enable-libxvid --enable-libvidstab --enable-libopenh264 --enable-zlib --enable-openssl
  libavutil      56. 22.100 / 56. 22.100
  libavcodec     58. 35.100 / 58. 35.100
  libavformat    58. 20.100 / 58. 20.100
  libavdevice    58.  5.100 / 58.  5.100
  libavfilter     7. 40.101 /  7. 40.101
  libswscale      5.  3.100 /  5.  3.100
  libswresample   3.  3.100 /  3.  3.100
  libpostproc    55.  3.100 / 55.  3.100
Hyper fast Audio and Video encoder
usage: ffmpeg [options] [[infile options] -i infile]... {[outfile options] outfile}...
``` 

The following libraries are also installed from source: 
1. Video Codecs:
	* [Dirac](http://www.bbc.co.uk/opensource/projects/dirac/ "Dirac Codec") - Dirac is an open and royalty-free video compression format, specification and system developed by BBC Research & Development.
	* [Kvazaar](http://ultravideo.cs.tut.fi/ "Kvazaar Codec") - Kvazaar is an award-winning academic open-source HEVC encoder developed from scratch in C.
	* [OpenH264](http://www.openh264.org/ "OpenH264 Codec") - OpenH264 is a free software library for real-time encoding and decoding video streams in the H.264/MPEG-4 AVC format, developed by Cisco.
	* [OpenJPEG](http://www.openjpeg.org/ "OpenJPEG Codec") - OpenJPEG is an open-source JPEG 2000 codec written in C language. It has been developed in order to promote the use of JPEG 2000, a still-image compression standard.
	* [Theora](https://www.theora.org/ "Theora Codec") - Theora is a free and open lossy video compression format from the Xiph.org Foundation.
	* [x264](http://www.videolan.org/developers/x264.html "x264 Codec") - x264 is a free software library developed by VideoLAN for encoding video streams into the H.264/MPEG-4 AVC format.
	* [x265](http://www.videolan.org/developers/x264.html "x265 Codec") - x265 is a library for encoding video into the High Efficiency Video Coding (HEVC/H.265) video compression format.
	* [Libvpx](https://www.webmproject.org/code/ "Libvpx Codec") - Libvpx is a free software video codec library from Google and the Alliance for Open Media. 
	* [Webp](https://developers.google.com/speed/webp/ "Webp Codec") - WebP is an image format employing both lossy[6] and lossless compression. It is currently developed by Google
	* [AV1](https://aomedia.org/) - AOMedia Video 1 (AV1), is an open, royalty-free video coding format designed for video transmissions over the Internet. It is being developed by the Alliance for Open Media (AOMedia)
	
2. Video Plugins:
	* [vid.stab](http://public.hronopik.de/vid.stab/ "vid.stab Video Plugin") - vid.stab provides a reasonably easy and flexible way to stabilize (deshake) even strongly jiggled video clips.

3. Transport Protocols
	* [SRT](https://www.srtalliance.org/) - Secure Reliable Transport (SRT) is an open source video transport protocol and technology stack that optimizes streaming performance across unpredictable networks with secure streams and easy firewall traversal, bringing the best quality live video over the worst networks. 

4. Audio Codecs:
	* [FDK-AAC](https://www.iis.fraunhofer.de/en/ff/amm/impl.html "FDK-AAC Codec") - Fraunhofer's FDK AAC code provides a complete, high-quality audio compression.
	* [Lame MP3](http://lame.sourceforge.net/ "Lame MP3 Codec") - LAME is a high quality MPEG Audio Layer III (MP3) encoder licensed under the LGPL.
	* [Opus](http://opus-codec.org/downloads/ "Opus Codec") - Opus is a lossy audio coding format developed by the Xiph.Org Foundation and standardized by the Internet Engineering Task Force
	* [Vorbis](http://www.vorbis.com/ "Vorbis Codec") - Vorbis is a free and open-source codec for lossy audio compression headed by the Xiph.Org Foundation.

5. Container Formats:
	* [Ogg](https://www.xiph.org/ogg/ "Ogg Container Format") - Ogg is a free, open container format maintained by the Xiph.Org Foundation.
6. Filters
	* [VMAF](https://github.com/Netflix/vmaf "VMAF Github Page") - VMAF is a perceptual video quality assessment algorithm developed by Netflix


### Usage Examples

Please run the [compilation.sh](https://github.com/stoyanovgeorge/ffmpeg/blob/master/compilation.sh "compilation.sh") script `sh compilation.sh` and it will take care of installing the latest version of FFMPEG and its most popular libraries from scratch presuming that you have cloned this repository.

In case you want to automate the installation of GIT and run the compilation script you can execute: 

```
sudo apt update && sudo apt install git -y && git clone https://github.com/stoyanovgeorge/ffmpeg.git && cd ffmpeg && sh compilation.sh
```

If you want to omit the installation of some of these libraries, please comment the line in the [compilation.sh](https://github.com/stoyanovgeorge/ffmpeg/blob/master/compilation.sh "compilation.sh") script and also remove the parameter in the [ffmpeg.sh](https://github.com/stoyanovgeorge/ffmpeg/blob/master/scripts/ffmpeg.sh "ffmpeg.sh") script. 

For example if you want to remove x265 support, you need to comment the `sh $PWD/scripts/libx265.sh 2> $HOME/ffmpeg/logs/libx265.log` line in the [compilation.sh](https://github.com/stoyanovgeorge/ffmpeg/blob/master/compilation.sh "compilation.sh") script.

And in the [ffmpeg.sh](https://github.com/stoyanovgeorge/ffmpeg/blob/master/scripts/ffmpeg.sh "ffmpeg.sh") script you need to remove `--enable-libkvazaar` option.

### Bugs and Missing Features

1. Currently I am unable to compile the AV1 video codec from source. 

Please use [Github Issues](https://github.com/stoyanovgeorge/ffmpeg/issues "Github Issues") in case you spot a bug or have an idea how to optimize the scripts. 

### External Links

* [FFMPEG Generic Compilation Guide](https://trac.ffmpeg.org/wiki/CompilationGuide/Generic "FFMPEG Generic Compilation Guide")
* [FFMPEG Ubuntu Compilation Guide](https://trac.ffmpeg.org/wiki/CompilationGuide/Ubuntu "FFMPEG Ubuntu Compilation Guide")
* [FFMPEG Syntax](https://ffmpeg.org/ffmpeg-all.html "FFMPEG Syntax")
* [FFMPEG Filters](https://ffmpeg.org/ffmpeg-filters.html "FFMPEG Filters")
* [Comparison of Video Codecs and Containers](http://download.das-werkstatt.com/pb/mthk/info/video/comparison_video_codecs_containers.html "Video Codecs Comparison")
* [List of YUV Formats](http://www.fourcc.org/yuv.php "List of YUV Formats")
* [Comparison of Container Formats](http://www.digitizationguidelines.gov/guidelines/video_reformatting_compare.html "Comparison of Container Formats")
* [X264 Encoding Guide](https://trac.ffmpeg.org/wiki/Encode/H.264 "X264 Encoding Guide")
* [FFV1 Video Encoding](https://trac.ffmpeg.org/wiki/Encode/FFV1 "FFV1 Video Encoding")
* [FFMPEG Ubuntu Compilation Guide](https://trac.ffmpeg.org/wiki/CompilationGuide/Ubuntu "FFMPEG Ubuntu Compilation Guide")
* [Kvazaar - Open Source HEVC Encoding Library GitHub Project](https://github.com/ultravideo/kvazaar "Kvazaar GitHub")
* [Kvazaar Official Webpage](http://ultravideo.cs.tut.fi/#encoder "Kvazaar Official Webpage")
* [X265 Commands](http://x265.readthedocs.io/en/default/cli.html "X265 Encoding Guide")
* [FFMPEG Presets Github](https://github.com/joeyblake/FFmpeg-Presets "FFMPEG Precompiled Presets")
* [FFPROBE examples](http://www.bugcodemaster.com/article/use-ffprobe-obtain-information-video-files "FFPROBE examples")
* [FFProbe Tips](https://trac.ffmpeg.org/wiki/FFprobeTips "FFProbe Tips")
* [VP9 Compression Guide](https://sites.google.com/a/webmproject.org/wiki/ffmpeg/vp9-encoding-guide "VP9 Compression Guide")
* [VP9 vs. H.264 vs. H.265 Comparison](https://blogs.gnome.org/rbultje/2015/09/28/vp9-encodingdecoding-performance-vs-hevch-264/ "VP9 vs. H.264 vs. H.265")
* [VP9 Encoder Parameters](https://www.webmproject.org/docs/encoder-parameters/ "VP9 Encoder Parameters")
* [VMAF](https://github.com/Netflix/vmaf "VMAF Github Page")

