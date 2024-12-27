```sh
> cargo doc
error: document output filename collision
The lib `b` in package `b v0.1.0 (doc-collision-minimal/b)` has the same name as the lib `b` in package `b v0.1.0 (doc-collision-minimal/b)`.
Only one may be documented at once since they output to the same path.
Consider documenting only one, renaming one, or marking one with `doc = false` in Cargo.toml.
```

# Steps to reproduce

- Workspace with 2 crates: `a` and `b`.
  - `a` depends on `b`, which is a `proc-macro`.
- Compile with optimizations enabled (any `opt-level` except `0`)
- Specify an explicit target (e.g. `x86_64-unknown-linux-musl`)

## Example

```sh
cargo doc -r --target x86_64-unknown-linux-musl
```
