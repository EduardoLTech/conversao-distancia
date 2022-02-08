# conversao-distancia

Dockerfile

FROM python:3.8-slim-buster
WORKDIR /app
COPY requirements.txt .
RUN python -m pip install -r requirements.txt
COPY . /app
EXPOSE 5000
CMD [ "gunicorn", "--workers=3", "--bind", "0.0.0.0:5000", "app:app"]


docker image build -t teclinux/conversao-distancia:v1 .
docker container run -d -p 80:5000 teclinux/conversao-distancia:v1