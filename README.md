# strfuncs

A custom string library in C

Source Code -> [https://gitlab.com/adwaithrajesh/strfuncs](https://gitlab.com/adwaithrajesh/strfuncs)

## Why a custom C lib

why not.

## Usage

- Clone the repo
  ```bash
  git clone https://gitlab.com/adwaithrajesh/strfuncs.git
  ```
- Compile the library

  ```bash
  make libstrfuncs.so
  ```

  This should make a `libstrfuncs.so` file in the current directory.
  Now you can move the `libstrfuncs.so` file and the header file from the src
  dir to your preferred dir.

  Lets go through a test use case.
  After cloning the repo and moving the file, I've the following file structure.

  ```commandline
  .
  ├── include
  │   └── strfuncs.h
  ├── lib
  │   └── libstrfuncs.so
  └── main.c
  ```

  - contents of `main.c` (and the list of all the available funcs)

  ```c
  #include <stdio.h>

  #include "strfuncs.h"

  int main(void) {
      printf("char count %ld\n", char_count("Hello World", 'l'));
      printf("is lower %d\n", is_lower("hello"));
      printf("is upper %d\n", is_upper("HELLO"));
      printf("is digit %d\n", is_digit("23423"));
      printf("is alpha %d\n", is_alpha("hElLO"));
      printf("startwith %d\n", startswith("Hello", "He"));
  }
  ```

  - compiling `main.c`

  ```commandline
  gcc main.c -I./include -L./lib -lstrfuncs -o main
  ```

  ```commandline
  LD_LIBRARY_PATH=./lib ./main

  char count 3
  is lower 1
  is upper 1
  is digit 1
  is alpha 1
  startwith 1
  ```

### using strfuncs without making a shared lib

Copy the two file in the `src` dir to your project folder.

```commandline
.
├── main.c
├── strfuncs.c
└── strfuncs.h
```

the you can compile the files to binary using the following command

```commandline
gcc main.c strfuncs.c -o main
```

```commandline
./main
char count 3
is lower 1
is upper 1
is digit 1
is alpha 1
startwith 1

```

#### Notes 😀

I'm a complete noob when it comes to C. So if you feel that the code is 'dangerous' or can
be made more efficient then please create an issue [here](https://gitlab.com/adwaithrajesh/strfuncs/-/issues) and help me fix my mistake.
