FROM rustlang/rust:nightly

RUN mkdir /app
WORKDIR /app

RUN curl -sS https://dl.yarnpkg.com/debian/pubkey.gpg | apt-key add -
RUN echo "deb https://dl.yarnpkg.com/debian/ stable main" | tee /etc/apt/sources.list.d/yarn.list

RUN apt-get update -y && apt-get upgrade -y
RUN apt-get install -y libssl-dev

# Install node
RUN curl -sL https://deb.nodesource.com/setup_17.x | bash - \
    && apt-get install -y nodejs yarn

# Install wasm-pack
RUN curl https://rustwasm.github.io/wasm-pack/installer/init.sh -sSf | sh

RUN rustup update
RUN rustup target add wasm32-unknown-unknown
CMD ["/bin/bash"]