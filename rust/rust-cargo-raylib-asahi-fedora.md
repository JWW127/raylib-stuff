# Simple setup for Raylib-rs (Asahi Linux / Fedora / apple silicon m2)

## prereqs

- gcc
- make
- git

## I had to add the following system level dependencies

```shell
sudo dnf install raylib-devel clang-devel glibc-devel glibc-headers llvm-devel
```

## confusion I had

> the repo [https://github.com/raylib-rs/raylib-rs](https://github.com/raylib-rs/raylib-rs) is not the same name in the dependency you add in the cargo.toml
> repo = raylib-rs
> cargo.toml = raylib = {version, features}

## hello world example code

```rs
use raylib::prelude::*;

fn main() {
    let (mut rl, thread) = raylib::init()
        .size(640, 480)
        .title("Hello, World")
        .build();

    while !rl.window_should_close() {
        let mut d = rl.begin_drawing(&thread);

        d.clear_background(Color::WHITE);
        d.draw_text("Hello, world!", 12, 12, 20, Color::BLACK);
    }
}
```

## run

- At this point you should need to call `cargo run`
