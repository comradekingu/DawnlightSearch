__This page is under construction...__
__some parts are out of date__

# DawnlightSearch

A Linux version of [Everything Search Engine](https://www.voidtools.com/). Show instant results as you type.

__The app is still under development and not stable. Comments and pull requests are very appreciated.__

[![Build Status](https://travis-ci.org/chg-hou/DawnlightSearch.svg?branch=c%2B%2B-version)](https://travis-ci.org/chg-hou/DawnlightSearch)

## Similar Everything-like Search Engine in Linux: 

(Ordered by first commit date)

| Name | Language | GUI | Database | 
|-|-|-|-|
|[ANGRYsearch](https://github.com/DoTheEvo/ANGRYsearch) | Python3 | PyQt5 | SQLite3 |
|[fsearch](https://github.com/cboxdoerfer/fsearch) | C | GTK+3 | (built-in) |
|[DawnlightSearch (old)](https://github.com/chg-hou/DawnlightSearch/tree/master) | Python3 | PyQt5 | SQLite3 |
|[DawnlightSearch (this)](https://github.com/chg-hou/DawnlightSearch) | C++ | Qt5 | SQLite3 |


## Test environment:

 - Ubuntu 16.04 / 18.04

## Highlights:

 - Instant search.
 - Support **wildcards** and **regular expressions**.
 - Support filter on multi fileds: file name, folder, full path, size, mtime, ctime, and atime. 
  - ~~Quick file indexing for NTFS partition by parsing master file table (MFT).~~ (This feature is available in the old python version. I will put it back soon. )
  - Customizable **dock widget** design.
  - **Multi-threaded** search. 

Video demo: [https://youtu.be/949Jm9j4sP4](https://youtu.be/949Jm9j4sP4)

![](./_screenshot/Dawnlight%20Search_c++.png)

![](./_screenshot/Dawnlight%20Search_2.png)

--------------------------------

### Interface:

#### Database:

Partitions of differenct UUIDs will be stored seperatedly in the database. In circumstances where duplicate UUIDs exist, they will be treated as a single one and records will be overwritten. 

![](./_screenshot/Database_table_1.png)

1. Whether search this partition. **You need to check it to search the corresponding partition.** Icon indicates the mount state.

2. Can be changed into any name you want. Will display in front of the path when partition unmounted.

3. Whether update this partition when “*Update DB*” clicked. You can always update a partition using the context menu, regardless of the checked state.


#### Menubar:

![](./_screenshot/Main_menu.png)

1. Edit excluded paths when indexing. Only full path is supported right now. Note: MFT parser will disregard this option.

2. Check this option to use MFT parser to speed up building index on an NTFS partition (like other MFT based searcher). 

3. Check to use the C++ MFT parser instead of the Python one. The C++ one is supposed to be much faster.


#### Search Syntax:


  Logical Operators   |  Description 
-------- | ---
&#160;  *space* | AND
 &#124; *vertical bar*   | OR
!   *exclamation mark* | NOT


  Wildcards   |  Description 
-------- | ---
&#160;  *space* | AND
 &#124; *vertical bar*   | OR
!   *exclamation mark* | NOT



Note: global "nocase" settings has no effect on regular expression. Use "(?i)" instead. 
Examples: 

***reg:"a"*** will match "123abcd", not "123Abcd". 

***reg:"A"*** will match "123Abcd", not "123abcd". 

***reg:"(?i)A"*** will match both "123Abcd" and "123abcd".


### Installation:

* Ubuntu 16.04:
> ppa: [https://launchpad.net/~chg-hou/+archive/ubuntu/dawnlightsearch](https://launchpad.net/~chg-hou/+archive/ubuntu/dawnlightsearch)

 > $ sudo add-apt-repository ppa:chg-hou/dawnlightsearch

 > $ sudo apt-get update

 > $ sudo apt-get install python3-dawnlightsearch 

* Others:

  Dependences:  

 - Qt5

 - kio-dev
 
### TODO:
 - Auto indexing.
 - Monitor file system changes.
 - Index files in archives.
 - More language options.
 - Support Windows.

### FIXME:
 - Wrong working path in .desktop (ubuntu 14.04)
 - Wrong location of extracted .desktop (  ? use    data_files=[('/usr/share/applications',...)]  ) 

## Similar Projects:

 - [ANGRYsearch](https://github.com/DoTheEvo/ANGRYsearch) (python)
 - [FSearch](https://github.com/cboxdoerfer/fsearch)


