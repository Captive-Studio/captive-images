FROM ghcr.io/captive-studio/ruby-ci:4.0.6@sha256:67f03b12fdcfad87a17ea8501e082f60b8db5a1d4c7411080b8243763b79e114

COPY images/rails-ci/Aptfile /tmp/Aptfile

RUN sudo apt-get update && \
    sudo apt-get install -y --no-install-recommends \
      $(grep -v '^#' /tmp/Aptfile | grep -v '^$' | tr '\n' ' ') && \
    sudo rm -rf /var/lib/apt/lists/* /var/cache/apt/archives/* /tmp/Aptfile

COPY --chown=circleci:circleci \
  images/rails-ci/Gemfile \
  images/rails-ci/Gemfile.lock \
  /tmp/rails-ci-gems/

RUN cd /tmp/rails-ci-gems && \
    bundle config set frozen true && \
    bundle install && \
    brakeman --version && \
    rm -rf /tmp/rails-ci-gems
