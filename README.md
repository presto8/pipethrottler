pipethrottler
=============

Passes through stdin to stdout, automatically throttling if CPU load gets too high.

Example
-------

Let's say you have a file foo.avi that you want to transcode to bar.avi. If you
use a program like ffmpeg, it will be very CPU intensive and consume all of the
CPU (only basic ffmpeg options shown for brevity):

    cat foo.avi | ffmpeg -i - bar.avi

Using pipethrottler, it's possible to run this same command while limiting the
CPU use. The following command would automatically adjust the I/O rate to keep
the CPU use below 50%.

     cat foo.avi | pipethrottler --maxcpu 50 | ffmpeg -i - bar.avi
     

