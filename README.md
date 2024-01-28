# Setup Splunk docker

**Source: https://docs.docker.com/config/containers/logging/splunk**

## 1. Config docker-compose file
```
version: "3.6"

services:
  splunk:
    image: splunk/splunk:9.0.5
    container_name: splunk
    environment:
      - SPLUNK_START_ARGS=--accept-license
      - SPLUNK_ENABLE_LISTEN=9997
      - SPLUNK_ADD=tcp 1514
      - SPLUNK_PASSWORD=xNTLAkOQRjgX12
    network_mode: "host"
    volumes:
      - ./splunk/etc:/opt/splunk/etc
      - ./splunk/var:/opt/splunk/var
```

## 2. Deploy docker-compose.yml
```
docker-compose up -d
```

## 3. Check container
```
docker ps | grep splunk
08ea0225cc61   splunk/splunk:9.0.5           "/sbin/entrypoint.sh…"   5 days ago   Up 5 days (healthy)                                                 splunk

```

## 4. Logs File
Log file location: ./splunk/var/log

```
tail -f ./splunk/var/log/splunk/splunkd_stderr.log
```
## 5. Go to http://localhost:8000 and see that splunk server is up

<img src="https://imgur.com/EoNUICA" />
