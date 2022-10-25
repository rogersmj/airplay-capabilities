# Airplay Capabilities
It can be confusing to know what functions are supported by AirPlay devices, because they can vary by device type and use case. This document attempts to enumerate what capabilities should be expected in different situations, depending on device type and scenario.

This was created after personally experiencing and witnessing a lot of confusion (mainly in the Home Assistant forums) regarding what "should work" with AirPlay in certain contexts.

## AirPlay Capability Matrix
See below for definitions and notes.

● = Fully supported  |  ⨀ = Partially/conditionally supported (see notes)  |  ✘ = Not supported

<table>
<thead>
  <tr>
    <th></th>
    <th colspan="4">Playback control from source device<br></th>
    <th colspan="4">Volume control from source device</th>
    <th colspan="4">Playback control/metadata on secondary device<br></th>
    <th colspan="4">Volume control on secondary device</th>
  </tr>
</thead>
<tbody>
  <tr>
    <td>Playback device →<br>↓ Source device</td>
    <td>Airport Express</td>
    <td>Apple TV</td>
    <td>HomePod</td>
    <td>Third Party</td>
    <td>Airport Express</td>
    <td>Apple TV</td>
    <td>HomePod</td>
    <td>Third Party</td>
    <td>Airport Express</td>
    <td>Apple TV</td>
    <td>HomePod</td>
    <td>Third Party</td>
    <td>Airport Express</td>
    <td>Apple TV</td>
    <td>HomePod</td>
    <td>Third Party</td>
  </tr>
  <tr>
    <td>iOS (iPhone, iPad)</td>
    <td>●</td>
    <td>●</td>
    <td>●</td>
    <td>●</td>
    <td>●</td>
    <td>⨀1</td>
    <td>●</td>
    <td>●</td>
    <td>✘</td>
    <td>●</td>
    <td>⨀3</td>
    <td>⨀3</td>
    <td>✘<br></td>
    <td>✘</td>
    <td>✘</td>
    <td>⨀3</td>
  </tr>
  <tr>
    <td>Apple TV</td>
    <td>●</td>
    <td>●</td>
    <td>●</td>
    <td>●</td>
    <td>●</td>
    <td>⨀2</td>
    <td>●</td>
    <td>●</td>
    <td>✘</td>
    <td>●</td>
    <td>●</td>
    <td>●</td>
    <td>✘</td>
    <td>⨀</td>
    <td>●</td>
    <td>●</td>
  </tr>
  <tr>
    <td>HomePod</td>
    <td>●</td>
    <td>●</td>
    <td>●</td>
    <td>●</td>
    <td>●</td>
    <td>✘</td>
    <td>●</td>
    <td>●</td>
    <td>✘</td>
    <td>●</td>
    <td>?4</td>
    <td>●</td>
    <td>✘</td>
    <td>✘</td>
    <td>?4</td>
    <td>●</td>
  </tr>
</tbody>
</table>

### Notes
1. Can only change volume if the Apple TV is able to send volume commands through CEC to connected TV/sound system.
2. Volume can be adjusted up the level that the connected TV/sound system is already set to. In other words, the source Apple TV can be used to adjust the volume of the playback Apple TV, but 100% volume level is the level that connected TV/sound system was set to prior to the initiation of the AirPlay stream. It's a "virtual" volume control, and not actually controlling the volume of the playback system.
3. Inconsistent -- sometimes works, sometimes doesn't
4. I only have one HomePod at the moment, so I can't test this.

### Caveats
* This information is current as of iOS 16.0/tvOS 16.0/HomePod OS 16.0.
* "Third party" in this table refers to [Shairport-Sync](https://github.com/mikebrady/shairport-sync) with Airplay 2 support running on a Raspberry Pi

### Definitions
#### Source Device
The device that initiated the music playback. For example, if you used the Music app on your iPhone to start the music and selected AirPlay endpoints from there, your iPhone is the Source Device.

#### Playback Device
A device that is receiving and playing back the AirPlay stream.

#### Secondary Device (e.g. secondary playback control)
"Seconday" refers to another device on the same network that was not involved in the original AirPlay "transaction." For instance, if you started playing music from your phone, your wife's phone would be a "Secondary Device."

# Background
What is commonly referred to as "AirPlay" is actually a combination of (at least) a couple protocols. AirPlay itself, for example, cannot provide metadata on the media being played. Metadata from Apple TVs and HomePods are visible to secondary devices because it is retrieved via another protocol: Media Remote Protocol (MRP). MRP is tunneled over AirPlay 2 since tvOS 15, but not supported by non-Apple devices nor the AirPort Express.

# Links and Acknowledgements
Most of the actual functionality in the table is derived from my own experience, but the technical details of what's going on have been gleaned from other sources.

* User [postlund](https://community.home-assistant.io/u/postlund) in the Home Assistant Community forums
* Mike Brady's excellent [Shairport-Sync](https://github.com/mikebrady/shairport-sync)