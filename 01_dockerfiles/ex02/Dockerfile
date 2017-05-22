FROM ruby:2.3.4
LABEL maintainer  Patrice CADIOT <pathibul.r@gmail.com>
RUN apt-get update && apt-get install -y nodejs && gem install rails -v 4.2.7 && mkdir -p /opt/app
ONBUILD WORKDIR /opt/app
ONBUILD ADD . /opt/app

ONBUILD EXPOSE 3000
ONBUILD RUN bundle install && rake db:migrate && \
	rake db:seed 
# pour tester, il faut une app rails dans laquelle il y aura un Dockerfile tel
# FROM ft-rails-on-build
# CMD ["rails", "s", "-b", "0.0.0.0"]

# on build d'abord ce Dockerfile (rendu de l'exo), situé à l'extérieur du dossier de l'app
# puis le "mini" Dockerfile dans l'app
# puis on teste
# # docker run -d -p 3000:3000 ft-rails