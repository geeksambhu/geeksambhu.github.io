---
title: Today I Learned :)
layout: post
comments: true
permalink: "/til/"
description: I take my whole life as an apprenticeship and this is my journey each
  day
---

-------------------------------------------------------------------------------
## Here is my journey so far:
-------------------------------------------------------------------------------

####  Fri Aug 17 14:28:36 +0545 2018

How to stash untracked files in `git`?

`git stash -u` stash the untracked files in git without adding files to staging area
New versions of `git` now have `git stash --all` which stashes all files, including untracked and ignored files.
`git stash --include-untracked` no longer touches ignored files

###  Mon Aug 13 09:28:52 +0545 2018

What is the difference between `json.dump()` and `json.dumps()` in 
python?

`json.dump` takes file stream and will dump into a file stream while 
`json.dumps` takes string argument and often used for printing parsing 
etc. `json.dumps` == `dump string` :D

### Thu Aug  9  2018

Wrote a blog and a script to Organize Desktop and group similar files in a Directory
##### ``` echo '\n#### ' `date` ``` appends UNIX commands  `date` to string in shell  

How to check if a string endswith any of the elements from a list in python?
     
  > such list of string  must be `tuple`  for that purpose

```python

>>> photos_extension = ("jpg", "JPEG", "jpeg","png","HEIC","svg","JPG")
>>> file_name = "picofNepal.jpg"
>>> file_name.endswith(photos_extension)
True

```
-------------------------------------------------------------------------------

### Wed Jul 18  2018

> nginx HSTS error fixed updating the certificate

-------------------------------------------------------------------------------

### Mon Jul 16  2018

Built the script and alias it to `.zshrc` for daily logging

How to open `nano` at the end of the file?

> nano +9999 opens the file at end of file


> `about:about` opens custom url in both the browser in firefox and chrome

####  Fri Aug 17 14:28:36 +0545 2018
