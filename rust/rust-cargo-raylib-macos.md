# Simple setup for Raylib-rs (macos arm64)

## prereqs

- git

## Instructions

- add raylib to cargo.toml dependencies
- [https://github.com/raylib-rs/raylib-rs](https://github.com/raylib-rs/raylib-rs)

```toml
[dependencies]
raylib = "version.number"
```

## hello world example code

- add the following to main.rs

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

- At this point you just need to call `cargo run`
