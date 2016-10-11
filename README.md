# pmbkp
Idea for a poor's man backup

Just think how much disk space is never used in an average workplace PC.
Times the number of workplace PCs at work.

You could be "wasting" an interesting amount of disk space. Said space could be used to backup, and that's the idea I want to explore.


Putting some flesh in the idea, there would be a central server (or more, but I will tackle just one just for the sake of simplicity), and there would be a lot of clients (most of them stable, some unstable).

Server:
------

Imagine a bittorrent client and an indexer, slapped together. The main services the server will provide are as follows:

+Add File:
  -encrypt file
  -split file (fixed n parts, %, other)
  -create torrent file for every file part
  -gather available clients
  -assign parts to clients (redundancy factor R)
  -deliver the torrent files to the selected clients
  -seed until there's at least s seeders
  -once the server stop seeding a part, delete it from server

+Recover File:
  -queue for download all the parts belonging to the file you want restored
  -wait untill all the parts are downloaded
  -reassemble the file and delete the parts
  -decrypt the file and place it "somewhere"
  -notify the user who requested the file that it's ready

+Delete File Backup:
  -Publish the parts that have to be deleted

+Update Free Space Available:
  -gather free space from every client

+Update Available Parts:
  -Do the index server already does it?


Client:
------

Almost a bare bittorrent client. Some extras, like getting local free space.

+Get Assignment:
  -Get torrent files assigned for downloading
  -Move the to the monitored folder
  -let the bittorrent client do its job

+Delete obsolete parts/files:
  -get list of parts/files to delete
  -delete file and associated torrent file (so it doesn't get downloaded again)

+Report Free Space:
  -get free space from disk
  -answer to server


