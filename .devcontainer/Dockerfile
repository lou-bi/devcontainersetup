# Use the latest Ubuntu image as the base
FROM ubuntu:22.04

# Update and install dependencies
RUN apt-get update && \
    apt-get install -y \
    curl \
    git \
    build-essential \
    software-properties-common

# Install Go
ENV GOROOT=/usr/local/go
ENV GOPATH=/go
ENV PATH=$GOPATH/bin:$GOROOT/bin:$PATH
RUN curl -sSL https://golang.org/dl/go1.21.4.linux-amd64.tar.gz | tar -C /usr/local -xz

# Install Node.js
RUN curl -fsSL https://raw.githubusercontent.com/tj/n/master/bin/n | bash -s lts

# Install Python and pipx
RUN apt-get install -y \
    python3 \
    python3-pip && \
    pip3 install --upgrade pip && \
    pip3 install pipx

# Install poetry
RUN curl -sSL https://install.python-poetry.org | python3 -

# Install Helix editor 
RUN add-apt-repository ppa:maveonair/helix-editor
RUN apt-get update
RUN apt-get install helix

# Create a non-root user
RUN useradd -ms /bin/bash loubcontainer
USER loubcontainer

# Set the working directory
WORKDIR /home/loubcontainer

# Start a shell by default
CMD ["/bin/bash"]

