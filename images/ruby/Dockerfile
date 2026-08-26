FROM ruby:4.0.6-slim@sha256:901e9c09db7b5e7e19af81799a7dd743c89f9c5fc93dc0038f899e9131c80b5b

COPY images/ruby/Aptfile /tmp/Aptfile

RUN apt-get update -qq && \
    apt-get install --no-install-recommends -y \
      $(grep -v '^#' /tmp/Aptfile | grep -v '^$' | tr '\n' ' ') && \
    rm -rf /var/lib/apt/lists /var/cache/apt/archives /tmp/Aptfile
