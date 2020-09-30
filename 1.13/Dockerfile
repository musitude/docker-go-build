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
    && apt-get install hugo \
    && apt-get clean
RUN pip3 --no-cache-dir install --upgrade awscli

RUN wget --quiet https://releases.hashicorp.com/terraform/0.12.13/terraform_0.12.13_linux_amd64.zip \
  && unzip terraform_0.12.13_linux_amd64.zip \
  && mv terraform /usr/bin \
  && rm terraform_0.12.13_linux_amd64.zip

# Allow circleci user to own /usr/local/include required by mmake
RUN chown -R circleci /usr/local/include

USER circleci

# Go tooling
RUN go get github.com/gobuffalo/packr/v2/... && \
    go get github.com/tj/mmake/cmd/mmake && \
    go get github.com/securego/gosec/cmd/gosec && \
    GO111MODULE=on go get github.com/sonatype-nexus-community/nancy
