# uconnect-handbrake-presets
Handbrake Preset file(s) for UConnect Theatre, especially for Chrysler Pacificas

Full credit goes to the folks over at [pacificaforums.com](https://www.pacificaforums.com/threads/uconnect-movies-via-usb-what-format.11914/), and especially to [jbebel](https://www.pacificaforums.com/members/jbebel.43290/) - only adding here so that I can stop searching through multi-year threads with others who are trying to get movies/shows onto their minivans' screens.

Pull requests welcome.

## Instructions

Copied from [jbebel's latest post](https://www.pacificaforums.com/threads/uconnect-movies-via-usb-what-format.11914/post-529745):

This re-enables the H.264 main profile, and they are built with Handbrake 1.1.2 on Linux. This requires to VRM to be at at least 17.50.13, which you can check on the rear screen under settings. If it's not, ask your dealer about service bulletin 08-007-18 REV. A.

MKV and MP4 versions are identical except the container. Both work fine in the van, but if you have devices that work better with MP4, choose it instead. Editing metadata and adding cover art is easier with MKV.

I started with the H.264 MKV 720p30 as it was the closest match to the screen and in the more versatile MKV container. MP4 works just as well if you have other devices that have better compatibility with one or the other, and it's closest to the "Android 720p30" preset.

I set Anamorphic to loose, which closely matches the pixel aspect ratio of the source. This allows HD content to keep close-to-square pixels optimized for the screen size, and for anamorphic DVDs to remain stored anamorphically to conserve space/quality. If you are only encoding HD sources for Uconnect, then turning anamorphic off will enforce square pixels which is probably better.

Previously I switched the H.264 profile to baseline, as the main profile resulted in dropped frames and stuttered video. The van seemed to handle the baseline profile better. But as of VRM version 17.50.13, the van seems to handle the main profile just fine, so I've dropped that change.

I added English as the default audio language so international movies will include the track my kids can understand. If your kids are multi-lingual or not native English speakers, you might want to change this.

I left the audio at 2-channel AAC Dolby Pro Logic II as I found the van can kind of decode the Pro Logic if you use the surround mode, and it still sounds pretty good in headphones or just in stereo.

I also unchecked the boxes to burn DVD or Blu-ray subtitles into the video, as I didn't want these burned in. Feel free to adjust the subtitle defaults to your tastes.

I did not remove chapters. The van doesn't currently use them, but they take up very little space, and might be supported in a future update, or if you use the files on another platform. Some remove them because the van uses the title of chapter 1 if you don't have a title set. So be sure to set a title in the tags tab before you start encoding a movie.

I got the 256 GB SanDisk Ultra Fit USB 3.1 drive. It's tiny and will hold around 128 movies since with this preset, each movie is around 2 GB. If you have a smaller drive, you could reduce the quality a bit to save space. I liked RF: 21, but I think I'd be ok with RF: 23 and it would produce smaller files. Also, I formatted the drive with FAT32. I think it's the right choice for maximum support and minimizing the chances of misusing file security features, but it does limit file size to 4 GB. The van does not support exFAT.

To summarize my procedure:

1. Open the source in Handbrake with the Uconnect preset.
2. Set the output filename at the top, and set the Title in the "Tags" tab (if you have that in your interface)
3. Optionally set anamorphic to off for HD sources which you are only encoding for Uconnect or smaller screens.
4. Optionally set "Tune" to match your content. "Animation" for older hand-drawn animated movies. "Film" for 3D animations and live action.
5. Begin encoding.
6. Look for a good cover art, like at fanart.tv (Movie Thumbs at the bottom of each page) or themoviedb.org (choose backdrops in English).
7. Convert the movie thumb to a format that works well with Uconnect using imagemagick:
convert $FILE -background none -gravity center -resize 800x600 -extent 800x600 cover.png
8. Once handbrake is done, use mkvtoolnix to attach cover.png to the .mkv file. Or if you chose mp4, then find an mp4 tag editor for you operating system. I don't have a common recommendation yet. I used easytag in Linux.
9. Copy onto the USB flash drive for the car.
