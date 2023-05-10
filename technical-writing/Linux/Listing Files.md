## Listing Files
The `ls` command is used to list the contents of a directory. You've already seen it used a few times before in examples, but this page will help ensure you are comfortable with its use.

    ls [OPTIONS] [FILE]

By default, when the `ls` command is used with no options or arguments, it will list the files in the current directory:

    sysadmin@localhost:~$ ls
    Desktop  Documents  Downloads  Music  Pictures  Public  Templates  Videos

To learn the details about a file, such as the type of file, the permissions, ownerships or the timestamp, perform a long listing using the `-l` option to the ls command. Below, a listing of the /var/log directory is used as an example, since it provides a variety of output:

    sysadmin@localhost:~$ ls -l /var/log/
    total 844                                                                       
    -rw-r--r-- 1 root   root  18047 Dec 20  2017 alternatives.log                   
    drwxr-x--- 2 root   adm    4096 Dec 20  2017 apache2                            
    drwxr-xr-x 1 root   root   4096 Dec 20  2017 apt                                
    -rw-r----- 1 syslog adm    1346 Oct  2 22:17 auth.log                           
    -rw-r--r-- 1 root   root  47816 Dec  7  2017 bootstrap.log                      
    -rw-rw---- 1 root   utmp      0 Dec  7  2017 btmp                               
    -rw-r----- 1 syslog adm     547 Oct  2 22:17 cron.log                           
    -rw-r----- 1 root   adm   85083 Dec 20  2017 dmesg                              
    -rw-r--r-- 1 root   root 325238 Dec 20  2017 dpkg.log                           
    -rw-r--r-- 1 root   root  32064 Dec 20  2017 faillog                            
    drwxr-xr-x 2 root   root   4096 Dec  7  2017 fsck                               
    -rw-r----- 1 syslog adm     106 Oct  2 19:57 kern.log                           
    -rw-rw-r-- 1 root   utmp 292584 Oct  2 19:57 lastlog                            
    -rw-r----- 1 syslog adm   19573 Oct  2 22:57 syslog                             
    drwxr-xr-x 2 root   root   4096 Apr 11  2014 upstart                            
    -rw-rw-r-- 1 root   utmp    384 Oct  2 19:57 wtmp 

Each line corresponds to a file contained within the directory. The information can be broken down into fields separated by spaces. The fields are as follows:

**File Type**

    -rw-r--r-- 1 root   root  18047 Dec 20  2017 alternatives.log       
                
    drwxr-x--- 2 root   adm    4096 Dec 20  2017 apache2  
The first field actually contains ten characters, where the first character indicates the type of file and the next nine specify permissions. The file types are:

The first field actually contains ten characters, where the first character indicates the type of file and the next nine specify permissions. The file types are:

    Symbol    File Type    Description
    d    directory    A file used to store other files.
    -    regular file    Includes readable files, images files, binary files, and compressed files.
    l    symbolic link    Points to another file.
    s    socket    Allows for communication between processes.
    p    pipe    Allows for communication between processes.
    b    block file    Used to communicate with hardware.
    c    character file    Used to communicate with hardware.
The first file alternatives.log is a regular file -, while the second file apache2 is a directory d.

**Permissions**

    drwxr-xr-x 2 root   root   4096 Apr 11  2014 upstart
Permissions indicate how certain users can access a file. Keep reading to learn more about permissions.

**Hard Link Count**

    -rw-r----- 1 syslog adm    1346 Oct  2 22:17 auth.log

This number indicates how many hard links point to this file. Hard links are beyond the scope of this module, but are covered in the NDG Linux Essentials course.

**User Owner**

    -rw-r----- 1 syslog adm     106 Oct  2 19:57 kern.log

User syslog owns this file. Every time a file is created, the ownership is automatically assigned to the user who created it.

**Group Owner**

    -rw-rw-r-- 1 root   utmp 292584 Oct  2 19:57 lastlog
Indicates which group owns this file

**File Size**

    -rw-r----- 1 syslog adm   19573 Oct  2 22:57 syslog

Directories and larger files may be shown in kilobytes since displaying their size in bytes would present a very large number. Therefore, in the case of a directory, it might actually be a multiple of the block size used for the file system. Block size is the size of a series of data stored in the filesystem.

**Timestamp**

    drwxr-xr-x 2 root   root   4096 Dec  7  2017 fsck
This indicates the time that the file's contents were last modified.

**Filename**

    -rw-r--r-- 1 root   root  47816 Dec  7  2017 bootstrap.log
The final field contains the name of the file or directory.

**Consider This**

In the case of symbolic links, a file that points to another file, the link name will be displayed along with an arrow and the pathname of the original file.

    lrwxrwxrwx. 1 root root 22 Nov 6 2012 /etc/grub.conf -> ../boot/grub/grub.conf

Symbolic links are beyond the scope of this module, but are covered in the NDG Linux Essentials course.

## Sorting
By default the output of the `ls` command is sorted alphabetically by filename. It can sort by other methods as well.

**Follow Along**

The options in examples below will be combined with the `-l` option so the relevant details of the files are displayed. Notice fields corresponding to the search option.

