FROM ghcr.io/falcondev-oss/actions-runner:2.336.0@sha256:b0cbd599b4124962a91930f85b0061adc5a5aaf874221d29741411fc661a259b

COPY images/actions-runner/Aptfile /tmp/Aptfile

USER root

RUN apt-get update -qq && \
    apt-get install --no-install-recommends -y \
      $(grep -v '^#' /tmp/Aptfile | grep -v '^$' | tr '\n' ' ') && \
    rm -rf /var/lib/apt/lists/* /var/cache/apt/archives/* /tmp/Aptfile

USER runner
