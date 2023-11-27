## Nieuwe setup
HASS OS met twee add-ons:
* [[Mosquitto]]
* [[Zigbee2MQTT]]
op [[Raspberry PI 4B]] met een [[Conbee II]] stick

### Stappen
1. Flashen van geheugenkaart met Homeassistant OS
2. [[Raspberry PI 4B]] koppelen aan LAN-kabel, [[Conbee II]] en stroom
3. IP achterhalen en inloggen via app of browser
4. Zigbee devices, zha, Conbee II negeren
5. Add-on [[Mosquitto]] installeren
6. Add-on [[Zigbee2MQTT]] installeren
7. Add-on [[Zigbee2MQTT]] configureren
	* radio: deconz, port ...?
8. Alles pairen
9. Backup maken

## Oude setup
[[Docker compose]] voor drie containers:
* [[Home Assistant]]
* [[Mosquitto]]
* [[Zigbee2MQTT]]
Op [[Raspberry PI 2B]]

Gestopt vanwege corrupte microSD