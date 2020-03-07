FROM circleci/golang:1.13.6

WORKDIR /app

# AWS cli
USER root
RUN apt-get update && \
    apt-get install -y \
        python3 \
        python3-pip \
        python3-setuptools \
        groff \
        less \
        ca-certificates \
    && pip3 install --upgrade pip \
    && apt-get clean
RUN pip3 --no-cache-dir install --upgrade awscli

USER circleci

# Go tooling
RUN go get github.com/gobuffalo/packr/v2/... && \
    go get github.com/tj/mmake/cmd/mmake && \
    GO111MODULE=on go get github.com/sonatype-nexus-community/nancy
