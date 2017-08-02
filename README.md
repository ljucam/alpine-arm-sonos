# docker-node-sonos-http-api
Docker wrapper for https://github.com/jishi/node-sonos-http-api with Alpine Linux (armhf).

## Usage
Create the following direcotries on your docker host:
```
<dir>/clips
<dir>/settings
<dir>/cache
<dir>/presets
```

Perform the following steps to prepare your newly created directories:
```shell
curl https://raw.githubusercontent.com/jishi/node-sonos-http-api/master/presets/example.json > <dir>/presets/example.json
echo {} > <dir>/settings/settings.json
```

Run the image with docker-compose:
```yaml
version: "3"
services:
  sonos:
    image: quay.io/almighty/sonos:1.0.0
    ports: 
      - "5005:5005"
    network_mode: "host"
    volumes:
      - <dir>/clips:/app/clips
      - <dir>/settings:/app/settings
      - <dir>/cache:/app/cache
      - <dir>/presets:/app/presets
```

Command:
```shell
docker-compose -f myDockerCompose.yaml up -d
```
