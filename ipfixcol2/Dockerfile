# Stage 1: Build environment
# FROM debian:bullseye-slim AS builder
FROM debian:bullseye-slim 

# Install build dependencies
RUN apt-get update && apt-get install -y \
    doxygen build-essential gcc g++ git cmake make pkg-config python3-docutils zlib1g-dev librdkafka-dev libxml2-dev liblz4-dev libzstd-dev



RUN git clone https://github.com/CESNET/libfds.git
WORKDIR /libfds/build
RUN cmake .. -DCMAKE_INSTALL_PREFIX=/usr && make && make install
WORKDIR /
RUN git clone https://github.com/CESNET/ipfixcol2.git 
WORKDIR /ipfixcol2/build
RUN cmake ..
RUN make
RUN make install

## # Set the working directory
## WORKDIR /app
## 
## # Copy your source code to the container
## COPY . .
## 
## # Build the application
## RUN cmake . && make
## 
## # Stage 2: Runtime environment
## FROM debian:bullseye-slim
## 
## # Install runtime dependencies
## # (Replace 'runtime-package-name' with your actual runtime dependencies)
## RUN apt-get update && apt-get install -y \
##     runtime-package-name
## 
## # Copy the built application from the previous stage
## COPY --from=builder /app/myapp /usr/local/bin/myapp
## 
## # Set the command to run your application
## CMD ["myapp"]
## 
