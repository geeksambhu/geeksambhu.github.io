---
title: Today I Learned :)
layout: post
comments: true
permalink: "/til/"
description: |-
  I take my whole life as an apprenticeship and this is my journey each day.
  In short: git stash untracked files, json.dump() and json.dumps python, Fix HSTS error, remotely execute script via ssh,
---

-------------------------------------------------------------------------------
## Here is my journey so far:
-------------------------------------------------------------------------------

###  Fri Aug 17 14:28:36 +0545 2018

#### How to stash untracked files in `git`?

`git stash -u` stash the untracked files in git without adding files to staging area
New versions of `git` now have `git stash --all` which stashes all files, including untracked and ignored files.
`git stash --include-untracked` no longer touches ignored files

###  Mon Aug 13 09:28:52 +0545 2018

#### What is the difference between `json.dump()` and `json.dumps()` in 
python?

`json.dump` takes file stream and will dump into a file stream while 
`json.dumps` takes string argument and often used for printing parsing 
etc. `json.dumps` == `dump string` :D

### Thu Aug  9  2018

Wrote a blog and a script to Organize Desktop and group similar files in a Directory

  ``` echo '\n#### ' `date` ``` appends UNIX commands  `date` to string in shell  

#### How to check if a string endswith any of the elements from a list in python?
     
  > such list of string  must be `tuple`  for that purpose

```python

>>> photos_extension = ("jpg", "JPEG", "jpeg","png","HEIC","svg","JPG")
>>> file_name = "picofNepal.jpg"
>>> file_name.endswith(photos_extension)
True

```
-------------------------------------------------------------------------------

### Wed Jul 18  2018

#### How to fix nginx HSTS error? 
 
    I fixed by updating the certificate

-------------------------------------------------------------------------------

### Mon Jul 16  2018

Built the script and alias it to `.zshrc` for daily logging

How to open `nano` at the end of the file?

> nano +9999 opens the file at end of file


> `about:about` opens custom url in both the browser in firefox and chrome


### Tue Oct 2 13:54:14 +0545 2018

#### How to redirect to `https` from `http` using Flask `url_for()` ?

> Since Flask `url_for` does not respect `http` or `https` while redirecting, always use `redirect(url_for('func_name', _external=True))` to respect the root `URL` and 
Scheme(`http` or `https`) Used

###  Wed Oct 3 17:01:09 +0545 2018

#### How to remotely execute remote bash script in remote machine from local machine?

>  To remotely execute a script residing in remote machine, do this:

`ssh username@host.address './remotescript.sh'`

On doing so remote script is executed however node module are not found and executed hence to execute the npm tools like `pm2` follow the following steps:

1. Type the following commands in your remote machine:" `echo $PATH`"
        It will output results like below:
"``/home/ubuntu/bin:/home/ubuntu/.local/bin:/home/ubuntu/.nvm/versions/node/v8.9.4/bin:/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games:/usr/local/games:/sn$``"

2. Copy the above output and open the file with texteditor like `nano remotescript.sh`  and add the new line at the start of file. The new line must be like :
"`export PATH='{step 1 Output}'`"
remember that the `{step 1 Output}` looks like this `/home/ubuntu/bin:/home/ubuntu/.local/bin:/home/ubuntu/.nvm/versions/node/v8.9.4/bin:/usr/local/sbin:/usr/local/bin:/usr/sbin$`

3. Now save and close the file and execute your remote file like below:
                
    `ssh username@host.address './remotescript.sh'` 

CONGRATS!!!, You just ran your remote script in remote machine from local machine: let me know if any problem occurs :)


###  Wed Oct 3 17:01:09 +0545 2018

#### How to find the length of a `set` in `javascript`?

> Use `set_variable.size` like below:

    var setTempVariable = new Set([1,2,3,4])
    console.log(setTempVariable.size) // Outputs 4


###  Tue Oct 23 17:02:53 +0545 2018

#### How to use or operator in regex to match either group?

> I had a use case to match either a number or a fixed string which I did by 
using following regex:
       
      `((^[0-9]+$)|FIXED$)`

Using `+` and `$` helped me to exact match either of the group i.e number or 
'FIXED' string. + looks for 0 or 1 repetition while $ matched the end of string

###  Sun Feb 3 23:59:31 +0545 2019

#### Simple Mail server for debugging in python
 
  ```python -m smtpd -c DebuggingServer -n <source_address>:<port>```

If default `mailserver` will be enable in port `localhost:8025`, Anything sent to this address and port will be sent in STDOUT
  
Happy Email debugging Folks:

```bash
telnet localhost 25
Trying 127.0.0.1...
Connected to localhost.
Escape character is '^]'.
220 Shivas-Macbook.local Python SMTP proxy version 0.2
helo localhost #To connect
250 Shivas-Macbook.local
mail from: username@mymail.com # From
250 Ok
rcpt to: shivaji@@mymail.com #receipent
250 Ok
data #data to send message
354 End data with <CR><LF>.<CR><LF>
Subject: Hello
Hello,
This is sample test
Me
.
```
End telnet with a `.` at the end

In STDOUT after sending message from `telnet`
:

```bash
python -m smtpd -c DebuggingServer -n

---------- MESSAGE FOLLOWS ----------
Subject: Hello
Hello,
This is sample test
Me
------------ END MESSAGE ------------
```
 


###  Thu May 16 10:32:44 +0545 2019

### How to create wheel from setup.py?

run ``python setup.py wheel`` inside the package root

### Download wheel or source from `pip` Python packages
``pip download -r requirements.txt --prefer-binary`` to download `whl` file.
` pip download -r requirements.txt --no-binary :all:` to download source file, `.gz` or `.zip`