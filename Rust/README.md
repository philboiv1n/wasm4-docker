# WASM-4 + Docker Dev Environment for Rust

This repository contains instructions to run a simple dev environment for the [WASM-4](https://wasm4.org/) retro game engine using Rust language in Docker.

## Create the Docker container

1 - Install and run [Docker Desktop](https://www.docker.com/products/docker-desktop/)

2 - Create new local directory

3 - Pull the Dockerfile from the AssemblyScript in this repo and copy it in that newly created directory.

4 - From the terminal (or Code), in that new directory, build the image by running the following

```
docker build -t wasm4-rust .
```

5 - Run and create the docker container

```
docker run -it -p 4444:4444 -v $(pwd):/usr/src/app --name wasm4-rust wasm4-rust
```

A shell access to your Docker container should start.

You can restart that same container (later) with the following command

```
docker start -ai wasm4-rust
```

## Start a new WASM-4 Rust project

Create a new WASM-4 Rust project within your container.
You can change the name `test-project`

```
w4 new --rust test-project
cd test-project
```

To build the project

```
cargo build --release
```

You should now be able to test your setup by running

```
w4 run target/wasm32-unknown-unknown/release/cart.wasm
```

You should now be able to access `http://localhost:4444` and see the demo app running.

You can start modifying the game by accessing the `/src/lib.rs` file.

While developing, you can also use `w4 watch` command to starts the build process and starts a server. Changes made to the code, will cause a rebuild and a refresh of the browser.
