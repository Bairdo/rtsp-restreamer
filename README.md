# RTSP Restreamer

Serve RTSP streams (e.g. From Security Cameras) and rewrap for HLS streaming (e.g. Webpage, or Chromecast).
Each stream is rewrapped in a Docker container running ffmpeg.

# Run

Set environment variables for camera streams to pull in 'restreamer/.env'

```bash
RTSP_USERNAME=username
RTSP_PASSWORD=SuperSecretPassword
RTSP_IP=10.0.0.1
RTSP_PORT=554
HTTP_PORT=8000
```

Add/remove streams via the encoder_*** services in docker-compose.yml

Start the docker instances

```bash
cd rtsp-Restreamer
docker-compose up --build --detach
```

You should then be able to access the webpage via http://SERVER_IP:HTTP_PORT e.g. http://192.168.1.2:8000

Or to use the HLS streams directly (e.g. With VLC) http://SERVER_IP:HTTP_PORT/hls/ch1/ch1.m3u8 e.g. http://192.168.1.2:8000/hls/ch1/ch1.m3u8

The 'ch1's can be changed to 'ch2' etc for a different stream (both need to be changed to the same thing e.g. .../hls/ch2/ch2.m38u).

The 'command' option in docker-compose for the encoders is 2 variables: A) The address of the stream to rewrap, and the name you want to give it. e.g. ch1. or lounge. You will then need to create a new volume for the encoder instance and webserver. (I think that should be all that is needed to use a different stream but I have not tested it.)

## TODO

- Chromecast Plugin for video.js
- Somehow stop the encoding if no one is streaming currently. (check the file access/requests on the webserver?)
- Prettify the webpage (Allow for different screen sizes: Desktop, Phone, etc)
