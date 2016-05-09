```CAPSed``` blocks mean configurable parameters (see ```*.sample.ini```).

# Audio

## sync-lossy-library

**Requires**:

* OS X, Linux or Windows
* Python 3 (tested on [PyPy](http://pypy.org) 2.4.0) with the following modules:
    * [sergeymakinen](https://github.com/sergeymakinen/python-modules)
* MediaInfo (only if encoding is needed) at ```MEDIAINFO_FILE_PATH```
* Command-line encoder (only if encoding is needed) that is callable as ```ENCODE_COMMAND```. ```ENCODE_COMMAND``` can contain two self-explainable substitutions:
    * ```:lossless_file_path```
    * ```:lossy_file_path```

Copies (preserving directories) files ending with ```EXTENSIONS``` from ```LOSSLESS_PATH``` to ```LOSSY_PATH``` (if they don't already exist or their time modified changed, sizes will also be compared if files are not in a format that requires encoding) and removes files from ```LOSSY_PATH``` that don't exist in ```LOSSLESS_PATH```.  
Also converts files ending with ```EXTENSIONS``` (those ones that have a format specified next to its extension) using the specified encoder. For example: ```m4a, ALAC``` means the encoder will be called for \*.m4a files with a “ALAC format”

## sync-itunes-library

**Requires**:

* OS X 10.10 or higher
* osascript with JavaScript support
* Python 3 (tested on [PyPy](http://pypy.org) 2.4.0) with the following modules:
    * [sergeymakinen](https://github.com/sergeymakinen/python-modules)

Removes “dead” files from the iTunes library. Then adds \*.mp3 and \*.m4a files from ```LIBRARY_PATH``` to the iTunes library (if they don't already exist).
