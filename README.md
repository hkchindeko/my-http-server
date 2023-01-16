# Let's make an Wasm32 Wasi HTTP Server

This is another attempt to create a Hyper HTTP server that compile in Wasm32-Wasi.

To compile, easy execute
```
cargo build --target wasm32-wasi --release
```

To run the server execute:
```
source $HOME/.wasmedge/env
wasmedge target/wasm32-wasi/release/my-http-server.wasm
```