FROM alpine
RUN apk update && apk add ffmpeg

COPY . /rtsp/
WORKDIR /rtsp
ENTRYPOINT ["/rtsp/rtsp-to-hls.sh"]
