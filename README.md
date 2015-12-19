dwm - dynamic window manager
============================
dwm is an extremely fast, small, and dynamic window manager for X.


Requirements
------------
To build dwm you'll need the Xlib header files and suckless-tools.


Installation
------------
Edit config.mk to match your local setup (dwm is installed into
the /usr/local namespace by default).

Afterwards enter the following command to build and install dwm (if
necessary as root):

    make clean install

To get the fonts working, download the fonts from my dotfiles repo. Then add
these lines to your `.xinitrc` (replacing `${FONTDIR}` with the directory you
placed the fonts):

    xset +fp ${FONTDIR}
    xset fp rehash

You need to run `mkfontdir` and possibly `mkfontscale` in `${FONTDIR}` as well.


Running dwm
-----------
In order to set dwm as a login session, add a .desktop file for dwm to
`/usr/share/xsessions/`.

You can just run `dwm` to start dwm using startx, but I personally use a start
script (`dwm-start`) which starts some background processes I want, runs my
`.xinitrc`, and then starts dwm.

In order to display status info in the bar, you can do something
like this in your `.xinitrc`:

    while xsetroot -name "`date` `uptime | sed 's/.*,//'`"
    do
    	sleep 1
    done &
    exec dwm

Alternatively, use my statusbar by running it as a background process.

    exec dwm-statusbar &


Configuration
-------------
The configuration of dwm is done by creating a custom config.h
and (re)compiling the source code.
