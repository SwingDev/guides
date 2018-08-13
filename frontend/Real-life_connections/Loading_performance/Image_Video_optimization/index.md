Image / Video optimization
==========================

Background
----------

Images and videos are often the first place to optimise in order to improve your application loading time. You need to remember to not serving source files on production. The same goes for images and videos.

Usually you receive hi-res assets from designer, which can be heavy. As a developer you need to keep the whole site smaller than a few megabytes tops and we have to keep the images crisp on high density displays (like iPhone's Retina display). It's important to find a golden mean between images / videos size and their quality.

More information about image optimisation you can find [here](https://developers.google.com/web/fundamentals/performance/optimizing-content-efficiency/image-optimization).

Rules
-----

*   Lazy load the right size of the image / video for the user's screen.  
    
*   Use [Responsive images](https://developer.mozilla.org/en-US/docs/Learn/HTML/Multimedia_and_embedding/Responsive_images) whenever you can.  
    
*   Optimise images and videos in production build  
    

How can one optimize images and videos
--------------------------------------

### Images

*   Don't just drop the images you receive right into the folder with application's assets.  
    
    *   Have images sized in multiple variants - all sized just right for how big the image will be **in your layout.**  
        
    *   Always prefer JPG over PNG - for non-transparent graphics.   
        
    *   Use ImageOptim on every image you commit.  
        
    *   Recompress JPGs to quality that's good - use imagemagick's 'convert' utility, e.g. like this:  
        

convert intro-1280x1280.png -resize 480x -quality 80 tile@1x.jpg  
convert intro-1280x1280.png -resize 960x -quality 75 tile@2x.jpg  
convert intro-1280x1280.png -resize 1280x -quality 65 tile@3x.jpg

Prefer manual approach to an automated solution, as the solution usually won't know what size the image will be displayed at.

### Videos

*   Videos are huge!   
    
*   Embed YouTube / Vimeo if possible.  
    
*   Use ffmpeg toolset to recompress the videos, e.g.:  
    

ffmpeg -i input.mp4 -y -movflags +faststart -strict experimental -c:v libx264 -crf 26 -vf scale=1280:720 -s 1280x720

'`crf`' flag determines the final quality.