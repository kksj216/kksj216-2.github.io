---
layout: post
title: <DS> Build Process 
tags: [DS]
color: blue
---



Compile, Link, Build static library 그리고 Make file에 대해서 정리한다.

<br>

## Build Process

Build process는 소스코드로 시작해서 실행파일로 끝나는 것을 말한다.

`Source Code` ---__complie__---> `Object files` ---__link__---> `Executable`

```powershell
$ g++ -c sort.cpp print_list.cpp -I../include       // Complie
$ g++ sort.o print_list.o -L../lib -lsort -o sort   // Link
or
$ g++ -c sort.cpp print_list.cpp -I../include -L../lib -lsort -o sort
(libsort.a가 ../lib에 있다고 가정한다.)
```

<br>

<br>

## Compile & Link

- __Compile stage__ __(.cpp , .h -> .o)__
  - __Syntax__ checked for correctness(문법 체크) 
  - Variables and function calls checked to insure that correct declarations
    were made and that they match. 
  - It __doesn't match function definitions__ to their calls at this point. 
  - 아직 실행파일이 아니다. __object code__로 번역하는거다. 
- 여러 소스코드들이 있는데 만약에, 하나의 코드만 수정을 했는데 전부다 컴파일 다시해야되면 비효율적이다. 이 때 수정된 소스만 컴파일하면 효율적임!

- __Linking stage (.o, .a -> .exe)__
  - object code를 실행파일로 Link한다. 
  - object code file은 한개일 수도, 여러개일 수도 있다. 
  - __Function calls__ are matched up with their definitions, and the compiler
    checks to make sure it has one, and only one, definition for every function.
  - The end result of linking is usually an __executable__.

<br>

- __Compiling options__
  - `-g` : turn on debugging
  - `-Wall` : turn on most warnings
  - `-O or -O2` : turn on optimizations
  - `-o <name>` : name of the output
  - `-c` : output an object file 
  - `-I<include path> `: specify an include derectory
  - `-L<library path>` : specify a lib directory
  - `-l<library>` : link with library `lib<library>.a`
- Use `-Ldir` option such that linker looks for library files in in `dir` folder
- Use `-llibrary` such that linker searches the library named `library`

<br>

 소스코드 파일들이 여러 개가 있다고 생각해보자. 여러개의 파일들 중에서 _하나만_ 변경된 경우, 그 하나의 파일을 위해서 변경사항이 없는 소스코드 파일들까지 __전부 다__ 다시 컴파일을 한다. 이것은 브루트 포스 방법이고 비효율적인 것으로 보인다. 

