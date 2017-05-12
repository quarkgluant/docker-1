FROM ruby
MAINTAINER Patrice CADIOT <pathibul.r@gmail.com>

ADD /Users/pcadiot/Ruby-exercism/day_07/ex00/acme /opt/app

EXPOSE 3000
WORKDIR /opt/app
ONBUILD RUN bundle install && rails db:migrate && \
	rails db:seed 