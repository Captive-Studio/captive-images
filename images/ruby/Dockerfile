FROM ruby:4.0.6-slim@sha256:607bf92fa7ecebb4a0c6654b62cb44c48d94b36b6f5a754611ddbbe3dc5b6135

COPY images/ruby/Aptfile /tmp/Aptfile

RUN apt-get update -qq && \
    apt-get install --no-install-recommends -y \
      $(grep -v '^#' /tmp/Aptfile | grep -v '^$' | tr '\n' ' ') && \
    rm -rf /var/lib/apt/lists /var/cache/apt/archives /tmp/Aptfile
