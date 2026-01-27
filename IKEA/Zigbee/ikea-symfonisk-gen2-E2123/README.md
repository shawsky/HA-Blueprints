# IKEA Symfonisk Gen2 [E2123] Media Control v1.55a
# Home Assistant Blueprint

This is a blueprint to support controlling a media player with an Ikea Symfonisk Gen2 remote. It's designed to work with the device added via Zigbee2MQTT (Z2M) only.

<img width="218" height="208" alt="image" src="https://github.com/user-attachments/assets/57ef256c-e59f-4791-a921-a4d801452e26" />

I wanted to allow for the use of more than one of these devices but also avoid the need to find and copy and paste topic strings from the entity MQTT settings. You can just select your device from the list :slight_smile: 

Hope you find it useful.

NOTE: It’s best to select “Legacy = False” in the specific settings for your controllers in the Z2M config if you're still using a version that supports this setting.

# Blueprint

[![Open your Home Assistant instance and show the blueprint import dialog with a specific blueprint pre-filled.](https://github.com/user-attachments/assets/7eb5d903-592f-49cd-8bb4-47ce3d29552b)](https://my.home-assistant.io/redirect/blueprint_import/?blueprint_url=https%3A%2F%2Fgithub.com%2Fshawsky%2FIKEASymfoniskGen2Blueprint%2Fblob%2Fmain%2Fz2m-ikea-symfonisk-gen2-e2123-media-control.yaml)

<!--<a href="http://www.google.com">
<img width="213" height="28" alt="image" src="https://github.com/user-attachments/assets/7eb5d903-592f-49cd-8bb4-47ce3d29552b"  />
</a>
-->

Setup
Select your device, adjust your MQTT base topic if required, choose a media_player to control or a media_player that will act as the main device in a scenario where other players are grouped with it. Finally, configure the “dot” buttons as needed

<img width="988" height="1000" alt="image" src="https://github.com/user-attachments/assets/785ff0c9-ed26-4710-b832-68e9bbd51dd5" />

**Usage**

* :arrow_forward: - Toggle Play / Pause
* :previous_track_button: - Previous Track
* :next_track_button: - Next Track
* :arrow_up_small: - Volume Up. Supports single press and hold
* :arrow_down_small: - Volume Down. Supports single press and hold
* **Single Dot**  - Supports single, double and long press to fire one or more actions
* **Double Dot** - Supports single, double and long press to fire one or more actions

**Credits**
Eric Kreuwels & Alex Austin for the original volume adjust aspects

**Updates**

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
