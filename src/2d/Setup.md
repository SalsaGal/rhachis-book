# Setup

Before code can be written, the workspace must be set up. Make a folder for the project and run `cargo init`. Add the following to the `Cargo.toml`'s dependencies:

```toml
glam = "0.22"
image = "0.24"
rhachis = "0.6"
```

 In the main file write the following code:

```rust
use rhachis::{*, renderers::SimpleRenderer};

#[run]
struct GoInvaders {
    renderer: SimpleRenderer,
}

impl Game for GoInvaders {
    fn init(data: &GameData) -> Self {
        let renderer = SimpleRenderer::new(data, todo!());
        Self { renderer }
    }

    fn get_renderer(&mut self) -> &mut dyn graphics::Renderer {
        &mut self.renderer
    }
} 
```

The field marked as `todo!()` is the one for the projection. There are a few options for what to fill this with. Since this is a 2D game we'll want something orthographic, but other options can be found [here](https://docs.rs/rhachis/latest/rhachis/renderers/enum.SimpleProjection.html#implementations). We'll want the origin to be the centre and the width to be free, but want the height to be a consistent range from 1.0, to -1.0. To do this we write:

```rust
let renderer = SimpleRenderer::new(
    data,
    SimpleRenderer::center_height(data.get_window_size().as_vec2(), 2.0),
);
```

If we run this now, you won't see much, just a black screen.
