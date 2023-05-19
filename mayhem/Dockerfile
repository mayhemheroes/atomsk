# Build Stage:
FROM --platform=linux/amd64 ubuntu:20.04 as builder

## Install build dependencies.
RUN apt-get update &&  DEBIAN_FRONTEND=noninteractive apt-get install -y build-essential gfortran liblapack-dev

## Add Source Code
ADD etc /etc
ADD examples /examples
ADD src /src
WORKDIR src

## Build Step
RUN make atomsk

# Package Stage
FROM --platform=linux/amd64 ubuntu:20.04
COPY --from=builder /src/atomsk /
RUN apt-get update && apt-get install -y liblapack-dev libgomp1
