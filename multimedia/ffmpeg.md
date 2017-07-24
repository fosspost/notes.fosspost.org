# FFMPEG

## [Tip] GIF Image Size Is Huge

### Description

If you try to use **ffmpeg** to record GIF images on your system, you will notice that the file size of the GIF images is huge. Maybe tens or hundreds of megabytes. While normally it should be just few kilobytes.

### Solution

First, record your needed video as a raw video using ffmpeg, then convert it into a GIF image using ImageMagick:

	ffmpeg -f x11grab -i $DISPLAY -codec:v pam -f rawvideo output.pam

	convert -layers Optimize output.pam output.gif

Additionally, you can use the **-fuzz 10%** option to get better size. But as you increase the fuzz percentage. The quality will increase. 

Note that the temproary raw video size is huge; maybe a hundreds of megabytes. So you need to have some free disk space to avoid some weird caching errors.
