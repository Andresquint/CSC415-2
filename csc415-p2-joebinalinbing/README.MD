﻿# CSC 415 - Project 2 - File copy

## Student Name : Joe Binalinbing

## Student ID   : 918501338

## Build Instructions

Line 31-35 prompts for user's files source and destination. Variable source
source and destination is initialized.

Line 38-43 creates an input file. 

line 45-49 creates output file

We run read() and write() inside loop 
because source file might be bigger than our buffer
to copy from one file into another

## Run Instructions

cd to the designated folder.

make

./fc



## strace/dtruss output
csc415@csc415:~$ cd /media/sf_GitHub/csc415-p2-joebinalinbing/
csc415@csc415:/media/sf_GitHub/csc415-p2-joebinalinbing$ strace -c ./fc
strace: Can't stat './fc': No such file or directory
csc415@csc415:/media/sf_GitHub/csc415-p2-joebinalinbing$ make
gcc -I -Wall filecopy.c -o fc
filecopy.c: In function ‘main’:
filecopy.c:33:13: warning: format ‘%s’ expects argument of type ‘char *’, but argument 2 has type ‘char (*)[59]’ [-Wformat=]
     scanf("%s", &source);
            ~^   ~~~~~~~
filecopy.c:35:13: warning: format ‘%s’ expects argument of type ‘char *’, but argument 2 has type ‘char (*)[61]’ [-Wformat=]
     scanf("%s", &destination);
            ~^   ~~~~~~~~~~~~
filecopy.c:66:56: warning: format ‘%i’ expects argument of type ‘int’, but argument 3 has type ‘ssize_t {aka long int}’ [-Wformat=]
     bytes_formatted = sprintf(buffer, "bytes copied:  %i!\n", bytes);
                                                       ~^
                                                       %li
csc415@csc415:/media/sf_GitHub/csc415-p2-joebinalinbing$ strace -c ./fc
Welcome to the File Copy Program by Joe Binalinbing!
Enter the name of the file to copy from:largetest3.txt
Enter the name of the file to copy to:result.txt
            
bytes copied:  4421481!
largetest3.txt% time     seconds  usecs/call     calls    errors syscall
------ ----------- ----------- --------- --------- ----------------
 50.76    8.365992          40    210551           write   writes 210551 to buffer
 49.24    8.114791          39    210551           read         reads 210551 times
  0.00    0.000076          19         4           close    calls close 4 times
  0.00    0.000002           2         1         1 lseek
  0.00    0.000000           0         4           fstat
  0.00    0.000000           0         5           mmap
  0.00    0.000000           0         4           mprotect
  0.00    0.000000           0         1           munmap
  0.00    0.000000           0         3           brk
  0.00    0.000000           0         3         3 access
  0.00    0.000000           0         1           execve
  0.00    0.000000           0         1           arch_prctl
  0.00    0.000000           0         4           openat
------ ----------- ----------- --------- --------- ----------------
100.00   16.480861                421133         4 total
