---
layout: post
title: "Video Subtitle Auto-generating with Python and Burning with ffmpeg"
date:   2022-10-18 13:40:00 +0200
categories: projects
math: true
---

## Motivation

It is straightforward and quicker to learn a foreign language from YouTube videos. However, many videos don't have subtitles, so it will help if it is possible to generate subtitles in different languages from the video files.
For this purpose, Python is the first choice for speech recognition.


## Python packages and tools needed:

- [pytube](https://pytube.io/), if need to download YouTube videos, but be careful, not to do torrent downloading, and download as less as possible.
- [autosub](https://pypi.org/project/autosub/). `pypi` installation only works for Python 2.x, for 3.x, need to use : `pip install git+https://github.com/agermanidis/autosub.git`. When it needs translating from a source language to another language, the Google Cloud Translation API key is required, but there is a free tier of 50,000 characters per month.
- [FFmpeg](https://www.ffmpeg.org/download.html#build-windows).

### Other optional tools
- VS Code plugin: `Subtitles Editor`. For subtitle language translation without providing Google API. Maybe not as perfect as with Google API, but it works.. 

### Results

- An example of `.srt` subtitle files compared in VS Code:  

![srt files comparison](/images/srt_swidish_english_chinese.PNG){:width="500px"}
{:center-img}

The subtitles look good, and it does not need to be perfect, but giving some hints is ok. This video is from a Vlogger, and the speech recognition API can't capture all the words sometimes when the speaker is too fast or if there are fast word connections.
