FROM ruby

# Install packages
RUN apt-get update  && apt-get install -y \
	nodejs
RUN gem install \ 
	rails

# Copy app 
ONBUILD COPY app /opt/app

# Install 
ONBUILD RUN bundle install
ONBUILD RUN rails db:migrate
ONBUILD RUN rails db:seed

# Set workdir 
WORKDIR /opt/app
