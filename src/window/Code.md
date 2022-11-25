# Basic Code

The framework expects a single `struct` to perform the core logic for everything. In practice, the core `struct` does not contain much and redirects game logic to other parts of your game.

To start, create a `struct` that contains just an `EmptyRenderer`:

```rust
use rhachis::graphics::EmptyRenderer;

struct Window {
    renderer: EmptyRenderer,
}
```

Note the lack of a main function. Right now this program doesn't even compile, we need to add the `#[run]` annotation and implement `Game`.

```rust
use rhachis::{*, graphics::EmptyRenderer};

#[run]
struct Window(EmptyRenderer);

impl Game for Window {
    fn init(_: &GameData) -> Self {
        Self(EmptyRenderer)
    }

    fn get_renderer(&mut self) -> &mut dyn graphics::Renderer {
        &mut self.0
    }
}
```

This is the most minimal Rhachis program, and you'll notice that it is  identical to the [window example](https://github.com/SalsaGal/rhachis/blob/master/examples/window.rs) on the repository.

Note that the code includes `rhachis::*`, this is important, as `rhachis::GameExt` is required for it to compile, despite not actually being referenced in the code. This is because it is referenced by the `#[run]` macro.
