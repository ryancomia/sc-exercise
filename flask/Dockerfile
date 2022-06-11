# lets pull the official python image
FROM python:3.8

# set the working directory
WORKDIR /app

# copy over the packages inside the docker env
COPY . .

# install all required packages
RUN pip3 install -r requirements.txt

EXPOSE 9090

# initialize application server
#CMD ["uwsgi", "app.ini"]

CMD ["gunicorn", "-b", "0.0.0.0:9090", "app:app" ]