## Bovenste knoppen

```yaml
alias: Bovenste knoppen
description: ""
trigger:
  - platform: device
    domain: mqtt
    device_id: 060d1e38ebb6291a74c1bc5f26e76c95
    type: action
    subtype: press_1_and_3
    discovery_id: 0x000000000175291f action_press_1_and_3
condition: []
action:
  - type: turn_on
    device_id: 700a212daa3ae417daf84a022e1f58e5
    entity_id: 7956ab1038c85a5fd1622de8749be111
    domain: light
    brightness_pct: 100
  - type: turn_on
    device_id: 400d54e8fda3722eea3ca423d5213f5f
    entity_id: bce1d0a3bdafa14748e438392e952c2a
    domain: light
    brightness_pct: 100
  - type: turn_on
    device_id: 8f49f2a198d4fb2d09045763b02e2018
    entity_id: 6e0963071ddfb43770cb8636ddf7cb63
    domain: light
    brightness_pct: 100
  - type: turn_on
    device_id: 75491924f3147102aed1e9b8e7d60232
    entity_id: a5ed82caaba71c6aa6ce17c1aef11681
    domain: light
    brightness_pct: 100
  - type: turn_on
    device_id: ce7e1beb64dc88b7fdefbd059b06f05d
    entity_id: ecf5d20a6127e3c05ff7caf9bd619ef0
    domain: light
    brightness_pct: 100
mode: single
```

## Knop linksboven

```yaml
alias: Knop linksboven
description: ""
trigger:
  - platform: device
    domain: mqtt
    device_id: 060d1e38ebb6291a74c1bc5f26e76c95
    type: action
    subtype: press_1
    discovery_id: 0x000000000175291f action_press_1
condition: []
action:
  - if:
      - condition: numeric_state
        entity_id: light.bank
        attribute: brightness
        above: 254
    then:
      - type: turn_on
        device_id: ce7e1beb64dc88b7fdefbd059b06f05d
        entity_id: ecf5d20a6127e3c05ff7caf9bd619ef0
        domain: light
        brightness_pct: 30
    else:
      - type: turn_on
        device_id: ce7e1beb64dc88b7fdefbd059b06f05d
        entity_id: ecf5d20a6127e3c05ff7caf9bd619ef0
        domain: light
        brightness_pct: 100
mode: single
```

## Knop linksonder

```yaml
alias: Knop linksonder
description: ""
trigger:
  - platform: device
    domain: mqtt
    device_id: 060d1e38ebb6291a74c1bc5f26e76c95
    type: action
    subtype: press_2
    discovery_id: 0x000000000175291f action_press_2
condition: []
action:
  - type: turn_off
    device_id: ce7e1beb64dc88b7fdefbd059b06f05d
    entity_id: ecf5d20a6127e3c05ff7caf9bd619ef0
    domain: light
mode: single
```

## Knop rechtsboven

```yaml
alias: Knop rechtsboven
description: ""
trigger:
  - platform: device
    domain: mqtt
    device_id: 060d1e38ebb6291a74c1bc5f26e76c95
    type: action
    subtype: press_3
    discovery_id: 0x000000000175291f action_press_3
condition: []
action:
  - if:
      - condition: numeric_state
        entity_id: light.speelhoek
        attribute: brightness
        above: 254
    then:
      - type: turn_on
        device_id: 75491924f3147102aed1e9b8e7d60232
        entity_id: a5ed82caaba71c6aa6ce17c1aef11681
        domain: light
        brightness_pct: 30
    else:
      - type: turn_on
        device_id: 75491924f3147102aed1e9b8e7d60232
        entity_id: a5ed82caaba71c6aa6ce17c1aef11681
        domain: light
        brightness_pct: 100
mode: single
```

## Knop rechtsonder

```yaml
alias: Knop rechtsonder
description: ""
trigger:
  - platform: device
    domain: mqtt
    device_id: 060d1e38ebb6291a74c1bc5f26e76c95
    type: action
    subtype: press_4
    discovery_id: 0x000000000175291f action_press_4
condition: []
action:
  - type: turn_off
    device_id: 75491924f3147102aed1e9b8e7d60232
    entity_id: a5ed82caaba71c6aa6ce17c1aef11681
    domain: light
mode: single
```

## Onderste knoppen

```yaml
alias: Onderste knoppen
description: ""
trigger:
  - platform: device
    domain: mqtt
    device_id: 060d1e38ebb6291a74c1bc5f26e76c95
    type: action
    subtype: press_2_and_4
    discovery_id: 0x000000000175291f action_press_2_and_4
condition: []
action:
  - if:
      - condition: device
        type: is_off
        device_id: 700a212daa3ae417daf84a022e1f58e5
        entity_id: 7956ab1038c85a5fd1622de8749be111
        domain: light
      - condition: device
        type: is_off
        device_id: 400d54e8fda3722eea3ca423d5213f5f
        entity_id: bce1d0a3bdafa14748e438392e952c2a
        domain: light
      - condition: device
        type: is_off
        device_id: 8f49f2a198d4fb2d09045763b02e2018
        entity_id: 6e0963071ddfb43770cb8636ddf7cb63
        domain: light
      - condition: device
        type: is_off
        device_id: 75491924f3147102aed1e9b8e7d60232
        entity_id: a5ed82caaba71c6aa6ce17c1aef11681
        domain: light
      - condition: device
        type: is_off
        device_id: ce7e1beb64dc88b7fdefbd059b06f05d
        entity_id: ecf5d20a6127e3c05ff7caf9bd619ef0
        domain: light
    then:
      - type: turn_off
        device_id: 80b0980ac34e3153a7e68c47be8d15bd
        entity_id: dff15576f4cfe4b3c08d114422c40ef3
        domain: light
      - type: turn_off
        device_id: 0f0507359702528baeeffcd347f001c1
        entity_id: 43e6563babaeecba85217a0a1ea37dc2
        domain: light
      - type: turn_off
        device_id: 981800cfd18a6ad4ae1f692999b4384d
        entity_id: 1bade8b47ba6f2d48f5d1c0b77c4029d
        domain: light
  - type: turn_off
    device_id: ce7e1beb64dc88b7fdefbd059b06f05d
    entity_id: ecf5d20a6127e3c05ff7caf9bd619ef0
    domain: light
  - type: turn_off
    device_id: 75491924f3147102aed1e9b8e7d60232
    entity_id: a5ed82caaba71c6aa6ce17c1aef11681
    domain: light
  - type: turn_off
    device_id: 700a212daa3ae417daf84a022e1f58e5
    entity_id: 7956ab1038c85a5fd1622de8749be111
    domain: light
  - type: turn_off
    device_id: 400d54e8fda3722eea3ca423d5213f5f
    entity_id: bce1d0a3bdafa14748e438392e952c2a
    domain: light
  - type: turn_off
    device_id: 8f49f2a198d4fb2d09045763b02e2018
    entity_id: 6e0963071ddfb43770cb8636ddf7cb63
    domain: light
mode: single
```
