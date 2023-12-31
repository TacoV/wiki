```json
{
	"commit": "unknown",
	"config": {
		"advanced": {
			"adapter_concurrent": null,
			"adapter_delay": null,
			"availability_blacklist": [],
			"availability_blocklist": [],
			"availability_passlist": [],
			"availability_whitelist": [],
			"cache_state": true,
			"cache_state_persistent": true,
			"cache_state_send_on_startup": true,
			"channel": 11,
			"elapsed": false,
			"ext_pan_id": [
				136,
				80,
				35,
				134,
				223,
				39,
				90,
				236
			],
			"last_seen": "disable",
			"legacy_api": true,
			"legacy_availability_payload": true,
			"log_directory": "/config/zigbee2mqtt/log/%TIMESTAMP%",
			"log_file": "log.txt",
			"log_level": "info",
			"log_output": [
				"console",
				"file"
			],
			"log_rotation": true,
			"log_symlink_current": false,
			"log_syslog": {},
			"output": "json",
			"pan_id": 58110,
			"report": false,
			"soft_reset_timeout": 0,
			"timestamp_format": "YYYY-MM-DD HH:mm:ss"
		},
		"blocklist": [],
		"device_options": {},
		"devices": {
			"0x000000000175291f": {
				"friendly_name": "Lichtknoppen"
			},
			"0x001788010be7a123": {
				"friendly_name": "Speelhoek",
				"transition": 1
			},
			"0x001788010c68440e": {
				"friendly_name": "Bank"
			},
			"0x9035eafffe1a1386": {
				"friendly_name": "Tafel raam"
			},
			"0x9035eafffe20aad0": {
				"friendly_name": "Spotje bed"
			},
			"0x9035eafffe243304": {
				"friendly_name": "Tafel trap"
			},
			"0x9035eafffe2ab921": {
				"friendly_name": "Spotje kast"
			},
			"0x9035eafffe2cf495": {
				"friendly_name": "Spotje muur"
			},
			"0x9035eafffe44c1db": {
				"friendly_name": "Tafel midden"
			}
		},
		"external_converters": [],
		"frontend": {
			"host": "0.0.0.0",
			"port": 8099
		},
		"groups": {},
		"homeassistant": {
			"discovery_topic": "homeassistant",
			"legacy_entity_attributes": true,
			"legacy_triggers": true,
			"status_topic": "hass/status"
		},
		"map_options": {
			"graphviz": {
				"colors": {
					"fill": {
						"coordinator": "#e04e5d",
						"enddevice": "#fff8ce",
						"router": "#4ea3e0"
					},
					"font": {
						"coordinator": "#ffffff",
						"enddevice": "#000000",
						"router": "#ffffff"
					},
					"line": {
						"active": "#009900",
						"inactive": "#994444"
					}
				}
			}
		},
		"mqtt": {
			"base_topic": "zigbee2mqtt",
			"force_disable_retain": false,
			"include_device_information": false,
			"server": "mqtt://core-mosquitto:1883",
			"user": "addons"
		},
		"ota": {
			"disable_automatic_update_check": false,
			"update_check_interval": 1440
		},
		"passlist": [],
		"permit_join": true,
		"serial": {
			"adapter": "deconz",
			"disable_led": false,
			"port": "/dev/ttyACM0"
		}
	},
	"config_schema": {
		"definitions": {
			"device": {
				"properties": {
					"debounce": {
						"description": "Debounces messages of this device",
						"title": "Debounce",
						"type": "number"
					},
					"debounce_ignore": {
						"description": "Protects unique payload values of specified payload properties from overriding within debounce time",
						"examples": [
							"action"
						],
						"items": {
							"type": "string"
						},
						"title": "Ignore debounce",
						"type": "array"
					},
					"disabled": {
						"description": "Disables the device (excludes device from network scans, availability and group state updates)",
						"requiresRestart": true,
						"title": "Disabled",
						"type": "boolean"
					},
					"filtered_attributes": {
						"description": "Filter attributes with regex from published payload.",
						"examples": [
							"^temperature$",
							"^battery$",
							"^action$"
						],
						"items": {
							"type": "string"
						},
						"title": "Filtered publish attributes",
						"type": "array"
					},
					"filtered_cache": {
						"description": "Filter attributes with regex from being added to the cache, this prevents the attribute from being in the published payload when the value didn't change.",
						"examples": [
							"^input_actions$"
						],
						"items": {
							"type": "string"
						},
						"title": "Filtered attributes from cache",
						"type": "array"
					},
					"filtered_optimistic": {
						"description": "Filter attributes with regex from optimistic publish payload when calling /set. (This has no effect if optimistic is set to false).",
						"examples": [
							"^color_(mode|temp)$",
							"color"
						],
						"items": {
							"type": "string"
						},
						"title": "Filtered optimistic attributes",
						"type": "array"
					},
					"friendly_name": {
						"description": "Used in the MQTT topic of a device. By default this is the device ID",
						"readOnly": true,
						"title": "Friendly name",
						"type": "string"
					},
					"homeassistant": {
						"properties": {
							"name": {
								"description": "Name of the device in Home Assistant",
								"title": "Home Assistant name",
								"type": "string"
							}
						},
						"title": "Home Assistant",
						"type": [
							"object",
							"null"
						]
					},
					"icon": {
						"description": "The user-defined device icon for the frontend. It can be a full URL link to an image (e.g. https://SOME.SITE/MODEL123.jpg) (you cannot use a path to a local file) or base64 encoded data URL (e.g. image/svg+xml;base64,PHN2ZyB3aW....R0aD)",
						"title": "Icon",
						"type": "string"
					},
					"optimistic": {
						"default": true,
						"description": "Publish optimistic state after set",
						"title": "Optimistic",
						"type": "boolean"
					},
					"qos": {
						"description": "QoS level for MQTT messages of this device",
						"title": "QoS",
						"type": "number"
					},
					"retain": {
						"description": "Retain MQTT messages of this device",
						"title": "Retain",
						"type": "boolean"
					},
					"retention": {
						"description": "Sets the MQTT Message Expiry in seconds, Make sure to set mqtt.version to 5",
						"title": "Retention",
						"type": "number"
					}
				},
				"required": [
					"friendly_name"
				],
				"type": "object"
			},
			"group": {
				"properties": {
					"devices": {
						"items": {
							"type": "string"
						},
						"type": "array"
					},
					"filtered_attributes": {
						"items": {
							"type": "string"
						},
						"type": "array"
					},
					"friendly_name": {
						"type": "string"
					},
					"off_state": {
						"default": "auto",
						"description": "Control when to publish state OFF for a group. 'all_members_off': only publish state OFF when all group members are in state OFF, 'last_member_state': publish state OFF whenever one of its members changes to OFF",
						"enum": [
							"all_members_off",
							"last_member_state"
						],
						"requiresRestart": true,
						"title": "Group off state",
						"type": [
							"string"
						]
					},
					"optimistic": {
						"type": "boolean"
					},
					"qos": {
						"type": "number"
					},
					"retain": {
						"type": "boolean"
					}
				},
				"required": [
					"friendly_name"
				],
				"type": "object"
			}
		},
		"properties": {
			"advanced": {
				"properties": {
					"adapter_concurrent": {
						"description": "Adapter concurrency (e.g. 2 for CC2531 or 16 for CC26X2R1) (default: null, uses recommended value)",
						"requiresRestart": true,
						"title": "Adapter concurrency",
						"type": [
							"number",
							"null"
						]
					},
					"adapter_delay": {
						"description": "Adapter delay",
						"requiresRestart": true,
						"title": "Adapter delay",
						"type": [
							"number",
							"null"
						]
					},
					"cache_state": {
						"default": true,
						"description": "MQTT message payload will contain all attributes, not only changed ones. Has to be true when integrating via Home Assistant",
						"title": "Cache state",
						"type": "boolean"
					},
					"cache_state_persistent": {
						"default": true,
						"description": "Persist cached state, only used when cache_state: true",
						"title": "Persist cache state",
						"type": "boolean"
					},
					"cache_state_send_on_startup": {
						"default": true,
						"description": "Send cached state on startup, only used when cache_state: true",
						"title": "Send cached state on startup",
						"type": "boolean"
					},
					"channel": {
						"default": 11,
						"description": "Zigbee channel, changing requires repairing all devices! (Note: use a ZLL channel: 11, 15, 20, or 25 to avoid Problems)",
						"examples": [
							15,
							20,
							25
						],
						"maximum": 26,
						"minimum": 11,
						"requiresRestart": true,
						"title": "ZigBee channel",
						"type": "number"
					},
					"elapsed": {
						"default": false,
						"description": "Add an elapsed attribute to MQTT messages, contains milliseconds since the previous msg",
						"title": "Elapsed",
						"type": "boolean"
					},
					"ext_pan_id": {
						"description": "Zigbee extended pan ID, changing requires repairing all devices!",
						"oneOf": [
							{
								"title": "Extended pan ID (string)",
								"type": "string"
							},
							{
								"items": {
									"type": "number"
								},
								"title": "Extended pan ID (array)",
								"type": "array"
							}
						],
						"requiresRestart": true,
						"title": "Ext Pan ID"
					},
					"last_seen": {
						"default": "disable",
						"description": "Add a last_seen attribute to MQTT messages, contains date/time of last Zigbee message",
						"enum": [
							"disable",
							"ISO_8601",
							"ISO_8601_local",
							"epoch"
						],
						"title": "Last seen",
						"type": "string"
					},
					"legacy_api": {
						"default": true,
						"description": "Disables the legacy api (false = disable)",
						"requiresRestart": true,
						"title": "Legacy API",
						"type": "boolean"
					},
					"legacy_availability_payload": {
						"default": true,
						"description": "Payload to be used for device availability and bridge/state topics. true = text, false = JSON",
						"requiresRestart": true,
						"title": "Legacy availability payload",
						"type": "boolean"
					},
					"log_directory": {
						"description": "Location of log directory",
						"examples": [
							"data/log/%TIMESTAMP%"
						],
						"requiresRestart": true,
						"title": "Log directory",
						"type": "string"
					},
					"log_file": {
						"default": "log.txt",
						"description": "Log file name, can also contain timestamp",
						"examples": [
							"zigbee2mqtt_%TIMESTAMP%.log"
						],
						"requiresRestart": true,
						"title": "Log file",
						"type": "string"
					},
					"log_level": {
						"default": "info",
						"description": "Logging level",
						"enum": [
							"info",
							"warn",
							"error",
							"debug"
						],
						"title": "Log level",
						"type": "string"
					},
					"log_output": {
						"description": "Output location of the log, leave empty to suppress logging",
						"items": {
							"enum": [
								"console",
								"file",
								"syslog"
							],
							"type": "string"
						},
						"requiresRestart": true,
						"title": "Log output",
						"type": "array"
					},
					"log_rotation": {
						"default": true,
						"description": "Log rotation",
						"requiresRestart": true,
						"title": "Log rotation",
						"type": "boolean"
					},
					"log_symlink_current": {
						"default": false,
						"description": "Create symlink to current logs in the log directory",
						"requiresRestart": true,
						"title": "Log symlink current",
						"type": "boolean"
					},
					"log_syslog": {
						"properties": {
							"app_name": {
								"default": "Zigbee2MQTT",
								"description": "The name of the application (Default: Zigbee2MQTT).",
								"title": "Localhost",
								"type": "string"
							},
							"eol": {
								"default": "/n",
								"description": "The end of line character to be added to the end of the message (Default: Message without modifications).",
								"title": "eol",
								"type": "string"
							},
							"host": {
								"default": "localhost",
								"description": "The host running syslogd, defaults to localhost.",
								"title": "Host",
								"type": "string"
							},
							"localhost": {
								"default": "localhost",
								"description": "Host to indicate that log messages are coming from (Default: localhost).",
								"title": "Localhost",
								"type": "string"
							},
							"path": {
								"default": "/dev/log",
								"description": "The path to the syslog dgram socket (i.e. /dev/log or /var/run/syslog for OS X).",
								"examples": [
									"/var/run/syslog"
								],
								"title": "Path",
								"type": "string"
							},
							"pid": {
								"default": "process.pid",
								"description": "PID of the process that log messages are coming from (Default process.pid).",
								"title": "PID",
								"type": "string"
							},
							"port": {
								"default": 514,
								"description": "The port on the host that syslog is running on, defaults to syslogd's default port.",
								"title": "Port",
								"type": "number"
							},
							"protocol": {
								"default": "udp4",
								"description": "The network protocol to log over (e.g. tcp4, udp4, tls4, unix, unix-connect, etc).",
								"examples": [
									"udp4",
									"tls4",
									"unix",
									"unix-connect"
								],
								"title": "Protocol",
								"type": "string"
							},
							"type": {
								"default": "5424",
								"description": "The type of the syslog protocol to use (Default: BSD, also valid: 5424).",
								"title": "Type",
								"type": "string"
							}
						},
						"title": "syslog",
						"type": "object"
					},
					"network_key": {
						"description": "Network encryption key, changing requires repairing all devices!",
						"oneOf": [
							{
								"title": "Network key(string)",
								"type": "string"
							},
							{
								"items": {
									"type": "number"
								},
								"title": "Network key(array)",
								"type": "array"
							}
						],
						"requiresRestart": true,
						"title": "Network key"
					},
					"output": {
						"description": "Examples when 'state' of a device is published json: topic: 'zigbee2mqtt/my_bulb' payload '{\"state\": \"ON\"}' attribute: topic 'zigbee2mqtt/my_bulb/state' payload 'ON' attribute_and_json: both json and attribute (see above)",
						"enum": [
							"attribute_and_json",
							"attribute",
							"json"
						],
						"title": "MQTT output type",
						"type": "string"
					},
					"pan_id": {
						"description": "ZigBee pan ID, changing requires repairing all devices!",
						"oneOf": [
							{
								"title": "Pan ID (string)",
								"type": "string"
							},
							{
								"title": "Pan ID (number)",
								"type": "number"
							}
						],
						"requiresRestart": true,
						"title": "Pan ID"
					},
					"timestamp_format": {
						"description": "Log timestamp format",
						"examples": [
							"YYYY-MM-DD HH:mm:ss"
						],
						"requiresRestart": true,
						"title": "Timestamp format",
						"type": "string"
					},
					"transmit_power": {
						"description": "Transmit power of adapter, only available for Z-Stack (CC253*/CC2652/CC1352) adapters, CC2652 = 5dbm, CC1352 max is = 20dbm (5dbm default)",
						"requiresRestart": true,
						"title": "Transmit power",
						"type": [
							"number",
							"null"
						]
					}
				},
				"title": "Advanced",
				"type": "object"
			},
			"availability": {
				"description": "Checks whether devices are online/offline",
				"oneOf": [
					{
						"title": "Availability (simple)",
						"type": "boolean"
					},
					{
						"properties": {
							"active": {
								"description": "Options for active devices (routers/mains powered)",
								"properties": {
									"timeout": {
										"default": 10,
										"description": "Time after which an active device will be marked as offline in minutes",
										"requiresRestart": true,
										"title": "Timeout",
										"type": "number"
									}
								},
								"requiresRestart": true,
								"title": "Active",
								"type": "object"
							},
							"passive": {
								"description": "Options for passive devices (mostly battery powered)",
								"properties": {
									"timeout": {
										"default": 1500,
										"description": "Time after which an passive device will be marked as offline in minutes",
										"requiresRestart": true,
										"title": "Timeout",
										"type": "number"
									}
								},
								"requiresRestart": true,
								"title": "Passive",
								"type": "object"
							}
						},
						"title": "Availability (advanced)",
						"type": "object"
					}
				],
				"requiresRestart": true,
				"title": "Availability"
			},
			"ban": {
				"items": {
					"type": "string"
				},
				"readOnly": true,
				"requiresRestart": true,
				"title": "Ban (deprecated, use blocklist)",
				"type": "array"
			},
			"blocklist": {
				"description": "Block devices from the network (by ieeeAddr)",
				"items": {
					"type": "string"
				},
				"requiresRestart": true,
				"title": "Blocklist",
				"type": "array"
			},
			"device_options": {
				"title": "Options that are applied to all devices",
				"type": "object"
			},
			"devices": {
				"patternProperties": {
					"^.*$": {
						"$ref": "#/definitions/device"
					}
				},
				"propertyNames": {
					"pattern": "^0x[\\d\\w]{16}$"
				},
				"type": "object"
			},
			"external_converters": {
				"description": "You can define external converters to e.g. add support for a DiY device",
				"examples": [
					"DIYRuZ_FreePad.js"
				],
				"items": {
					"type": "string"
				},
				"requiresRestart": true,
				"title": "External converters",
				"type": "array"
			},
			"frontend": {
				"oneOf": [
					{
						"title": "Frontend (simple)",
						"type": "boolean"
					},
					{
						"properties": {
							"auth_token": {
								"description": "Enables authentication, disabled by default",
								"requiresRestart": true,
								"title": "Auth token",
								"type": [
									"string",
									"null"
								]
							},
							"host": {
								"default": "0.0.0.0",
								"description": "Frontend binding host. Binds to a unix socket when an absolute path is given instead.",
								"examples": [
									"127.0.0.1",
									"/run/zigbee2mqtt/zigbee2mqtt.sock"
								],
								"requiresRestart": true,
								"title": "Bind host",
								"type": "string"
							},
							"port": {
								"default": 8080,
								"description": "Frontend binding port. Ignored when using a unix domain socket",
								"requiresRestart": true,
								"title": "Port",
								"type": "number"
							},
							"ssl_cert": {
								"description": "SSL Certificate file path for exposing HTTPS. The sibling property 'ssl_key' must be set for HTTPS to be activated.",
								"requiresRestart": true,
								"title": "Certificate file path",
								"type": [
									"string",
									"null"
								]
							},
							"ssl_key": {
								"description": "SSL key file path for exposing HTTPS. The sibling property 'ssl_cert' must be set for HTTPS to be activated.",
								"requiresRestart": true,
								"title": "key file path",
								"type": [
									"string",
									"null"
								]
							},
							"url": {
								"description": "URL on which the frontend can be reached, currently only used for the Home Assistant device configuration page",
								"requiresRestart": true,
								"title": "URL",
								"type": [
									"string",
									"null"
								]
							}
						},
						"title": "Frontend (advanced)",
						"type": "object"
					}
				],
				"requiresRestart": true,
				"title": "Frontend"
			},
			"groups": {
				"patternProperties": {
					"^.*$": {
						"$ref": "#/definitions/group"
					}
				},
				"propertyNames": {
					"pattern": "^[\\w].*$"
				},
				"type": "object"
			},
			"homeassistant": {
				"default": false,
				"description": "Home Assistant integration (MQTT discovery)",
				"oneOf": [
					{
						"title": "Home Assistant (simple)",
						"type": "boolean"
					},
					{
						"properties": {
							"discovery_topic": {
								"description": "Home Assistant discovery topic",
								"examples": [
									"homeassistant"
								],
								"requiresRestart": true,
								"title": "Homeassistant discovery topic",
								"type": "string"
							},
							"legacy_entity_attributes": {
								"default": true,
								"description": "Home Assistant legacy entity attributes, when enabled Zigbee2MQTT will add state attributes to each entity, additional to the separate entities and devices it already creates",
								"title": "Home Assistant legacy entity attributes",
								"type": "boolean"
							},
							"legacy_triggers": {
								"default": true,
								"description": "Home Assistant legacy triggers, when enabled Zigbee2mqt will send an empty 'action' or 'click' after one has been send. A 'sensor_action' and 'sensor_click' will be discoverd",
								"title": "Home Assistant legacy triggers",
								"type": "boolean"
							},
							"status_topic": {
								"description": "Home Assistant status topic",
								"examples": [
									"homeassistant/status"
								],
								"requiresRestart": true,
								"title": "Home Assistant status topic",
								"type": "string"
							}
						},
						"title": "Home Assistant (advanced)",
						"type": "object"
					}
				],
				"requiresRestart": true,
				"title": "Home Assistant integration"
			},
			"map_options": {
				"properties": {
					"graphviz": {
						"properties": {
							"colors": {
								"properties": {
									"fill": {
										"properties": {
											"coordinator": {
												"type": "string"
											},
											"enddevice": {
												"type": "string"
											},
											"router": {
												"type": "string"
											}
										},
										"type": "object"
									},
									"font": {
										"properties": {
											"coordinator": {
												"type": "string"
											},
											"enddevice": {
												"type": "string"
											},
											"router": {
												"type": "string"
											}
										},
										"type": "object"
									},
									"line": {
										"properties": {
											"active": {
												"type": "string"
											},
											"inactive": {
												"type": "string"
											}
										},
										"type": "object"
									}
								},
								"type": "object"
							}
						},
						"type": "object"
					}
				},
				"title": "Networkmap",
				"type": "object"
			},
			"mqtt": {
				"properties": {
					"base_topic": {
						"default": "zigbee2mqtt",
						"description": "MQTT base topic for Zigbee2MQTT MQTT messages",
						"examples": [
							"zigbee2mqtt"
						],
						"requiresRestart": true,
						"title": "Base topic",
						"type": "string"
					},
					"ca": {
						"description": "Absolute path to SSL/TLS certificate of CA used to sign server and client certificates",
						"examples": [
							"/etc/ssl/mqtt-ca.crt"
						],
						"requiresRestart": true,
						"title": "Certificate authority",
						"type": "string"
					},
					"cert": {
						"description": "Absolute path to SSL/TLS certificate for client-authentication",
						"examples": [
							"/etc/ssl/mqtt-client.crt"
						],
						"requiresRestart": true,
						"title": "SSL/TLS certificate",
						"type": "string"
					},
					"client_id": {
						"description": "MQTT client ID",
						"examples": [
							"MY_CLIENT_ID"
						],
						"requiresRestart": true,
						"title": "Client ID",
						"type": "string"
					},
					"force_disable_retain": {
						"default": false,
						"description": "Disable retain for all send messages. ONLY enable if you MQTT broker doesn't support retained message (e.g. AWS IoT core, Azure IoT Hub, Google Cloud IoT core, IBM Watson IoT Platform). Enabling will break the Home Assistant integration",
						"requiresRestart": true,
						"title": "Force disable retain",
						"type": "boolean"
					},
					"include_device_information": {
						"default": false,
						"description": "Include device information to mqtt messages",
						"title": "Include device information",
						"type": "boolean"
					},
					"keepalive": {
						"default": 60,
						"description": "MQTT keepalive in second",
						"requiresRestart": true,
						"title": "Keepalive",
						"type": "number"
					},
					"key": {
						"description": "Absolute path to SSL/TLS key for client-authentication",
						"examples": [
							"/etc/ssl/mqtt-client.key"
						],
						"requiresRestart": true,
						"title": "SSL/TLS key",
						"type": "string"
					},
					"password": {
						"description": "MQTT server authentication password",
						"examples": [
							"ILOVEPELMENI"
						],
						"requiresRestart": true,
						"title": "Password",
						"type": "string"
					},
					"reject_unauthorized": {
						"default": true,
						"description": "Disable self-signed SSL certificate",
						"requiresRestart": true,
						"title": "Reject unauthorized",
						"type": "boolean"
					},
					"server": {
						"description": "MQTT server URL (use mqtts:// for SSL/TLS connection)",
						"examples": [
							"mqtt://localhost:1883"
						],
						"requiresRestart": true,
						"title": "MQTT server",
						"type": "string"
					},
					"user": {
						"description": "MQTT server authentication user",
						"examples": [
							"johnnysilverhand"
						],
						"requiresRestart": true,
						"title": "User",
						"type": "string"
					},
					"version": {
						"default": 4,
						"description": "MQTT protocol version",
						"examples": [
							5
						],
						"requiresRestart": true,
						"title": "Version",
						"type": [
							"number",
							"null"
						]
					}
				},
				"required": [
					"server"
				],
				"title": "MQTT",
				"type": "object"
			},
			"ota": {
				"properties": {
					"disable_automatic_update_check": {
						"default": false,
						"description": "Zigbee devices may request a firmware update, and do so frequently, causing Zigbee2MQTT to reach out to third party servers. If you disable these device initiated checks, you can still initiate a firmware update check manually.",
						"title": "Disable automatic update check",
						"type": "boolean"
					},
					"ikea_ota_use_test_url": {
						"default": false,
						"description": "Use IKEA TRADFRI OTA test server, see OTA updates documentation",
						"requiresRestart": true,
						"title": "IKEA TRADFRI OTA use test url",
						"type": "boolean"
					},
					"update_check_interval": {
						"default": 1440,
						"description": "Your device may request a check for a new firmware update. This value determines how frequently third party servers may actually be contacted to look for firmware updates. The value is set in minutes, and the default is 1 day.",
						"title": "Update check interval",
						"type": "number"
					},
					"zigbee_ota_override_index_location": {
						"description": "Location of override OTA index file",
						"examples": [
							"index.json"
						],
						"requiresRestart": true,
						"title": "OTA index override file name",
						"type": "string"
					}
				},
				"title": "OTA updates",
				"type": "object"
			},
			"passlist": {
				"description": "Allow only certain devices to join the network (by ieeeAddr). Note that all devices not on the passlist will be removed from the network!",
				"items": {
					"type": "string"
				},
				"requiresRestart": true,
				"title": "Passlist",
				"type": "array"
			},
			"permit_join": {
				"default": false,
				"description": "Allow new devices to join (re-applied at restart)",
				"title": "Permit join",
				"type": "boolean"
			},
			"serial": {
				"properties": {
					"adapter": {
						"default": "auto",
						"description": "Adapter type, not needed unless you are experiencing problems",
						"enum": [
							"deconz",
							"zstack",
							"zigate",
							"ezsp",
							"auto"
						],
						"requiresRestart": true,
						"title": "Adapter",
						"type": [
							"string"
						]
					},
					"baudrate": {
						"description": "Baud rate speed for serial port, this can be anything firmware support but default is 115200 for Z-Stack and EZSP, 38400 for Deconz, however note that some EZSP firmware need 57600",
						"examples": [
							38400,
							57600,
							115200
						],
						"requiresRestart": true,
						"title": "Baudrate",
						"type": "number"
					},
					"disable_led": {
						"default": false,
						"description": "Disable LED of the adapter if supported",
						"requiresRestart": true,
						"title": "Disable led",
						"type": "boolean"
					},
					"port": {
						"description": "Location of the adapter. To autodetect the port, set null",
						"examples": [
							"/dev/ttyACM0"
						],
						"requiresRestart": true,
						"title": "Port",
						"type": [
							"string",
							"null"
						]
					},
					"rtscts": {
						"description": "RTS / CTS Hardware Flow Control for serial port",
						"requiresRestart": true,
						"title": "RTS / CTS",
						"type": "boolean"
					}
				},
				"title": "Serial",
				"type": "object"
			},
			"whitelist": {
				"items": {
					"type": "string"
				},
				"readOnly": true,
				"requiresRestart": true,
				"title": "Whitelist (deprecated, use passlist)",
				"type": "array"
			}
		},
		"required": [
			"mqtt"
		],
		"type": "object"
	},
	"coordinator": {
		"ieee_address": "0x00212effff09324d",
		"meta": {
			"maintrel": 0,
			"majorrel": 38,
			"minorrel": 114,
			"product": 0,
			"revision": "0x26720700",
			"transportrev": 0
		},
		"type": "ConBee2/RaspBee2"
	},
	"log_level": "info",
	"network": {
		"channel": 11,
		"extended_pan_id": "0x88502386df275aec",
		"pan_id": 58110
	},
	"permit_join": false,
	"restart_required": false,
	"version": "1.33.2",
	"zigbee_herdsman": {
		"version": "0.21.0"
	},
	"zigbee_herdsman_converters": {
		"version": "15.106.0"
	}
}
```