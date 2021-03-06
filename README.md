# scalehook
Welcome! I'm glad you came here. I hope that my new library will be very useful for your project. This is a hooking library that works on any platform. If you are really interested in this, then we can continue. <br></br>

The main advantages of this library:
1. Works on any platform
2. You can use it for x32 and x64 architecture
3. Easy to install and simple for use <br></br>

Also you can use my library not only for C, but for C++ too. You will not find it difficult to use it in any of these languages.

## Note
If you want to use it for C++, you should change scalehook source file extension to .cpp. Example: scalehook.`c`=>`cpp`. I hope for you it will not be difficult.

## Contributing
If you want to help me in the develop, then write me a mail. I will write to you about what you can help me, I will be very grateful for your help.

## Issue
If you find a problem when using scalehook, please describe it [here](https://github.com/RakLabs/scalehook/issues). I will try to solve it as soon as possible.

## Getting started
### First prject
Let's take one of the examples from here and try to build it, imagine that this is your project (Or you can write yourself using the example). First of all, we will put the library files in the same folder together with the project. Please note that in the file of your project you must include the library header file. If you are sure that everything is in order, let's build it. First, we compile the scalehook source file. <br>
`gcc -c scalehook.c` <br>
If compiled successfully, then we compile our file. <br>
`gcc -c main.c` <br>
And then build project completely. <br>
`gcc ./*.o -o main.out` <br>
Let's run the program. <br>
`./main.out` <br>
I hope everything turned out of you. If you have any compiling problems, please describe it [here](https://github.com/RakLabs/scalehook/issues).

### Test
To build and run test, follow the steps:
1. Clone this repository (`git clone https://github.com/RakLabs/scalehook`)
2. Build and run (`make`)
3. Done <br>
Report any problems [here](https://github.com/RakLabs/scalehook/issues).

## [Examples](https://github.com/RakLabs/scalehook/tree/master/examples)
```c
#include <stdio.h>
#include "scalehook.h"

scalehook_t *scalehook;
typedef void(*original)(int);

void main_print(int a)
{
  printf("main_print(%i)\n", a);
}

void hook_print(int a)
{
  printf("hook_print(%i)\n", a);
}

int main()
{
  scalehook = scalehook_create((void*)main_print, (void*)hook_print, scalehook_jmp_size, scalehook_opcode_jmp);
  main_print(5);
  scalehook_destroy(scalehook);
  return 0;
}
```