The `-t` option will sort the files by timestamp:

    sysadmin@localhost:~$ ls -lt /var/log                                           
    total 844                                                                       
    -rw-r----- 1 syslog adm   19573 Oct  2 22:57 syslog                             
    -rw-r----- 1 syslog adm    1346 Oct  2 22:17 auth.log                           
    -rw-r----- 1 syslog adm     547 Oct  2 22:17 cron.log                           
    -rw-rw-r-- 1 root   utmp 292584 Oct  2 19:57 lastlog                            
    -rw-rw-r-- 1 root   utmp    384 Oct  2 19:57 wtmp                               
    -rw-r----- 1 syslog adm     106 Oct  2 19:57 kern.log                           
    -rw-r--r-- 1 root   root  18047 Dec 20  2017 alternatives.log                   
    -rw-r--r-- 1 root   root  32064 Dec 20  2017 faillog                            
    -rw-r----- 1 root   adm   85083 Dec 20  2017 dmesg                              
    -rw-r--r-- 1 root   root 325238 Dec 20  2017 dpkg.log                           
    drwxr-x--- 2 root   adm    4096 Dec 20  2017 apache2                            
    drwxr-xr-x 1 root   root   4096 Dec 20  2017 apt                                
    -rw-r--r-- 1 root   root  47816 Dec  7  2017 bootstrap.log                      
    drwxr-xr-x 2 root   root   4096 Dec  7  2017 fsck                               
    -rw-rw---- 1 root   utmp      0 Dec  7  2017 btmp                               
    drwxr-xr-x 2 root   root   4096 Apr 11  2014 upstart              

The `-S` option will sort the files by file size:

    sysadmin@localhost:~$ ls -l -S /var/log                                         
    total 844                                                                       
    -rw-r--r-- 1 root   root 325238 Dec 20  2017 dpkg.log                           
    -rw-rw-r-- 1 root   utmp 292584 Oct  2 19:57 lastlog                            
    -rw-r----- 1 root   adm   85083 Dec 20  2017 dmesg                              
    -rw-r--r-- 1 root   root  47816 Dec  7  2017 bootstrap.log                      
    -rw-r--r-- 1 root   root  32064 Dec 20  2017 faillog                            
    -rw-r----- 1 syslog adm   19573 Oct  2 22:57 syslog                             
    -rw-r--r-- 1 root   root  18047 Dec 20  2017 alternatives.log                   
    drwxr-x--- 2 root   adm    4096 Dec 20  2017 apache2                            
    drwxr-xr-x 1 root   root   4096 Dec 20  2017 apt                                
    drwxr-xr-x 2 root   root   4096 Dec  7  2017 fsck                               
    drwxr-xr-x 2 root   root   4096 Apr 11  2014 upstart                            
    -rw-r----- 1 syslog adm    1346 Oct  2 22:17 auth.log                           
    -rw-r----- 1 syslog adm     547 Oct  2 22:17 cron.log                           
    -rw-rw-r-- 1 root   utmp    384 Oct  2 19:57 wtmp                               
    -rw-r----- 1 syslog adm     106 Oct  2 19:57 kern.log                           
    -rw-rw---- 1 root   utmp      0 Dec  7  2017 btmp

The `-r` option will reverse the order of any type of sort. Notice the difference when it is added to the previous example:

    sysadmin@localhost:~$ ls -lSr /var/log
    total 844                                                                       
    -rw-rw---- 1 root   utmp      0 Dec  7  2017 btmp                               
    -rw-r----- 1 syslog adm     106 Oct  2 19:57 kern.log                           
    -rw-rw-r-- 1 root   utmp    384 Oct  2 19:57 wtmp                               
    -rw-r----- 1 syslog adm     654 Oct  2 23:17 cron.log                           
    -rw-r----- 1 syslog adm    1669 Oct  2 23:17 auth.log                           
    drwxr-xr-x 2 root   root   4096 Apr 11  2014 upstart                            
    drwxr-xr-x 2 root   root   4096 Dec  7  2017 fsck                               
    drwxr-xr-x 1 root   root   4096 Dec 20  2017 apt                                
    drwxr-x--- 2 root   adm    4096 Dec 20  2017 apache2                            
    -rw-r--r-- 1 root   root  18047 Dec 20  2017 alternatives.log                   
    -rw-r----- 1 syslog adm   19680 Oct  2 23:17 syslog                             
    -rw-r--r-- 1 root   root  32064 Dec 20  2017 faillog                            
    -rw-r--r-- 1 root   root  47816 Dec  7  2017 bootstrap.log                      
    -rw-r----- 1 root   adm   85083 Dec 20  2017 dmesg                              
    -rw-rw-r-- 1 root   utmp 292584 Oct  2 19:57 lastlog                            
    -rw-r--r-- 1 root   root 325238 Dec 20  2017 dpkg.log

The numbers in file size field switch from descending to ascending.

Used alone the `-r `option with list the files in reverse alphabetical order:

    sysadmin@localhost:~$ ls -r /var/log                                            
    wtmp     lastlog   faillog   cron.log       auth.log  alternatives.log
    upstart  kern.log  dpkg.log  btmp           apt
    syslog   fsck      dmesg     bootstrap.log  apache2