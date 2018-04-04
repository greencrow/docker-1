FROM ruby

# Install packages
RUN apt-get update  && apt-get install -y \
	nodejs
RUN gem install \ 
	rails

# Copy app 
ONBUILD ADD . /opt/app
WORKDIR /opt/app

# Install 
ONBUILD RUN bundle install
ONBUILD RUN rake db:migrate
ONBUILD RUN rake db:setup
ONBUILD RUN rake db:seed

# Port
ONBUILD EXPOSE 3000

# To test it: first create an ruby app folder with a Dockerfile inside
# This Dockerfile should countain: 
#	FROM ft_rails:latest
#	EXPOSE 3000
#	CMD ["rails", "s", "-b", "0.0.0.0", "-p", "3000"]
# Then build THIS dockerfile with
#	docker build . -t ft_rails
# Then build the Dockerfile INSIDE the app folder 
#	docker build . -t app
# Run with 
#	docker run -p 3000:3000 app
