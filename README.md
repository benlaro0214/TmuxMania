 
              
## TMUX Mania

A collection of shellscripts to use with TMUX in order to create minimalistic TUI, without re-inventing the wheel. You can use this with your favorite Linux and MacOS CLI apps. The scripts are coded to be self-explanatory. 
 
## Dependencies

* tmux 
* CLI                  
* your apps.  
                    

## TMUX cheatsheet

Sessions
---------

Start a new Session:

tmux

Start a new session with a name:

tmux new -s [name]

Start an attached session:

tmux a #

If the Tmux session has a name:

tmux attach -t [name]

List all Tmux sessions:

tmux ls

Exit the utility:

exit

Kill session:

tmux kill-session -t [name]

Window Handling
----------------

New window	<prefix>+c

Next window	<prefix>+n

List all windows	<prefix>+w

Rename a window	<prefix>+,

Previous window	<prefix>+p

Find a window	<prefix>+f

Kill a window	<prefix>+&

Pane Handling
----------------
Split panes vertically	<prefix>+%

Split panes horizontally	<prefix>+“

Toggle last active plane	<prefix>+;

Swap panes	<prefix>+o

Kill pane	<prefix>+x

Show pane numbers	<prefix>+q

Move plan left	<prefix>+{

Move plan right	<prefix>+}

Switching between panes	<prefix>+arrow key

##

1 - The Friday night companion (Tmux + Links2+ Weechat + CMUS)

FRIDAY NIGHT COMPANION
---------------

For those wanting a chill Friday night and take a break from Netlfix binging, the savvy combination of a light browser, chat client and music player will fit the bill.

Throw in a few snacks and you can spend the night chatting up a storm in the old IRC networks.


LAYOUT
-------


 ---------------------------------
 |               |               |
 |               |               |
 |               |               |
 |      1        |               |
 |               |               |
 |               |               |
 |---------------+         3     |
 |               |               |
 |               |               |
 |      2        |               |
 |               |               |
 |               |               |
 |               |               |
 ---------------------------------


|  1.             | 2.      |
|-|-|
| 3  | 4 |




APPS:

1) Links2 

2) Weechat

3) Cmus

HOW TO INSTALL SOFTWARE
-----------------------

Debian/Ubuntu/Mint/Raspbian
----------------------------

apt install cmus links2 weechat


And if using a *.deb file;

sudo dpkg -i app_name.deb


Centos/RedHat
-------------

yum install cmus links2 weechat

And if using an *.rpm file

sudo rpm -i app_name.rpm


Archlinux
----------

sudo pacman -S links2 weechat cmus




Script (With TMUX!!)
-----------

#!/bin/bash
    SN="Layout"
    tmux has-session -t $SN &>/dev/null
    if [ $? != 0 ]
    then
        tmux new -s $SN -n conf -d
        tmux new-window -t $SN:2 -n misc
        tmux select-window -t $SN:1
        tmux send-keys "links2 www.google.ca" C-m
        tmux split-window -h -p 50 # split vertically by 50%
        tmux send-keys "weechat" C-m
        tmux select-pane -t 0
        tmux split-window -v -p 50
        tmux send-keys "cmus" C-m
        fi
        tmux -2 attach -t $SN


2 - The Jukebox (Alsamixer + CMUS + cava )

The JukeBox
---------------

Turn an old pc into a music management system with a visualizer. Pop in your favorite MP3's and hook it up to your old stereo and have some cool tunes with a nice retro gui.


LAYOUT
-------

#---------------------------------
#|                               |
#|                               |
#|                               |
#|              1                |
#|                               |
#|                               |
#|-------------------------------|
#|              |                |
#|              |                |
#|      2       |       3        |
#|              |                |
#|              |                |
#|              |                |
#---------------------------------

APPS:

1) cmus

2) Alsamixer

3) Cava

HOW TO INSTALL SOFTWARE
-----------------------

Debian/Ubuntu/Mint/Raspbian
----------------------------

apt install alsamixer cava cmus


And if using a *.deb file;

sudo dpkg -i app_name.deb


Centos/RedHat
-------------

yum install alsamixer cava cmus

And if using an *.rpm file

sudo rpm -i app_name.rpm


Archlinux
----------

sudo pacman -S alsamixer cava cmus




TMUX SCRIPT
-----------

#!/bin/bash
    SN="Layout1"
    tmux has-session -t $SN &>/dev/null
    if [ $? != 0 ]
    then
        tmux new -s $SN -n conf -d
        tmux new-window -t $SN:2 -n misc
        tmux select-window -t $SN:1
        tmux send-keys "cmus" C-m
        tmux split-window -v -p 40 # split vertically by 60%
        tmux send-keys "alsamixer" C-m
        tmux split-window -h -p 50 # split horizontal by 50%
        tmux send-keys "cava" C-m
        tmux select-pane -t 0
        fi
        tmux -2 attach -t $SN



The Internet Radio
---------------

Similar to the jukebox, the internet radio recycles an old pc into a source of listening pleasure. Rather than soundfiles (such as mp3's and ogg's), it relies on the old shoutcast and icecast feeds.

LAYOUT
-------

#---------------------------------
#|                               |
#|                               |
#|                               |
#|              1                |
#|                               |
#|                               |
#|-------------------------------|
#|              |                |
#|              |                |
#|      2       |       3        |
#|              |                |
#|              |                |
#|              |                |
#---------------------------------


APPS:

1) links2

2) cmus

3) alsamixer

HOW TO INSTALL SOFTWARE
-----------------------

Debian/Ubuntu/Mint/Raspbian
----------------------------

apt install links2 cmus alsamixer


And if using a *.deb file;

sudo dpkg -i app_name.deb


Centos/RedHat
-------------

yum install links2 cmus alsamixer

And if using an *.rpm file

sudo rpm -i app_name.rpm


Archlinux
----------

sudo pacman -S alsamixer cmus links2




TMUX SCRIPT
-----------

#!/bin/bash


    SN="Layout1"
    tmux has-session -t $SN &>/dev/null
    if [ $? != 0 ]
    then
        tmux new -s $SN -n conf -d
        tmux new-window -t $SN:2 -n misc
        tmux select-window -t $SN:1
        tmux send-keys "links2 dir.xiph.org" C-m
        tmux split-window -v -p 50 # split vertically by 50%
        tmux send-keys "cmus" C-m
        tmux split-window -h -p 50 # split horizontal by 50%
        tmux send-keys "alsamixer" C-m
        tmux select-pane -t 0
        fi
        tmux -2 attach -t $SN


*NOTE: Some extra configuration is required with links2. Here's what you do;

1) Open in a text editor the links2 config file (found here:) 
2) find this line
3) Add this code; **INSERT CODE HERE**

This will set m3u, xlpf and ogg's mount points to open cmus as a default.

                    
       
## Licensing

GNU [![License: GPL v3](https://img.shields.io/badge/License-GPLv3-blue.svg)](https://www.gnu.org/licenses/gpl-3.0) 
                    
## Resources:


* Bootstrap (Components):  https://getbootstrap.com/
* Programmable web: https://www.programmableweb.com/
* freeCodeCamp: https://www.freecodecamp.org/
* MDN web docs moz://a: https://developer.mozilla.org/en-US/
* stack overflow: https://stackoverflow.com/
* w3schools: https://www.w3schools.com/
* Hackaday: https://www.hackaday.com
 