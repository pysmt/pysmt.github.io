# Dockerfile to have a Jekyll env.
#
# By default, this will serve the content on :4000. Run with:
#   docker run --rm -ti -p 4000:4000 -v /<git-repo>:/www jekyll .
# Assuming this image has been tagged as jekyll
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
