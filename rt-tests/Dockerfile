ARG IMAGE_ARCH=linux/amd64
ARG IMAGE_TAG=20.04
FROM --platform=$IMAGE_ARCH ubuntu:$IMAGE_TAG

RUN apt-get update \
    && apt-get install -y --no-install-recommends gnuplot rt-tests \
    && rm -rf /var/lib/apt/lists/*
 
COPY ./rt-tests.sh /rt-tests.sh

CMD ["sh", "-c", "/rt-tests.sh ${label}"]
