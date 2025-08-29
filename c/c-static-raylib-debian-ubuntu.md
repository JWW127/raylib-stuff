# simple fast setup for static raylib build in c (macos arm64)

## prereqs

- gcc (clang works too)
- make
- git

### working macos apple silicon arm build

- gcc
- make
- git

1. clone the repo
   [https://github.com/raysan5/raylib.git](https://github.com/raysan5/raylib.git)

1. after cloned cd raylib>src

1. run `make PLATFORM=PLATFORM_DESKTOP`

1. cd to your project directory

1. create diretories for raylib header files `mkdir include lib`

1. copy libraylib.a from raylib repo to yourproject/lib

1. copy raylib.h from raylib repo to yourproject/include

1. create a main.c with main function at min

1. run `gcc main.c -o main -Iinclude -Llib -lraylib -lm -ldl -lpthread -lGL -lrt -lX11`

1. if your create a .clangd file so your neovim/vscode/ knows where to look to find raylib.h

```yaml
CompileFlags:
  Add: [-Iinclude]
```

11. if no errors its probably working

#### starter example

```c
#include "raylib.h"
int main(void)
    const int screenWidth = 800;
    const int screenHeight = 450;
    InitWindow(screenWidth, screenHeight, "raylib [core] example - basic window");
    SetTargetFPS(60);
    while (!WindowShouldClose())
    {
        BeginDrawing();
            ClearBackground(RAYWHITE);
            DrawText("Congrats! You created your first window!", 190, 200, 20, LIGHTGRAY);
        EndDrawing();
    }
    CloseWindow();
    return 0;
}
```

______________________________________________________________________

##### trouble shooting

> [! TIP]
> create a makefile or justfile for step 9

[wiki](https://github.com/raysan5/raylib/wiki)
