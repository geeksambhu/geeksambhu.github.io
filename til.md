---
title: Today I Learned
layout: post
comments: true
permalink: "/til/"
description: A part of my day to day learning
metadescription: Collection of solution to common programming and technical problems
  and also tips and tricks on Python, JavaScript, bash, command line and everything
  I learnt
metatitle: Today I Learned- Collection of programming tips and tricks
metatags: today i learned,  til,  python,  javascript,  command line,  bash, tips,
  tricks
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

###  Wed Aug 28 09:28:39 +0545 2019

### How to exclude files and folders when compressing using `tar`?

Use `--exclude` as many times you like to exclude files and folders.


```bash 
 cd <directory> #DIrectory in which you want to compress the files and folders
 tar --exclude='./node_modules' --exclude='.excluding_folder_name' --exclude='./test.py' --exclude='./env' -czvf excluded.tar.gz .
```
###  Mon Nov 11  16:49:56 +0545 2019

### Removing Sensitive information from git

```bash
  git filter-branch --force --index-filter \
  "git rm --cached --ignore-unmatch -r <FILE_NAME_OR_FOLDER_IF_FOLDER_-r_AS_ARGS>" --prune-empty --tag-name-filter cat -- --all
```

This will Force Git to process, but not check out, the entire history of every branch and tag, Remove the specified file, as well as any empty commits generated as a 
result, Add file or folder to `.gitignore` once removed to ensure you won't commit again 

###  Wed Jan 22 13:26:47 +0545 2020

### Solve CORS issue in Flask API call
Do this in your response `@app.after_request` decorator

```python
@app.after_request
def add_headers(response):
    white_list_url= ['https://yourserverorigin.com/','http://localhost:8000'] #List of URLs you want to allow
    if request.headers['Origin'] in white_list_url:
        response.headers.add('Content-Type', 'application/json')
        response.headers.add('Access-Control-Allow-Origin', request.headers['Origin'] )
        response.headers.add('Access-Control-Allow-Methods', 'GET')
        response.headers.add('Access-Control-Allow-Headers', 'Content-Type,Authorization')
        response.headers.add('Access-Control-Expose-Headers', 'Content-Type,Content-Length,Authorization,X-Pagination')
    return response

```



###  Thu Dec 10 14:22:04 +0545 2020

#### To take mongodump with timestamp:

```bash 
mongodump --db <db_name> -o dump_`date "+%Y-%m-%dT%H:%M:%S%Z"` 

```

remember the backtick at start of "date" after dump and at the end

###  Thu Dec 10 14:22:04 +0545 2020

#### Collection Specific mongorestore command

```bash
mongorestore --db <db_name> --collection <collection_name> <dump_location>/<collection_name.bson>

```
