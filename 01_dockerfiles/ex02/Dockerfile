FROM ruby
LABEL maintainer  Patrice CADIOT <pathibul.r@gmail.com>

ADD . /opt/app

EXPOSE 3000
WORKDIR /opt/app
ONBUILD RUN bundle install && rails db:migrate && \
	rails db:seed 