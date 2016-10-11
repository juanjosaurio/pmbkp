# pmbkp
Idea for a poor's man backup

Just think how much disk space is never used in an average workplace PC.
Times the number of workplace PCs at work.

You could be "wasting" an interesting amount of disk space. Said space could be used to backup, and that's the idea I want to explore.


Putting some flesh in the idea, there would be a central server (or more, but I will tackle just one just for the sake of simplicity), and there would be a lot of clients (most of them stable, some unstable).

## Server

Imagine a bittorrent client and an indexer, slapped together. The main services the server will provide are as follows:

+ Add File:
  1. encrypt file
  2. split file (fixed n parts, %, other)
  3. create torrent file for every file part
  4. gather available clients
  5. assign parts to clients (redundancy factor R)
  6. deliver the torrent files to the selected clients
  7. seed until there's at least s seeders
  8. once the server stop seeding a part, delete it from server

+ Recover File:
  1. queue for download all the parts belonging to the file you want restored
  2. wait untill all the parts are downloaded
  3. reassemble the file and delete the parts
  4. decrypt the file and place it "somewhere"
  5. notify the user who requested the file that it's ready

+ Delete File Backup:
  1. Publish the parts that have to be deleted

+ Update Free Space Available:
  1. gather free space from every client

+ Update Available Parts:
  1. Do the index server already does it?


## Client

Almost a bare bittorrent client. Some extras, like getting local free space.

+ Get Assignment:
  1. Get torrent files assigned for downloading
  2. Move the to the monitored folder
  3. let the bittorrent client do its job

+ Delete obsolete parts/files:
  1. get list of parts/files to delete
  2. delete file and associated torrent file (so it doesn't get downloaded again)

+ Report Free Space:
  1. get free space from disk
  2. answer to server


