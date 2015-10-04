# Dockerfile to have a Jekyll env.
# This assumes a volume is mounted with the contents.
#
FROM debian:latest

VOLUME /www

RUN DEBIAN_FRONTEND=noninteractive \
    apt-get update && apt-get upgrade -y && \
    apt-get install ruby ruby-dev -y && \
    apt-get install ruby-redcloth ruby-json -y && \
    apt-get install make gcc liblz-dev libxml2 zlib1g-dev -y && \
    apt-get install ruby-nokogiri bundler ruby-execjs -y && \
    apt-get clean

COPY Gemfile /root/
RUN cd /root; bundle install


EXPOSE 4000
CMD cd /www; bundle exec jekyll serve
