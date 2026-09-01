FROM ghcr.io/captive-studio/ruby-ci:4.0.6@sha256:43c38d37141dcca9a08ee1e0fb29ec2c6db7b9beed390aedd9c6d99f83495368

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
