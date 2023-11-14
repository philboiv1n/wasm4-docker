# Use an official Node.js runtime as a parent image
FROM node:20-alpine

# Set the working directory in the container
WORKDIR /usr/src/app

# Install WASM4
RUN npm install -g wasm4

# Make bash the default shell
ENTRYPOINT ["/bin/sh"]