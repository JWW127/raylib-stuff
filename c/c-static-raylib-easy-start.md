# simple fast setup for static raylib build in c

## prereqs

### working debian build

- gcc
- make
- git

1. clone the repo
   [https://github.com/raysan5/raylib.git](https://github.com/raysan5/raylib.git)
2. after cloned cd raylib>src
3. run `make PLATFORM=PLATFORM_DESKTOP`
4. cd to your project directory
5. create diretories for raylib header files`mkdir include lib`
6. copy libraylib.a from raylib repo to yourproject/lib
7. copy raylib.h from raylib repo to yourproject/include
8. create a main.c with main function at min
9. run `gcc main.c -o main -Iinclude -Llib -lraylib -lm -ldl -lpthread -lGL -lrt -lX11`
10. if your create a .clangd file so your neovim/vscode/ knows where to look to find raylib.h

```yaml
CompileFlags:
  Add: [-Iinclude]
```

11. if no errors its working

> hint
> create a makefile or justfile for step 9

### working macos build

### working asahi linux (fedora) build
