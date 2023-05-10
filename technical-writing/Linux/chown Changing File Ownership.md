## chown Changing File Ownership
Initially, the owner of a file is the user who creates it. The `chown` command is used to change the ownership of files and directories. Changing the user owner requires administrative access. A regular user cannot use this command to change the user owner of a file, even to give the ownership of one of their own files to another user. However, the `chown` command also permits changing group ownership, which can be accomplished by either root or the owner of the file.

To change the user owner of a file, the following syntax can be used. The first argument, [OWNER], specifies which user is to be the new owner. The second argument, FILE, specifies which file's ownership is changing.

`chown [OPTIONS] [OWNER] FILE` 

    **Follow Along**
    
    Use the following command to switch to the Documents directory:
    
    sysadmin@localhost:~$ cd ~/Documents

Currently all the files in the Documents directory are owned by the sysadmin user. This can be verified by using the `ls -l` command. Recall that the third column indicates the user owner.

    sysadmin@localhost:~/Documents$ ls -l                                           
    total 144                                                                       
    drwx------ 5 sysadmin sysadmin  4096 Dec 20  2017 School                        
    drwx------ 2 sysadmin sysadmin  4096 Dec 20  2017 Work                          
    -rw-r--r-- 1 sysadmin sysadmin    39 Dec 20  2017 adjectives.txt                
    -rw-r--r-- 1 sysadmin sysadmin    90 Dec 20  2017 alpha-first.txt               
    -rw-r--r-- 1 sysadmin sysadmin   106 Dec 20  2017 alpha-second.txt              
    -rw-r--r-- 1 sysadmin sysadmin   195 Dec 20  2017 alpha-third.txt               
    -rw-r--r-- 1 sysadmin sysadmin   390 Dec 20  2017 alpha.txt                     
    -rw-r--r-- 1 sysadmin sysadmin    42 Dec 20  2017 animals.txt                   
    -rw-r--r-- 1 sysadmin sysadmin    14 Dec 20  2017 food.txt                      
    -rwxr--r-- 1 sysadmin sysadmin   647 Dec 20  2017 hello.sh                      
    -rw-r--r-- 1 sysadmin sysadmin    67 Dec 20  2017 hidden.txt                    
    -rw-r--r-- 1 sysadmin sysadmin    10 Dec 20  2017 letters.txt                   
    -rw-r--r-- 1 sysadmin sysadmin    83 Dec 20  2017 linux.txt                     
    -rw-r--r-- 1 sysadmin sysadmin 66540 Dec 20  2017 longfile.txt                  
    -rw-r--r-- 1 sysadmin sysadmin   235 Dec 20  2017 newhome.txt                   
    -rw-r--r-- 1 sysadmin sysadmin    10 Dec 20  2017 numbers.txt                   
    -rw-r--r-- 1 sysadmin sysadmin    77 Dec 20  2017 os.csv                        
    -rw-r--r-- 1 sysadmin sysadmin    59 Dec 20  2017 people.csv                    
    -rw-r--r-- 1 sysadmin sysadmin   110 Dec 20  2017 profile.txt                   
    -rw-r--r-- 1 sysadmin sysadmin    51 Dec 20  2017 red.txt   
To switch the owner of the hello.sh script to the root user, use root as the first argument and hello.sh as the second argument. Don't forget to use the `sudo` command in order to gain the necessary administrative privileges. Use password netlab123 if prompted:

    sysadmin@localhost:~/Documents$ sudo chown root hello.sh                        
    [sudo] password for sysadmin:
Confirm the user owner has changed by executing the `ls -l` command. Use the filename as an argument to limit the output:

    sysadmin@localhost:~/Documents$ ls -l hello.sh                                  
    -rwxr--r-- 1 root sysadmin 647 Dec 20  2017 hello.sh  
The user owner field is now root indicating the change was successful.

`-rwxr--r-- 1 root sysadmin 647 Dec 20  2017 hello.sh`
    
    **Consider This**
    
    Try executing the hello.sh script again. It fails! Why?
    
    sysadmin@localhost:~/Documents$ ./hello.sh                                      
    -bash: ./hello.sh: Permission denied  
   
    Only the user owner has the execute permission, and now the root user is the user owner. This file now requires administrative access to execute. Use the sudo command to execute the script as the root user.
    
    sysadmin@localhost:~/Documents$ sudo ./hello.sh                                 
    [sudo] password for sysadmin:                                                   
     ______________                                                                 
    ( Hello World! )                                                                
     --------------                                                                 
            \                                                                       
             \                                                                      
               <(^)                                                                 
                ( )  