# Use this Dockerfile to create minimal reproductions of issues

FROM ruby:3.2@sha256:d3bcbd845d26ae1efafcc987f641aa9ac796267b9b857e0f196a2b05070c8330

# throw errors if Gemfile has been modified since Gemfile.lock
RUN bundle config --global frozen 1

WORKDIR /usr/src/app

COPY . .

RUN bundle install
RUN bundle exec rake compile

EXPOSE 9292
CMD bundle exec bin/puma test/rackup/hello.ru
