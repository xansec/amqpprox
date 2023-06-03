FROM ubuntu AS builder

RUN apt update -y && DEBIAN_FRONTEND=noninteractive apt install -y make cmake clang python3 python3-pip
RUN pip install "conan<2.0"

COPY . .
RUN make setup
RUN make init
RUN make build

FROM ubuntu

COPY --from=builder /build/Linux/bin/* /
