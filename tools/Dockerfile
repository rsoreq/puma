# Use this Dockerfile to create minimal reproductions of issues

FROM ruby:4.0@sha256:8400f102008d4e7322fbe610684312dfe1d1205550075c6c28834b5eb44afb97

# throw errors if Gemfile has been modified since Gemfile.lock
RUN bundle config --global frozen 1

WORKDIR /usr/src/app

COPY . .

RUN bundle install
RUN bundle exec rake compile

EXPOSE 9292
CMD bundle exec bin/puma test/rackup/hello.ru
