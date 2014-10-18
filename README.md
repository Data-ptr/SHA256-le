# SHA256-le
## A simple implementation of the SHA256 hashing algorithm in C

*By: Jane Hacker - janehacker.com*

---

### Disclaimer
I did this for fun and experimentation. It is clearly NOT consumer, user, or probably even superuser friendly. You will only find it useful as a developer, and then only if you are really interested in the inner workings of SHA265 and just want a simple step by step example of the process that you can build, trace though, and play with in actually code.

**DO NOT USE THIS CODE IN PRODUCTION,** don't even use it in your projects unless it really helps to have a skeleton implementation.

There are production ready implementations of SHA256 from multiple sources in probably every language imaginable, use these in your code!


This code is in no way guaranteed to work.
There are very few, if any checks.
No way it is near the fastest.
It is not tested for portability, do so at your own risk! (And read notes below, they might help)

There are sure to be bugs....
...and poor general coding practices
...and poor C coding practices
...and overflows
...and underflows
...and every other kind of flow possible

---

### What is it good for
* Learning SHA256 and maybe hashing in general (it is simple)
* Having an SHA256 implementation to play with (and in C)
* It prints out each compression step's hash output
 * I have found this to be VERY useful in checking and debugging other/your own SHA256 implementations or other related code
* There is commented code to print various steps of the initialization process in binary

---

### What is included

* The source... Yup.
* This README
* A super simple Makefile
* A Windows binary
 * Which probably requires MinGW or Cygwin libraries
 * And might be for 64-bit systems only

---

### What is ~~wrong~~ not so good with it

* Endianness
 * I have it swap the input so it works on x86 and other little-endian architectures
 * because I used big-endian constants, I don't know why
 * If using this code on a big-endian system just skipping the swap step should work... maybe


* Uses ROR instruction by default
 * Which is common on x86
 * Not on, say... ARM
 * There is a commented macro without it though
 * Honestly the non-ROR version is probably faster in the end?


* It uses C99 standard
 * Which makes playing with it, coding, and readability easier
 * I'm sure works with newer versions
 * But requires a C99 compatable compiler, or a few rewrites for ones without it
 * I doubt even the newest of C programmers would have any trouble doing those rewrites...
 * Requires an entire extra argument on the command line to compile (`--std=c99` if you didn't know, and couldn't look in the Makefile)

---

### Credits

#### Pseudo-code
From Wikipedia's entry for "SHA-2"
http://en.wikipedia.org/wiki/SHA-2#Pseudocode
In history if for some reason it is (re)moved or changed:
http://en.wikipedia.org/w/index.php?title=SHA-2&diff=630108357&oldid=17306306#Pseudocode

#### Binary printer (function named "p")
Is from an answer on stack overflow
http://stackoverflow.com/a/3974138