![build1](https://github.com/kksj216/kksj216.github.io/blob/master/assets/img/ds/build1.PNG?raw=true)

마지막 빌드 이후로 하나의 소스 코드 파일만 변경된 경우에 다시 빌드할 때, 사실상 변경된 파일만을 다시 컴파일하면 된다. 변경되지 않은 파일들까지 다시 컴파일하지 않고!! 이전 빌드의 변경되지 않은 Object file을 사용하면 전체 빌드 시간들 줄일 수 있다! 

![build2](https://github.com/kksj216/kksj216.github.io/blob/master/assets/img/ds/build2.PNG?raw=true)

<br>

<br>

## Creating a Library Archive

- __Archive?__ 여러개의 object 파일들을 하나의 파일로 만드는 것이다. 

- __Naming convention:__ `lib`로 시작해서 `.a`로 끝나게 해야 한다.
- `ar` 명령어를 사용해서 object file로 부터 archive file이 만들어질 수 있다. 
  
- ex) `$ ar cr libsort.a bubble.o insertion.o quicksort.o selection.o`
  
- __ar 옵션__ 

  - `-c` : Create an archive file

  - `-r` : Insert the files member... into archive (with replacement) 

  - `-s` : Write an object-file index into the archive, change is made to the archive

  - `-t` : Display contents of archive (show the list of .o files, use nm ~.o to see functions in ~.o)

  - ```
    c는 이러한 library가 생성되어있지 않을 때 추가하라는 명령어, 즉 아카이브가 생성되어있지 않을 때 추가하라는 명령어
    
    r은 library 즉 libnowic.a에 새로운 object file 즉 nowic.o를 추가하겠다는 명령어, 만약 nowic가 존재하면 새롭게 update하라는 명령어
    
    s는 아카이브된 파일들에 index를 붙여 주어서 몇번째로 조합하고 묶어낸 파일인지 식별하는 명령어
    ```

- `ar` Examples: 

  - `g++ -c nowic.cpp -L../include`  -> produces nowic.o
  - `ar crs libnowic.a nowic.o`  ->  produces libnowic.a that includes nowic.o
  - `ar` -> list all the options available
  - `ar t libnowic.a` -> list ~.o files archived
  - `ar x libnowic.a` -> extract ~.o files archived
  - `nm libnowic.o`  -> list the actual function names in .o file

<br>

<br>

## Make 

- make file을 쓰면 뭐가 좋은가? 

소스파일들로부터 프로그램 파일을 만드는 것은 복잡하고 시간이 오래 걸린다. 명령어를 하나하나 치고 있어야 하니...! 소스코드가 여러갠데, 한 파일만 조금 수정을 했다가 다시 전부다를 컴파일을 해야 하면 너무 비효율적이다. 또는 리컴파일을 해야하는 파일을 까먹으면 찾는데 애먹는다. 그 래 서 나온것이 __make__이다! 

*__makefile__*은 프로그램을 빌드하기 위한 레시피(?)들을 가지고 있다. 

- 기본적인 문법!

```makefile
target: dependencies     // dependencies는 target을 만드는데 필요한 파일들임
    system command(s)    // 여기는 target을 만드는 명령어 
```

- 예시

Source files: quicksort.cpp  /  print_list.cpp
Executable: qsort.exe

```makefile
qsort: quicksort.o print_list.o
	g++ quicksort.o print_list.o -o qsort

quicksort.o: quicksort.cpp
	g++ -c quicksort.cpp
print_list.o: print_list.cpp
	g++ -c print_list.cpp
clean:								// clean 이라는 명령어. make clean하면
	rm -f *.o qsort.exe qsort       // 이 명령어를 실행한다. 
```

<br>

```makefile
# Using Rules
INCDOR = ../../include
SRCS = sortx.cpp print_list.cpp ...    //소스파일을 리스트함
OBJS = $(SRCS:.cpp=.o)                 //.cpp로 되어있는 파일을 .o로 만들어줘
Target = sortx						   // 타겟이름.
$(TARGET): $(OBJS)
    g++ -I$(INCDIR) $(SRCS) -o $(TARGET)
```

<br>

- a typical *__Makefile__*

```makefile
CC = g++
CCFLAGS = -Wall
LDFLAGS = -L$(LIBDIR) -lsort -lnowic -lm
LIBDIR = ../lib
INCDIR = ../include
SRCS = $(wildcard *.cpp)
OBJS = $(SRCS:.cpp=.o)
TARGET = $(SRCS:.cpp=.o)
TARGET: $(OBJS)
	$(CC) $(CCFLAGS) -I$(INCDIR) -o $@ $^ $(LDFLAGS)
	
.PHONY: clean
clean:
	rm -f $(OBJS) $(TARGET)
```

`$@` : refers to target

`$^` : refers to all dependencies

`$<` : refers to the first dependency

`$*` : wildcard (or any number of characters)

`%` : make a pattern that we want to watch in both the target and the dependency (약간 for루프 같은거)

<br>

- Ex)

```makefile
# make.1 - incomplete makefile without automatic dependencies
CC = g++
CCFLAGS = -Wall
LDFLAGS = -L$(LIBDIR)
LIBDIR = ../../lib
INCDIR = ../../include
SRCS = sort.cpp print_list.cpp bubble.cpp insertion.cpp quicksort.cpp selection.cpp
OBJS = $(SRCS:.cpp=.o)
TARGET = sort
%.o: %.cpp
	$(CC) -c -I$(INCDIR) -o $@ $< $(CCFLAGS)
$(TARGET): $(OBJS)
	$(CC) -o $@ $^ $(LDFLAGS)
.PHONY: clean cleanx
clean:
	rm -f $(OBJS)
cleanx:
	rm -f $(OBJS) $(TARGET).exe $(TARGET)
```

```powershell
$ make -f make.1
$ make clean -f make.1
$ make cleanx -f make.1
```

Reference - https://www.tuwlab.com/index.php?mid=ece&category=7074&document_srl=27193

<br>