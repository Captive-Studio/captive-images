FROM ghcr.io/captive-studio/ruby-ci:4.0.6@sha256:642a12ef5cce62d7c651d05cfd506e72648925b6ec0febec7bec7485bc187aae

COPY images/rails-ci/Aptfile /tmp/Aptfile

RUN sudo apt-get update && \
    sudo apt-get install -y --no-install-recommends \
      $(grep -v '^#' /tmp/Aptfile | grep -v '^$' | tr '\n' ' ') && \
    sudo rm -rf /var/lib/apt/lists/* /var/cache/apt/archives/* /tmp/Aptfile
