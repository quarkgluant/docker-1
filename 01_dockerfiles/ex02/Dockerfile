FROM ruby
LABEL maintainer  Patrice CADIOT <pathibul.r@gmail.com>
RUN gem install rails && mkdir -p /opt/app
ONBUILD WORKDIR /opt/app
ONBUILD ADD . /opt/app

ONBUILD EXPOSE 3000
ONBUILD RUN bundle install && rails db:migrate && \
	rails db:seed 