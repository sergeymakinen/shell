*CAPSed* italics mean configurable parameters in the beginings of scripts. Some scripts include *LOG_PATH* but no logging performed if *LOG_PATH* doesn't exist.

# Audio

## sync-lossy-library

**Requires**: MediaInfo, XLD with a “Lossy” profile configured.

Copies (preserving directories) \*.mp3 and \*.m4a files from *LOSSLESS_PATH* to *LOSSY_PATH* (if they don't already exist or their size/time modified changed) and removes files from *LOSSY_PATH* that don't exist in *LOSSLESS_PATH*.  
Also converts ALAC *.m4a files to whatever specified in the XLD “Lossy” profile (I use AAC CVBR 256 kbps).

## sync-itunes-library

**Requires**: osascript with JavaScript support.

Removes “dead” files from the iTunes library. Then adds \*.mp3 and \*.m4a files from *LIBRARY_PATH* to the iTunes library (if they don't already exist).

# Backup

## sync-dropbox-backup

**Requires**: dropbox (*PIP*).

Uploads files (preserving directories) from *LOCAL_PATH* to *DROPBOX_PATH* at Dropbox (if they don't already exist or their size/time modified/Dropbox revision changed) and removes files from *LOCAL_PATH* that don't exist in *DROPBOX_PATH* at Dropbox.

Maintains its state in a SQLite 3 database placed in *CACHE_PATH*. On OS X it reads a Dropbox OAuth 2 token from a system Keychain, on non-OS X systems it reads the token from file located at *TOKEN\_FILE\_PATH* with the following format:

```bash
TOKEN="dropbox-oauth-token"
```

This script is mostly experimental as it's not extensively tested.
