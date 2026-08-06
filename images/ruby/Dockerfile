FROM ruby:4.0.6-slim@sha256:b6505477e3b9409e6786c9cc2facc0e7b3e0aab575c53ef4a92b4e61c0cdd983

COPY images/ruby/Aptfile /tmp/Aptfile

RUN apt-get update -qq && \
    apt-get install --no-install-recommends -y \
      $(grep -v '^#' /tmp/Aptfile | grep -v '^$' | tr '\n' ' ') && \
    rm -rf /var/lib/apt/lists /var/cache/apt/archives /tmp/Aptfile
