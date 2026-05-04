FROM ubuntu:22.04

# install dependencies
RUN apt-get update && apt-get install -y \
    g++ \
    curl \
    && rm -rf /var/lib/apt/lists/*

# install ollama
RUN curl -fsSL https://ollama.com/install.sh | sh

# set working dir
WORKDIR /app

# copy files
COPY . .

# build project
RUN g++ -std=c++17 -O2 main.cpp -o db -lws2_32

# expose port
EXPOSE 8080

# start everything
CMD ollama serve & ./db
