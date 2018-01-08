volascripts.sh
==============

Those are bash scripts which are meant to interact with [Volafile](https://volafile.org) without
a need of using the browser.

Disclaimer
----------

`volaupload.sh` was originally made by [lain](https://github.com/laino) and Xiao. It seemed
to be abandoned so I enhanced it with agrument parsing and some other features.

volaupload.sh ver. 1.7
----------------------

This script allows you to upload files to [Volafile](https://volafile.org)
without using the browser. This is convenient, since it allows you to upload
files with different names without a need to rename them beforehand.
Use -h or --help command for full list of capabilities. Check insides of this script
for information on how to preset your room, nick and password.

stuff2vola.sh ver. 1.9
----------------------

Are you a fan of redundancy and don't want to post links to stuff in chat like a pleb?
Than this is a script for you. It will download most content from the web and upload it to
designeted Volafile room. Script can take multiple arguments just like volaupload.sh.
Script doesn't save downloaded files by default. If you want to keep downloaded files, please
specify download directory with the -d option.
Invoke script with -h or --help command to list other options.

volacrypt.sh ver. 1.2
---------------------

With this script you are able to upload and retrive files encrypted with symmetric AES256
algorithm. If you will supply the script with a file, it will encrypt it and upload to
a specified room. If you will specify valid volafile link, script will download and
decrypt it.

Prerequisites
------------

- bash >= 4.0
    * 4.3 version is needed if you want to have better upload bar in volaupload.sh
- coreutils
- [curl](https://curl.haxx.se/download.html) >= 7.33.0
- [youtube-dl](https://github.com/rg3/youtube-dl)
- [bc](https://www.gnu.org/software/bc/)
    * required for floating point arithmetics
- [ffmpeg](http://ffmpeg.org/download.html)
- [gpg](https://www.gnupg.org/download)
    * required for volacrypt.sh

### Optional:

- [curlbar](https://gist.github.com/Szero/cd496ca43df4b871df75818ebcc40233)
    * required for riced upload bar, install script will ask you if you want to install it
- [inotify-tools](https://github.com/rvoicilas/inotify-tools/wiki)
    * This one is needed just for --watch command in volaupload.sh script.
      Check the script source and decide if you find this usefull.

Installation & Updating
-----------------------

bash and coreutils packages are essential on most Linux distributions, so you should already have
them. All you need to do is to get `curl` and `ffmpeg` with your distribution's package manager.
(`ffmpeg` is needed because sometimes to get best audio and video, `youtube-dl` will download
separate streams and mux them together with `ffmpeg`)
[youtube-dl](https://github.com/rg3/youtube-dl) and
[curlbar](https://gist.github.com/Szero/cd496ca43df4b871df75818ebcc40233) will be
installed with install script if you don't have them already.

To install on all UNIX-like systems for current user (into `~/.local/bin` directory) type:

    bash <(curl -sLo- https://rawgit.com/Szero/volascripts.sh/master/install.sh)

To install on all UNIX-like systems for all users (into `/usr/local/bin` directory) type:

    sudo bash -c 'bash <(curl -sLo- https://rawgit.com/Szero/volascripts.sh/master/install.sh)'

Restart your terminal to finalize installation process.
Install script is responsible both for updating and installing so you are good with running it
whenever I release new updates.

Configuration
-------------

You can create `.volascriptsrc` file in your `$HOME` directory to preset some options you may not
want to specify every time you upload something. Possible values to set:

```bash
# Room you want to upload by default.
ROOM="HF33Go"
# Your nick and password if you want to upload as logged user so
# uploads counts toward your profile statistics.
NICK="somedude"
PASSWORD="somepass"
# Room aliases in a form of bash array for setting memorable names for chosen rooms
ROOM_ALIASES=(
"plebeians=HF33Go"
"patricians=BEEPi"
)
# If you will set this options, all the files downloaded by stuff2vola.sh script will be saved
# in the specified directory.
VID_DIR="/home/dude/weed"
```

Example usage
-------------

    volaupload.sh -r BEEPi -n Monkey ~/Pictures/wild_nigra.jpg -a "merc - approximation"

    stuff2vola.sh -r HF33Go -a "oy vey" https://jewtube.com/watch?v=SH4L0M

Contributing
------------

Just hit me with that sweet issue ticket or pull-request.
