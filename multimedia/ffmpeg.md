# FFMPEG

## [Tip] GIF Image Size Is Huge

### Description

If you try to use **ffmpeg** to record GIF images on your system, you will notice that the file size of the GIF images is huge. Maybe tens or hundreds of megabytes. While normally it should be just few hundreds kilobytes.

### Solution

First, record your needed video as a raw video using ffmpeg, then convert it into a GIF image using ImageMagick:

	ffmpeg -f x11grab -i $DISPLAY -codec:v pam -f rawvideo output.pam # Or whatever other options you want.
	
	convert -layers Optimize output.pam output.gif

Additionally, you can use the **-fuzz 10%** option to get better size. But as you increase the fuzz percentage. The quality will decrease. 

Note that the temproary raw video size is huge; maybe a hundreds of megabytes. So you need to have some free disk space to avoid some weird caching errors. After you are done of generating the GIF file from the raw video, you can remove it.

## [Problem] Non-monotonous DTS in output stream 0:1; This may result in incorrect timestamps in the output file.


### Description

If you are trying to use ffmpeg to record audio (with video probably), you may face an error like:

    [avi @ 0x561c9548ae00] Non-monotonous DTS in output stream 0:1; previous: 1203, current: 1028; changing to 1204. This may result in incorrect timestamps in the output file.

Which causes the audio to be out of sync with the video. There will be sort of "delay" by 2 or 3 seconds for the audio in the output file. Which is a bad thing to have.

### Solution

Make sure you are not using the **-ac** option. Removing it from the used ffmpeg command solves the problem.
