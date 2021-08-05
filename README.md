# -Asterisk
How to enable video calling in Asterisk

These codecs do not need to be installed, they are already included in Asterisk by default, however, if you do not, follow the instructions below with the necessary changes.

1- Install Asterisk PABX software

2- If the video call option is not enabled in the GUI, the options area displays one of the h261, h263, h263p, h264 or mpeg4 video compression standards, you will need to make changes or add a file to the folder. .conf and one more in extension.conf

3- Making changes to the .conf file

3.1 - open terminal and enter root path vi /etc/asterisk/sip.conf, if vi doesn't work try vim, this command will open this folder in preview mode and press Enter to access the folder

3.2- enter i to enable insertion, if no file, add below text at the end of the documentation by clicking the down arrow

context = default
bindaddr = 0.0.0.0
allow = ulaw
allow = alaw
allow = ilbc
allow = h263
allow = h263
allow = h263p
allow = h264
allow = mpeg4
videosupport = yes
textupport = yes
McCallbitrate = 384

[1000]
type = friend
callerid = "test" <1000>
username = 1000
secret = 1000
host = dynamic
nat = yes
canreinvite = no
context = internal
qualify = yes
allow = all
videosupport = yes

[1001]
type = friend
callerid = "test" <1001>
username = 1001
secret = 1001
host = dynamic
nat = yes
canreinvite = no
context = internal
qualify = yes
allow = all
videosupport = yes

Then type esc and type: qw to exit and save changes: w to save: q! to exit without saving changes and just: q to exit

3.3- after entering vi /etc/asterisk/extensions.conf to access

3.4- Down arrow or page down key to add the file below at the end of the code.

[interior]
exten => 1000.1, dial (SIP / 1000.25)
exten => 1000.2, Hang

[interior]
exten => 1002.1, dial (SIP / 1002.25)
exten => 1002.2, Hang

4} After typing service asterisk restart and restarting, the configuration programs will be added to the interface.
