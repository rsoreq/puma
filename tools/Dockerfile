# Use this Dockerfile to create minimal reproductions of issues

FROM ruby:3.4@sha256:48ecc7a76bacf6fc0da5f6c7a5b43f96461bac68fa571213a8afcf79c461c7b7

# throw errors if Gemfile has been modified since Gemfile.lock
RUN bundle config --global frozen 1

WORKDIR /usr/src/app

COPY . .

RUN bundle install
RUN bundle exec rake compile

EXPOSE 9292
CMD bundle exec bin/puma test/rackup/hello.ru
