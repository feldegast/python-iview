Python command-line and GTK+ interface to ABC iView
Copyright (C) 2009-2010 by Jeremy Visser <jeremy@visser.name>

This program is free software: you can redistribute it and/or modify
it under the terms of the GNU General Public License as published by
the Free Software Foundation, either version 3 of the License, or
(at your option) any later version.

This program is distributed in the hope that it will be useful,
but WITHOUT ANY WARRANTY; without even the implied warranty of
MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the
GNU General Public License for more details.

You should have received a copy of the GNU General Public License
along with this program.  If not, see <http://www.gnu.org/licenses/>.

Warning
=======

This version includes a workaround which may mean the downloads are actually
metered even if they are supposed to be unmetered. The following warning is
printed on the terminal when this happens:

	http://iviewum-vh.akamaihd.net/z/: Not an RTMP server
	Using fallback from config (possibly metered)

Requirements
============

* Python 3.0-3.3 or 2.6-2.7 <http://www.python.org/>. Python 2 recommended
   for the GTK GUI.
* rtmpdump <http://lkcl.net/rtmp/>
* socksipy <http://socksipy.sourceforge.net/> (Only for SOCKS proxy)
* GTK (Only for the GUI). Py GTK <http://pygtk.org/> is recommended, but does
   does not appear to be ported to Python 3. The alternative is Py G Object
   with GTK 2, but this does not always work.

Installation
============

1. Make sure Python is installed and working.
2. Install rtmpdump. If building from source, copy rtmpdump_x86 to
   somewhere within your $PATH (e.g. /usr/local/bin).
3. Either run ./iview-cli or ./iview-gtk.

Usage
=====

Some usage examples are provided for your perusal.

This is a purely informational command, and verifies that handshaking is
working correctly.

	$ ./iview-cli --print-auth
	iView auth data:
		Token: XXXXXXXXXXXXXXXXXXXX
		RTMP URL: rtmp://203.18.195.10/ondemand
		Unmetered: True

This can be used to view the iView programme and find the program URL:

	$ ./iview-cli --programme
	7.30 Report:
	    7.30 Report 12/01/10	(news/730report_100112.flv)
	    7.30 Report 11/01/10	(news/730report_100111.flv)
	    7.30 Report 07/01/10	(news/730report_100107.flv)
	    7.30 Report 06/01/10	(news/730report_100106.flv)
	[...]

To actually download the program, use something like the following:

	$ ./iview-cli --download news/730report_100112.flv

If rtmpdump is all set up correctly, hopefully that will download
an .flv file into your current directory, appropriately named. If it
didn't work, type "rtmpdump" or "rtmpdump_x86" and see if it does anything.
If not, install it, or put it somewhere on your $PATH.

Hacking
=======

Uh...good luck.

There are a few variables that can be edited in the "config.py" file.

:wq
