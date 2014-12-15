*CAPSed* italics mean configurable parameters in the beginings of scripts. Some scripts include *LOG_DIR* but no logging performed if *LOG_DIR* doesn't exist.

Audio
=====

sr-sync-lossy-library
---------------------

**Requires**: MediaInfo, XLD with a "Lossy" profile configured.

Copies (preserving directories) \*.mp3 and \*.m4a files from *LOSSLESS_DIR* to *LOSSY_DIR* (if they don't already exist or their size/date modified changed) and removes files from *LOSSY_DIR* that don't exist in *LOSSLESS_DIR*. Also converts ALAC *.m4a files to whatever specified in the XLD "Lossy" profile (I use AAC CVBR 256 kbps).

sr-sync-itunes-library
----------------------

**Requires**: osascript with JavaScript support.

Removes "dead" files from the iTunes library. Then adds \*.mp3 and \*.m4a files from *LIBRARY_DIR* to the iTunes library (if they don't already exist).
