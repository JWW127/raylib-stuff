# simple fast setup for static raylib build in c (macos arm64)

## prereqs

- gcc (clang works too)
- make
- git

### instructions

- clone the repo
  [https://github.com/raysan5/raylib.git](https://github.com/raysan5/raylib.git)
- after cloned cd raylib>src
- run

```shell
make PLATFORM=PLATFORM_DESKTOP
```

- cd to your project directory
- create diretories for raylib header files

```shell
mkdir include/ lib/
```

- copy libraylib.a from raylib repo to yourproject/lib/
- copy raylib.h from raylib repo to yourproject/include/
- create a main.c with main function at the minimum
- run

```shell
gcc -o main main.c -Iinclude -Llib -lraylib -framework CoreVideo -framework IOKit -framework Cocoa -framework GLUT -framework OpenGL -lm
```

#### starter example

```c
#include "raylib.h"
int main(void) {
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

---

##### trouble shooting

> [! TIP]
>
> create a makefile or justfile for the long gcc comppile command
> if you create a .clangd file so your neovim/vscode/ knows where to look to find raylib.h

```yaml
CompileFlags:
  Add: [-Iinclude]
```

check out official wiki if build commands aren't working
[wiki](https://github.com/raysan5/raylib/wiki)
