# m3u8-download

Download from m3u8 address as MP4 video file using [ffmpeg](https://github.com/FFmpeg/FFmpeg).

## Usage

```sh
$ m3u8-download
usage: m3u8-download M3U8_ADDRESS {OUTPUT_FILENAME}
```

## How it works

- It accepts [MPEG2 Transport Stream](https://wiki.multimedia.cx/index.php/MPEG-2_Transport_Stream) format.
- It outputs an [MP4](https://en.wikipedia.org/wiki/MP4_file_format) container format.
- It leverages [ffmpeg](https://github.com/FFmpeg/FFmpeg), a command line toolbox to manipulate, convert and stream multimedia content.
	- It uses `-c copy` to copy both audio and video streams as-is.
	- It uses `-bsf:a aac_adtstoasc` [bitstream filter](https://ffmpeg.org/ffmpeg-bitstream-filters.html#Bitstream-Filters) to convert Audio Data Transport Stream ([ADTS](https://wiki.multimedia.cx/index.php/ADTS)) to MPEG-4 Audio Specific Configuration bitstream.

## Preview

![screenshot](screenshot.png?raw=true "Screenshot")
