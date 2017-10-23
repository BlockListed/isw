# isw / Ice-Sealed Wyvern
Warning
-------
isw was made for MSI GS40 6QE, please verify that your EC work the same way before trying.
You can find documentation at: NA
isw was only tested under Arch/systemd.
Use it at your own risk !

Purpose
-------
isw was made as an equivalent of "control tools by pherein" but under linux.

In details
----------
Replace value at ADDRESS,ADDRESS+1,...,ADDRESS+5.
The ADDRESS value will be replaced by VALUE and following one incremented by X (from VALUE).
VALUE correspond to °C.
X is the increment for VALUE.
In Short: Fan will start spinning at VALUE and increase speed every X °C.
NB: EC contain 7 values, only 6 of them are edited, last value is unchanged (100°C).

How to use it ?
---------------
It's just a python script to launch with wanted options, you can have a list with:
'''
./isw.py -h
'''
It will need ec_sys module so you should use '''isw -l''' or '''isw -ls''' to load it (read below)

isw -s
------
Add the following for ec_sys to load at startup:
"ec_sys" > /etc/modules-load.d/isw-ec_sys.conf
"options ec_sys write_support=1" > /etc/modprobe.d/isw-ec_sys.conf

isw -l
------
Load ec_sys directly with:
modprobe ec_sys write_support=1

isw -c
------
Check your EC with:
od -t x1 /sys/kernel/debug/ec/ec0/io

TODO
----
Daemonisation ?
	Launch at startup
	Launch at event(power source change)