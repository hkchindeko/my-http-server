# Let's make an Wasm32 Wasi HTTP Server

This is another attempt to create a Hyper HTTP server that compile in Wasm32-Wasi.

To compile, easy execute
```
$ cargo build --target wasm32-wasi --release
```

To run the server execute:
```bash
$ source $HOME/.wasmedge/env
$ wasmedge target/wasm32-wasi/release/my-http-server.wasm
```

To build the Docker image for wasi/wasm32 execute the following command. 
Note: You will need the latest version of Docker desktop (as of 16/01/2023).
```bash
$ docker build --platform wasi/wasm32 -t my-http-service .
```

To execute the docker container with the image built above, execute the following:
```bash
$ docker run -dp 8080:8080 --name=my-http-service --runtime=io.containerd.wasmedge.v1 --platform=wasi/wasm32 my-http-service
```

To test the container is currently working execute:
```bash
$ curl -v -X GET localhost:8080/
$ curl -v -X POST localhost:8080/echo -d "Hello World from Wasm Container in Docker"
```