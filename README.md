# ffmpeg Docker mod

This mod is intended to be used with images from linuxserver. More specifically, it was built to enable the ffmpeg features of the [lazylibrarian image](https://github.com/linuxserver/docker-lazylibrarian).

To use the mod, include it in the environment variable `DOCKER_MODS`. An example docker-compose file is shown below:

```yaml
version: "2.1"
services:
  lazylibrarian:
    image: linuxserver/lazylibrarian
    container_name: lazylibrarian
    environment:
      - PUID=1000
      - PGID=1000
      - TZ=Europe/London
      - DOCKER_MODS=linuxserver/calibre-web:calibre|mkerix/docker-ffmpeg-mod:latest
    volumes:
      - <path to data>:/config
      - <path to downloads>:/downloads
      - <path to data>:/books
    ports:
      - 5299:5299
    restart: unless-stopped
```