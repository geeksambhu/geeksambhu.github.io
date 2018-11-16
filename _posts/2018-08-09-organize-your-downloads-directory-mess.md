---
title: Organize your Downloads Directory
layout: post
image_url: "/assets/images/file_management.jpg"
tags:
- Python,  Automation
category: Python
description: Organize and improve your Download directory using python programmatically.
---

### Organize the Mess in your Download Directory with this Simple Python Script

These days we all use the internet a lot and download multiples files which are messily arranged in our Downloads directory.
So, I thought to write a simple script that manages all the files that are downloaded and arranges the file according to their types.

For example, 
- all the images file moved into a single folder named  **Photos**

- All the  scripts file like `.py`,`.sh`  into a  directory named **Scripts**

and so on

![File](/assets/images/file_management.jpg)

To get rid of unorganized files in Download or other Directory I wrote this Script which organizes the file according to their types and move them to clear the cluster in your Download Directory

``` python
import os,shutil, datetime as dt
import sys
result_dict = {}

download_dir=sys.argv[1]
photos_extension = ("jpg", "JPEG", "jpeg","png","HEIC","svg","JPG")
videos_extension = ("mp4", "ovi")
scripts_extension = ("py","sh","txt","md")
book_extension = ("pdf","mobi","epub","PDF")
doc_extension = ("doc","docx","xlsx","csv","odt")
archive_extension = ("gz", "zip","deb")
pak_extension = ("pak")
for each in os.listdir(download_dir):
    if os.path.isfile(download_dir + each):
        file_src = str(download_dir+each)
        if file_src.endswith(photos_extension):
            result_dict.setdefault("Photos", []).append(each)
        if file_src.endswith(videos_extension):
            result_dict.setdefault("Videos",  []).append(each)
        if file_src.endswith(scripts_extension):
            result_dict.setdefault("Scripts",  []).append(each)
        if file_src.endswith(book_extension):
            result_dict.setdefault("Book", []).append(each)
        if file_src.endswith(doc_extension):
            result_dict.setdefault("Docs", []).append(each)
        if file_src.endswith(archive_extension):
            result_dict.setdefault("Archives", []).append(each)
        if file_src.endswith(pak_extension):
            result_dict.setdefault("PakFiles", []).append(each)
print(result_dict)

for key in result_dict:
    new_dir = download_dir+key+'/'
    os.makedirs(new_dir, exist_ok=True)
    [shutil.move(download_dir+each, new_dir+each) for each in result_dict[key]]

```

To use this **Script** Please run it with python3:

1. >  Copy the above codeblock and paste it into a file named `clean_directory.py`
2. > Run this file using `$ python clean_directory.py <Your Directory>` for eg: `$ python clean_directory.py /Users/shiva/Desktop/`, This code is **Python3** Compatible & mind the `/` at the last of Directory in Command line arguments

Voila, Your directory mess is now arranged and Organized Perfectly, Enjoy and leave a comment if you liked my work