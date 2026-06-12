## 1.2.26

- Add `dark_icon.png`/`dark_logo.png` (color-inverted) to the integration's `brand/` directory, per the HA Brands Proxy API, so the logo is visible in dark mode.

## 1.2.25

- Fix "Input" sensor reverting to "Streaming" right after switching to "Line-in" from a Raumfeld-zone source (e.g. podcast/radio playback). After `setRoomLineIn`, the renderer briefly disconnects/reconnects and reports a stale URI; the "Line-in" source is now protected for 10 seconds to avoid being overridden during this transition.

## 1.2.24

- Fix "Input" sensor for devices without "Source Select" (e.g. Raumfeld Connector): immediately mark the source as "Line-in" when `setRoomLineIn` is invoked, instead of relying solely on URI inspection. Switching to Line-in causes the renderer to briefly disconnect/reconnect, during which the `AVTransportURI`-based detection could miss the change.

## 1.2.23

- Fix "Input" sensor not switching to "Line-in" when coming from "Streaming" (e.g. Spotify Connect or Raumfeld zone playback) on devices without "Source Select": nowPlaying for grouped/zoned rooms is derived from the zone's virtual renderer, which doesn't reflect a Line-in selection made on the physical renderer. Now also checks the physical renderer's `AVTransportURI` for the Line-in pattern.

## 1.2.22

- Fix "Input" sensor for devices without "Source Select" (e.g. Speaker Bank): correctly detect "Line-in" from the `dlna-playsingle://...iid=0%2FLine%20In%2F...` URI (URL-encoded "Line In" path was not matched before), and keep the last detected source while `AVTransportURI` is briefly empty during transitions instead of falling back to "Streaming". Removes the temporary debug logging from 1.2.21.

## 1.2.21

- Debug build: add temporary logging of `AVTransportURI`/metadata for non-Source-Select rooms to diagnose why the "Input" sensor still shows "Streaming" when Line-in is selected.

## 1.2.20

- Fix the "Input" sensor for devices without "Source Select" (e.g. Speaker Bank): correctly detect Line-in by inspecting the current playback URI/title instead of relying on the "Source Select" cache, so it now shows "Line-in" instead of "Streaming" when Line-in is active.

## 1.2.19

- Add local brand images (`brand/icon.png`, `brand/logo.png`) to the integration, per the [HA Brands Proxy API](https://developers.home-assistant.io/blog/2026/02/24/brands-proxy-api/), so the Raumfeld logo shows up without needing a submission to the brands repository.

## 1.2.18

- Add a separate "Eco mode" button per room, which puts the device into automatic standby (`EnterAutomaticStandby`) without affecting the existing "Off" button (`EnterManualStandby`).
- Add two new sensor entities per room: "Power status" (`Off` / `On` / `ECO mode`) and "Input" (current source: Streaming, Line-in, Optical, TV, Spotify, Radio).
- Track and broadcast the current "Source Select" value for soundbars/sounddecks, with periodic refresh to detect external changes (e.g. TV auto-switching to ARC).

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
