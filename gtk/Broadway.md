GTK+3 with the Broadway (HTML5) backend

ADDING THIS PPA TO YOUR SYSTEM
==============================

Run these commands in a terminal:

```shell
sudo add-apt-repository ppa:malizor/gtk-broadway
sudo apt-get update
sudo apt-get upgrade
sudo apt-get install broadwayd # For Ubuntu >= 13.10
```

error
```output
The following packages have unmet dependencies:
 broadwayd : Depends: libgtk-3-common (= 3.10.8-0ubuntu1.5+broadway1) but 3.10.8-0ubuntu1.6 is to be installed
```

```shell
sudo apt-get install libgtk-3-common=3.10.8-0ubuntu1.5+broadway1 --reinstall
```

HOWTO SINCE SAUCY (gtk+ >= 3.8)
===============================

As an example, here is how to run gedit in your browser.

In a terminal, run:
```shell
broadwayd
```

In another terminal, run:
```shell
GDK_BACKEND=broadway UBUNTU_MENUPROXY= LIBOVERLAY_SCROLLBAR=0 gedit
```

Finally, open you Web browser and go to http://localhost:8080/

The "UBUNTU_MENUPROXY= LIBOVERLAY_SCROLLBAR=0" is only useful if you use the global-menu and/or overlay-scrollbars. You have to disable them for Broadway, otherwise the program will segfault.

Please see the "broadwayd" manpage for more information.

HOWTO BEFORE SAUCY (gtk+ < 3.8)

Running LibreOffice in server mode
==================================
```shell
export SAL_USE_VCLPLUGIN=gtk3
export GDK_BACKEND=broadway
/usr/bin/soffice -writer
```