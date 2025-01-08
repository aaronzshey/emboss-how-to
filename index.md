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

## Step 3: Install WSL

Everyone knows that using the Windows command line is like talking to the spawn of the devil himself.  Create-Item, Remove-Item, Get-Help, etc, etc... whoever invented PowerShell sits right next to Microsoft Word in hell.  

Thankfully, Windows knows they suck so now you can run timeless Linux commands thru WSL - windows subsystem for Linux.

A quick Bing search will tell you to run "wsl --install."  DO NOT!

On my computer, this command got stuck at 0% for an hour.  

Instead, open the Windows Store and search "Linux."  You'll see something like Ubuntu 24.0.4 LTS - just choose the one with the highest number and the words LTS after it and click install.

On to the last step:

## Step 4: Building

First, move the EMBOSS-6.6.0 folder into your Linux folder. Linux is listed on the left hand sidebar of File Explorer, underneath "This PC" and "Network Drives".  Copy the EMBOSS-6.6.0 folder from your "C:\Users\yourusername" into "/home/yourusername".

Now open your Linux terminal.  You can do this by pressing the Windows menu and searching "Linux".

Run the following commands:

```sh
cd EMBOSS-6.6.0
sudo apt-get upgrade
sudo apt-get install gcc
sudo apt install make
cd EMBOSS-6.6.0
./configure --without-x
make
```

Make takes a while.  When it's done, test with the command:

```
embossversion
```

It should work!  If it doesn't, too bad.

And then set your PATH:

```
export PATH=home/yourusername/EMBOSS-6.6.0/emboss:$PATH

```

## Step 5: How come I can't just `sudo apt install emboss`?

I dunno.  Didn't work on my machine.  I could install gcc and make though.




