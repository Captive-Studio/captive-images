FROM ghcr.io/falcondev-oss/actions-runner:2.337.0@sha256:32a63e960641cde7df61ee56e18576d9781d3980f3e6461d379308b88ec5c036

COPY images/actions-runner/Aptfile /tmp/Aptfile

USER root

RUN apt-get update -qq && \
    apt-get install --no-install-recommends -y \
      $(grep -v '^#' /tmp/Aptfile | grep -v '^$' | tr '\n' ' ') && \
    rm -rf /var/lib/apt/lists/* /var/cache/apt/archives/* /tmp/Aptfile

USER runner
