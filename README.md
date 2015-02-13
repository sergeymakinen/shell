*CAPSed* italics mean configurable parameters in the beginings of scripts. Some scripts include *LOG_PATH* but no logging performed if *LOG_PATH* doesn't exist.

# Audio

## sync-lossy-library

**Requires**: MediaInfo, XLD with a “Lossy” profile configured.

Copies (preserving directories) \*.mp3 and \*.m4a files from *LOSSLESS_PATH* to *LOSSY_PATH* (if they don't already exist or their size/date modified changed) and removes files from *LOSSY_PATH* that don't exist in *LOSSLESS_PATH*.  
Also converts ALAC *.m4a files to whatever specified in the XLD “Lossy” profile (I use AAC CVBR 256 kbps).

## sync-itunes-library

**Requires**: osascript with JavaScript support.

Removes “dead” files from the iTunes library. Then adds \*.mp3 and \*.m4a files from *LIBRARY_PATH* to the iTunes library (if they don't already exist).

# Backup

## sync-dropbox-backup

**Requires**: dropbox (*PIP*).

Uploads files from *LOCAL_PATH* to *DROPBOX_PATH* at Dropbox. Maintains its state in a SQLite 3 database placed in *CACHE_PATH*. On non-OS X systems reads Dropbox OAuth 2 token from *TOKEN\_FILE\_NAME* file.  
It's mostly experimental as it's not properly tested and it doesn't remove from Dropbox files that don't exist in the local directory.
