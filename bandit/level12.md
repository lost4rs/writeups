# OverTheWire Bandit: Level 12
## Objective: Find the password stored in _data.txt_ 
Impediments: The person who is playing, hehe (just joking).  
From the instructions provided, we know that _data.txt_ is a **hexdump** file that has been repeatedly compressed.  

## Our tools
The commands that will be our weapons of war are the following ones:  
`mkdir` <!--(or `mmktemp -d`)--> and `cp`: To work in a temporary folder (important for security and organization!).  
`xxd`: To convert the file to binary.  
`file`: To identify the file type.  
`gzip`, `bzip`, `tar`: The decompression trio.  

## Step by step instructions  
**Step 1: Creating a working space**  
- [ ] Since we cannot create files in the home directory, we must move to `/tmp`. It's a good practice to create a personal folder there.  
`mkdir /tmp/workspace`  
Pro tip: you can use `mktemp -d`, this command creates the directory with permissions such that only the owner can read and write to it (unless modified by umask, but that´s another topic). 
- [ ] Then, we copy *data.txt* to our personal folder.  
`cp data.txt /tmp/workspace`  
- [ ]  And we move there.  
`cd /tmp/workspace`  
## My biggest stumble
