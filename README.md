```CAPSed``` blocks mean configurable parameters in the beginning of scripts. Some scripts include ```LOG_PATH``` but no logging performed if ```LOG_PATH``` doesn't exist.

# Audio

## sync-lossy-library

**Requires**:

* OS X, Linux or Windows
* Python (tested on 2.7) with the following modules:
    * python-dateutil
    * [sergeyreznikov](https://github.com/sergeyreznikov/python-modules)
* MediaInfo (only if encoding is needed) at ```MEDIAINFO_FILE_PATH```
* Command-line encoder (only if encoding is needed) that is callable as ```ENCODE_COMMAND```. ```ENCODE_COMMAND``` can contain two self-explainable substitutions:
    * ```:lossless_file_path```
    * ```:lossy_file_path```

Copies (preserving directories) files ending with ```EXTENSIONS``` from ```LOSSLESS_PATH``` to ```LOSSY_PATH``` (if they don't already exist or their time modified changed, sizes will also be compared if files are not in a format that requires encoding) and removes files from ```LOSSY_PATH``` that don't exist in ```LOSSLESS_PATH```.  
Also converts files ending with ```EXTENSIONS``` (those ones that have a format specified next to its extension) using the specified encoder. For example: ```('m4a', 'ALAC')``` means the encoder will be called for \*.m4a files with a “ALAC format”

## sync-itunes-library

**Requires**:

* OS X 10.10
* osascript with JavaScript support.

Removes “dead” files from the iTunes library. Then adds \*.mp3 and \*.m4a files from ```LIBRARY_PATH``` to the iTunes library (if they don't already exist).

# Backup

## sync-dropbox-backup

**Requires**:

* OS X, Linux or Windows
* Python (tested on 2.7) with the following modules:
    * dropbox
    * python-dateutil
    * [sergeyreznikov](https://github.com/sergeyreznikov/python-modules)

Uploads files (preserving directories) from ```LOCAL_PATH``` to ```DROPBOX_PATH``` at Dropbox (if they don't already exist or their size/time modified/Dropbox revision changed) and removes files from ```DROPBOX_PATH``` at Dropbox that don't exist in ```LOCAL_PATH```.

Basically, it's a one-way sync “local files to Dropbox”.

Maintains its state in a SQLite 3 database placed in ```CACHE_PATH```. On OS X it reads a Dropbox OAuth 2 token from a system Keychain, on non-OS X systems it reads the token from a file at ```TOKEN_FILE_PATH``` with the following format:

```python
TOKEN="dropbox-oauth-token"
```

Optionally checks for a ```UNMOUNT_CHECK_PATH``` (relative to ```LOCAL_PATH```) existence (if ```UNMOUNT_CHECK_PATH``` is not empty) and immediately stops if it's not found.
