# lets pull the official python image
FROM python:3.8

# set the working directory
WORKDIR /app

# copy over the packages inside the docker env
COPY . .

# install all required packages
RUN pip install -r requirements.txt

# logical exposing of port
EXPOSE 9090

# initialize application server
CMD ["uwsgi", "app.ini"]