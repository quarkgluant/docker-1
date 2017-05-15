FROM ruby:2.3.4
LABEL maintainer  Patrice CADIOT <pathibul.r@gmail.com>
RUN apt-get update && apt-get install -y nodejs && gem install rails -v 4.2.7 && mkdir -p /opt/app
ONBUILD WORKDIR /opt/app
ONBUILD ADD . /opt/app

ONBUILD EXPOSE 3000
ONBUILD RUN bundle install && rake db:migrate && \
	rake db:seed 