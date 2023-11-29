Oude config van [[Raspberry PI 2B]] setup.

```yaml
version: "3"

services:

  homeassistant:
    image: "ghcr.io/home-assistant/home-assistant:stable"
    restart: unless-stopped
    privileged: true
    network_mode: host
    volumes:
      - ./homeassistant:/config
      - /etc/localtime:/etc/localtime:ro

  mqtt-broker:
    image: eclipse-mosquitto
    restart: unless-stopped
    volumes:
      - ./mosquitto/data:/mosquitto/data
      - ./mosquitto/credentials:/mosquitto/config/credentials
      - ./mosquitto/mosquitto.conf:/mosquitto/config/mosquitto.conf:ro
    ports:
      - "1883:1883" # MQTT protocol
      - "9001:9001" # webhooks

  zigbee2mqtt:
    image: koenkk/zigbee2mqtt
    restart: unless-stopped
    privileged: true
    user: 1000:1000
    group_add:
      - dialout 
    volumes:
      - ./z2m/data:/app/data
      - /run/udev:/run/udev:ro
    ports:
      - "8080:8080"     # webUI
    environment:
      - TZ=Europe/Amsterdam
    devices:
      - /dev/ttyACM0:/dev/ttyAMC0
```