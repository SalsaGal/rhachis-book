# Setup

Before code can be written, the workspace must be set up. Make a folder for the project and run `cargo init`. In the main file write the following code:

```rust
use rhachis::{*, renderers::SimpleRenderer};

#[run]
struct Window {
    renderer: SimpleRenderer,
}

impl Game for Window {
    fn init(data: &GameData) -> Self {
        Self {
            renderer: SimpleRenderer::new(data, todo!()),
        }
    }

    fn get_renderer(&mut self) -> &mut dyn graphics::Renderer {
        &mut self.renderer
    }
} 
```

The field marked as `todo!()` is the one for the projection. There are a few options for what to fill this with. Since this is a 2D game we'll want something orthographic, but other options can be found [here](https://docs.rs/rhachis/latest/rhachis/renderers/enum.SimpleProjection.html#implementations).

```rust
SimpleRenderer::new(data, SimpleRenderer::default()),
```

