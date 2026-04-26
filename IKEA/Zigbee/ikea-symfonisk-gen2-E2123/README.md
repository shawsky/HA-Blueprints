# IKEA Symfonisk Gen2 [E2123] Media Control v2.00
# Home Assistant Blueprint

This is a blueprint to support controlling a media player with an Ikea Symfonisk Gen2 remote. It's designed to work with the device added via Zigbee2MQTT (Z2M) only.

<img width="218" height="208" alt="image" src="https://github.com/user-attachments/assets/634b6220-8632-4682-ba24-5680739ee8e7" />

I wanted to allow for the use of more than one of these devices but also avoid the need to find and copy and paste topic strings from the entity MQTT settings. You can just select your device from the list :slight_smile: 

Hope you find it useful.

NOTE: It’s best to select “Legacy = False” in the specific settings for your controllers in the Z2M config if you're still using a version that supports this setting.

# Blueprint

[![Open your Home Assistant instance and show the blueprint import dialog with a specific blueprint pre-filled.](https://github.com/user-attachments/assets/ea8fffc7-f88b-4f84-b549-05403cc50cba)](https://my.home-assistant.io/redirect/blueprint_import/?blueprint_url=https%3A%2F%2Fgithub.com%2Fshawsky%2FHA-Blueprints%2Fblob%2Fmain%2FIKEA%2FZigbee%2Fikea-symfonisk-gen2-E2123%2Fikea-symfonisk-gen2-media-control.yaml)

**Manual Import URL**

If the button above doesn't work, you can copy the URL below and paste it into the "Import Blueprint" dialog in Home Assistant:
`https://github.com/shawsky/HA-Blueprints/blob/main/IKEA/Zigbee/ikea-symfonisk-gen2-E2123/ikea-symfonisk-gen2-media-control.yaml`


## Setup

### Basic Configuration
Select your Symfonisk Gen2 device, adjust your MQTT base topic if required, and choose a media_player to control (or a media_player that will act as the main device in a scenario where other players are grouped with it).

### Dynamic Volume Control (Group vs. Room)
You can choose to disable group volume control by using the Allow Group Volume Control option, it is enabled by default. If you want to use the option to dynamically switch between controlling the group volume and just the room volume, you must select an Input Helper (Boolean) to store the state.

By default volume control will revert to group when Play/Pause is pressed, if you want to prevent this behaviour, turn off the Reset to Group Volume Control when Play/Pause pressed setting.

Use the drop down to select which button on the Symfonisk to use to switch between Group and Room volume control. Note: If you've previously set an action on the button you select to switch between Group and Room volume control, it will no longer fire.

The Volume Control Toggle option can be used to fire an action when switching between Group and Room volume control. This is useful if you have dashboards, indicators or other physical items you use to indicate state from your Home Assistant setup.

### Volume Ducking
You can enable and configure volume ducking, which briefly lowers the volume to provide audio feedback when you successfully toggle between group and room volume control. The slider allows you to choose how long the volume is ducked for.

### Custom Actions & Buttons
Configure the custom actions such as what happens when Play/Pause is pressed but no media is playing or queued and set up the actions for your "dot" buttons as needed.

***Note***
If you're not sure how to create an Input Helper: In Home Assistant, navigate to Settings > Devices & Services > Helpers. Click the + Create Helper button in the bottom right, select Toggle, give it a recognisable name (e.g., "Living Room Volume Mode"), and click Create. Finally, select this new helper in the blueprint config.

<img width="2612" height="1835" alt="image" src="https://github.com/user-attachments/assets/78fdd2bc-068e-49b1-a0f8-1434a914a88c" />
<img width="2580" height="1335" alt="image" src="https://github.com/user-attachments/assets/cc8bac40-2f28-4368-ba1d-7fd2775b2fb7" />


**Usage**

* :arrow_forward: - Toggle Play / Pause
* :previous_track_button: - Previous Track
* :next_track_button: - Next Track
* :arrow_up_small: - Volume Up. Supports single press and hold
* :arrow_down_small: - Volume Down. Supports single press and hold
* **Single Dot**  - Supports single, double and long press to fire one or more actions
* **Double Dot** - Supports single, double and long press to fire one or more actions

**Updates**

2025-12-30 v2.00: Add group/room volume control and switching with volume ducking, action running when switching from group/room volume control. Action on Play/Pause when no media playing/queued.

2024-04-16 v1.55: Add additional filtering to remove the false positives of the automations triggering for MQTT topics or where you run multiple Ikea E2123 devices. This should help clean up log book entries etc. Thanks kenno.

2024-04-10 v1.54: Update device selector to account for the Ikea refactoring which will change the model name slightly. Both versions supported. Add support for the legacy action on the play/pause button.

2023-09-06 v1.52/v1.53: Update to allow 100 volume steps. / Fix copy paste fail on volume down hold for non grouped players.

2023-09-06 v1.51: Fix to stop non grouped players with empty group_members attribute triggering the grouped volume actions.

2023-09-05 v1.5: Resolve an issue with non grouped players presenting empty arrays rather than "none" in the group members attribute. Also apply these and previous fixes to volume hold.

2023-08-15 v1.4: Resolve an issue with volume not working on media player integrations that do not populate the group members attribute for single devices/group in a different way to the Sonos integration

2023-06-26 v1.3: Resolve an issue where multiple devices are attached to a system and all automations are triggered by any device.

2023-05-08 v1.2: Added support for volume control of all Sonos players joined to/grouped with the media player specified in the automation. The volume is adjusted on a per player basis so any differential set in the Sonos app is maintained. Note: To continue control the main media player specified in the automation must always remain in the Sonos group.

2023-04-16 v1.1: Tweak descriptive text for volume steps and set the default to match the scale of the Sonos app.

2023-05-08 v1.2: Added support for volume control of all Sonos players joined to/grouped with the media player specified in the automation. The volume is adjusted on a per player basis so any differential set in the Sonos app is maintained. Note: To continue control the main media player specified in the automation must always remain in the Sonos group.

2023-04-16 v1.1: Tweak descriptive text for volume steps and set the default to match the scale of the Sonos app.
