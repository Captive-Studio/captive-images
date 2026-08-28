FROM ruby:4.0.6-slim@sha256:58479f164d5947f852da27a4436c89bb986a811f959c40552bc7f6ccaabcc9c9

COPY images/ruby/Aptfile /tmp/Aptfile

RUN apt-get update -qq && \
    apt-get install --no-install-recommends -y \
      $(grep -v '^#' /tmp/Aptfile | grep -v '^$' | tr '\n' ' ') && \
    rm -rf /var/lib/apt/lists /var/cache/apt/archives /tmp/Aptfile
