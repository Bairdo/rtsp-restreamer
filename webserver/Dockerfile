FROM tiangolo/nginx-rtmp
RUN apt-get update && apt-get install -y ffmpeg

COPY . /www
WORKDIR /www
