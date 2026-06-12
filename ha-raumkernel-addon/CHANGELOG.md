## 1.2.18

- Change "Turn off" to put devices into eco/automatic standby (`EnterAutomaticStandby`) instead of full manual standby (`EnterManualStandby`), so devices remain reachable and wake faster.

## 1.2.17

- Use friendly source names in the UI for soundbar/sounddeck source selection: "Streaming", "Line-in", "Optical", "TV" (instead of the raw `Raumfeld`, `LineIn`, `OpticalIn`, `TV_ARC` values).

## 1.2.16

- Fix `selectSource` for Soundbars/Sounddecks: include `InstanceID` in `GetDeviceSetting`/`SetDeviceSetting` calls and target the physical room renderer instead of the virtual zone renderer.
- Add Line-in switching for devices that don't support `Source Select` but have a physical Line-in input (e.g. Stereo M/L/R speakers).

## 1.2.14

- Add `selectSource` support for Soundbars and Sounddecks (TV_ARC, OpticalIn).
- Update Integration to expose Source Select feature.

## 1.2.13

- Fix track images which are hosted on Raumfeld devices (e.g. Local music, Tidal) not showing up.
- Add information/debug page to the addon (reachable at the default port).

## 1.2.12

- Added a setting to manually set the Raumfeld host address if auto discovery fails.

## 1.2.11

- Add support for media_content_id. It is now possible to see which media is currently playing.

## 1.2.10

- Fixes a crash if homeassistant sends a "prev" command even if prev is not allowed
- Fix issues with seek.

## 1.2.9

- Automatic install of integration

## 1.2.7

- Add Seek
- Improved Zone Handling
- Reboot Devices

## 1.2.2

- Add reboot feature to restart Raumfeld devices via SSH

## 1.0.0

- Initial release
