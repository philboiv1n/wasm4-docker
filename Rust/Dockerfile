# Use an official Node.js runtime as a parent image
FROM node:20-alpine

# Set the working directory in the container
WORKDIR /usr/src/app

# Install utilities
RUN apk add --no-cache curl

# Install Rust and Cargo
RUN curl https://sh.rustup.rs -sSf | sh -s -- -y

# Add Cargo to the PATH for all future shell sessions
ENV PATH="/root/.cargo/bin:${PATH}"

# Add wasm32-unknown-unknown target
RUN rustup target add wasm32-unknown-unknown

# Install WASM4
RUN npm install -g wasm4

# Entrypoint
ENTRYPOINT ["/bin/sh"]