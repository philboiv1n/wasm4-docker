# WASM-4 + Docker Dev Environment for AssemblyScript

This repository contains instructions to run a simple dev environment for the [WASM-4](https://wasm4.org/) retro game engine using the AssemblyScript language in Docker.

## Create the Docker container

1 - Install and run [Docker Desktop](https://www.docker.com/products/docker-desktop/)

2 - Create new local directory

3 - Pull the AssemblyScript `Dockerfile` (no extension) and copy it in that newly created directory.

4 - From the terminal (or Code), in that new directory, build the image by running the following

```
docker build -t wasm4-as .
```

5 - Run and create the docker container

```
docker run -it -p 4444:4444 -v $(pwd):/usr/src/app --name wasm4-as wasm4-as
```

A shell access to your Docker container should start.

You can restart that same container (later) with the following command

```
docker start -ai wasm4-as
```

## Start a new WASM-4 AssemblyScript project

Create a new WASM-4 AssemblyScript project within your container.
You can change the name `test-project`

```
w4 new --assemblyscript test-project
cd test-project
npm install
```

To build the project

```
npm run build
```

You should now be able to test your setup by running

```
w4 run build/cart.wasm
```

You should now be able to access `http://localhost:4444` and see the demo app running.

You can start modifying the game by accessing the `/src/main.ts` file.

While developing, you can also use `w4 watch` command to starts the build process and starts a server. Changes made to the code, will cause a rebuild and a refresh of the browser.
