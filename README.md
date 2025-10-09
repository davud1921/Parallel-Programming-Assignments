# Parallel-Programming-Assignments
*Before*

base) student@itcenter-lab128:~/Desktop/Parallel-Programming-Assignments$ make valgrind
valgrind --leak-check=full --show-leak-kinds=all --track-origins=yes ./ass_1
==8860== Memcheck, a memory error detector
==8860== Copyright (C) 2002-2017, and GNU GPL'd, by Julian Seward et al.
==8860== Using Valgrind-3.18.1 and LibVEX; rerun with -h for copyright info
==8860== Command: ./ass_1
==8860== 
==8860== Invalid write of size 4
==8860==    at 0x1091C6: main (main.c:7)
==8860==  Address 0x4a9e068 is 0 bytes after a block of size 40 alloc'd
==8860==    at 0x4848899: malloc (in /usr/libexec/valgrind/vgpreload_memcheck-amd64-linux.so)
==8860==    by 0x109185: main (main.c:5)
==8860== 
==8860== Conditional jump or move depends on uninitialised value(s)
==8860==    at 0x1091F4: main (main.c:9)
==8860==  Uninitialised value was created by a stack allocation
==8860==    at 0x109169: main (main.c:3)
==8860== 
==8860== Invalid read of size 4
==8860==    at 0x1091EF: main (main.c:9)
==8860==  Address 0x4a9e068 is 0 bytes after a block of size 40 alloc'd
==8860==    at 0x4848899: malloc (in /usr/libexec/valgrind/vgpreload_memcheck-amd64-linux.so)
==8860==    by 0x109185: main (main.c:5)
==8860== 
==8860== 
==8860== HEAP SUMMARY:
==8860==     in use at exit: 40 bytes in 1 blocks
==8860==   total heap usage: 1 allocs, 0 frees, 40 bytes allocated
==8860== 
==8860== 40 bytes in 1 blocks are definitely lost in loss record 1 of 1
==8860==    at 0x4848899: malloc (in /usr/libexec/valgrind/vgpreload_memcheck-amd64-linux.so)
==8860==    by 0x109185: main (main.c:5)
==8860== 
==8860== LEAK SUMMARY:
==8860==    definitely lost: 40 bytes in 1 blocks
==8860==    indirectly lost: 0 bytes in 0 blocks
==8860==      possibly lost: 0 bytes in 0 blocks
==8860==    still reachable: 0 bytes in 0 blocks
==8860==         suppressed: 0 bytes in 0 blocks
==8860== 
==8860== For lists of detected and suppressed errors, rerun with: -s
==8860== ERROR SUMMARY: 14 errors from 4 contexts (suppressed: 0 from 0)

Mistakes:
1) Initialized in line 4 and 5: We need to initialize ipos and ival because in the original code they were uninitialized we gave them value of 0 to both of them, so we could prevent Unitialized Memory Issue.

2) Memory Overwrites (array out of bounds): I changed loop condition from "i<=10" to "i<10" because the array has 10 elements from 0 to 9 and we are looping to its 11th element.  

3) Memory leak: Missing free(iarray) call. We called free(iarray) to release memory previously allocated using malloc. If we didn`t call free(iarray) there would be a memory leak. 

*After*
(base) student@itcenter-lab128:~/Desktop/Parallel-Programming-Assignments$ make valgrind
gcc -Wall -Wextra -g -std=c99 -o ass_1 main.c
valgrind --leak-check=full --show-leak-kinds=all --track-origins=yes ./ass_1
==9553== Memcheck, a memory error detector
==9553== Copyright (C) 2002-2017, and GNU GPL'd, by Julian Seward et al.
==9553== Using Valgrind-3.18.1 and LibVEX; rerun with -h for copyright info
==9553== Command: ./ass_1
==9553== 
==9553== 
==9553== HEAP SUMMARY:
==9553==     in use at exit: 0 bytes in 0 blocks
==9553==   total heap usage: 1 allocs, 1 frees, 40 bytes allocated
==9553== 
==9553== All heap blocks were freed -- no leaks are possible
==9553== 
==9553== For lists of detected and suppressed errors, rerun with: -s
==9553== ERROR SUMMARY: 0 errors from 0 contexts (suppressed: 0 from 0)