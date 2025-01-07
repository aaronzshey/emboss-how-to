# How to Install EMBOSS on Windows 11

Hello fellow labrats!  Today I'm going to teach you how to install EMBOSS 6.6.0 with minimal hassle on Windows 11.  It took me 
three days to get EMBOSS installed, so hopefully this will help you get it done a lot faster!

## Step 1: Download EMBOSS-6.6.0.tar.gz

The official EMBOSS website directs you to connect to their ftp server.  Unfortunately, the ftp client that comes with windows
by default (vsFTPd 2.2.2) is really bad and doesn't work (you can try following the directions from the EMBOSS site but they just plain don't work).

Instead, you're going to use cURL to download EMBOSS:

`curl -o 'ftp://emboss.open-bio.org/pub/EMBOSS/EMBOSS-6.6.0.tar.gz'`

This will download the gzipped tarball to your home folder (C:\Users\your username)

## Step 2: Unpack it

### IMPORTANT!  Do NOT just double-click the tar.gz file and let the windows extracter open it.  It'll take something like 2 hours (and my laptop has an SSD, 16GB RAM and an Intel i7-13700H).  

Let the fun begin!  Windows does NOT come with a gunzipper, so you need to download 7zip:

`winget install --id 7zip.7zip`

Now I couldn't get 7zip's command line interface to work, so instead open 7-zip (you can press the Windows key or click on the 
Windows icon in thee lower left-hand corner of the task bar and search 7-zip to find it), navigate to the location of EMBOSS-6.6.0.tar.gz (it should be in C:\Users\your username), select it, and then click "extract" on the top of the 7zip window (it looks like a navy blue minus symbol).

Great!  Now you have a tarball (.tar).  Thankfully, Windows does come with a tar extractor, so you can just select EMBOSS-6.6.0.tar in File Explorer and click "Extract All" near the top of the screen.

Wonderful!  It'll take about a minute for Windows to extract everything in the EMBOSS folder.  Almost done!

## Step 3: Install 