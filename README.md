# m3u8-download

Download from m3u8 address as an MP4 video file using [ffmpeg](https://github.com/FFmpeg/FFmpeg).

## Usage

```sh
$ m3u8-download
usage: m3u8-download M3U8_ADDRESS {OUTPUT_FILENAME}
```

#### Example

```sh
$ m3u8-download "https://test-streams.mux.dev/x36xhzz/x36xhzz.m3u8" "example.mp4"
```

## How it works

- It accepts [MPEG2 Transport Stream](https://wiki.multimedia.cx/index.php/MPEG-2_Transport_Stream) format.
- It outputs an [MP4](https://en.wikipedia.org/wiki/MP4_file_format) container format.
- It uses [ffmpeg](https://github.com/FFmpeg/FFmpeg), a command line toolbox to manipulate, convert and stream multimedia content.
	- `-c copy` to copy both audio and video streams as-is.
	- `-bsf:a aac_adtstoasc` [bitstream filter](https://ffmpeg.org/ffmpeg-bitstream-filters.html#Bitstream-Filters) to convert Audio Data Transport Stream ([ADTS](https://wiki.multimedia.cx/index.php/ADTS)) to MPEG-4 Audio Specific Configuration bitstream.
