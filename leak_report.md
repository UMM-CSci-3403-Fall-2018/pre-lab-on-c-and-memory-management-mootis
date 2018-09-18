# Leak report

==25217== 46 bytes in 6 blocks are definitely lost in loss record 1 of 1
==25217==    at 0x4C2FA50: calloc (vg_replace_malloc.c:711)
==25217==    by 0x400678: strip (check_whitespace.c:41)
==25217==    by 0x4006E3: is_clean (check_whitespace.c:62)
==25217==    by 0x40076B: main (check_whitespace.c:87)

46 bytes were lost, and they were allocated by calloc. This was on line 41,62 and 87.

Need to free:
result - in strip
cleaned - in is_cleaned
strings - in main

Was able to use free on result. Using free on the other two caused problems. valgrind says that All heap blocks were freed -- no leaks are possible.
