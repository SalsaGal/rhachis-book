# Setting up

## Dependencies

To start using Rhachis, add these dependencies to your `Cargo.toml` file:

```toml
rhachis = "0.6"
glam = "0.22"
```

If you wish to have access to more features of the engine that allow you to customise beyond the simple components, also add the following to the `Cargo.toml`:

```toml
wgpu = "0.14"
```

## Basic Code

The framework expects a single `struct` to perform the core logic for everything. In practice, the core `struct` does not contain much and redirects game logic to other parts of your game.
