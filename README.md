# Tarkov Internal

Download: soon

Internal build for Escape from Tarkov — code runs inside the client instead of an overlay.

Includes player ESP with skeleton, loot ESP filtered by value, aimbot with bone pick and a radar. Internal means lower latency and no window on top.

Requirements: Windows 10/11, Battlestate launcher, admin for the injector.

Steps: download, unpack, injector as admin, start the game, menu on INSERT. BattlEye updates can break offsets, wait for the next build.


## Troubleshooting

## Troubleshooting

**Overlay does not show.** Switch the game to borderless or windowed fullscreen, exclusive fullscreen hides every overlay.

**Menu does not open.** Run the loader as administrator, INSERT is ignored without elevation.

**Nothing attaches.** Start the loader before the game. If the process is already running, restart it.

**Wrong values after a patch.** Wait for the next build, offsets are version specific.

**Overlay flickers in OBS.** Enable streamproof and capture the game with game capture, not display capture.

## Notes

## Notes

- keep the loader and config.json in the same folder
- profiles are plain text, edit them while the game is closed
- close other overlays (Discord, GeForce, RTSS) before attaching
- the first launch after a patch can take a few seconds longer while offsets load

## Compatibility

## Compatibility

- Windows 10 21H2 and newer, Windows 11 all builds
- borderless, windowed fullscreen, and windowed work
- 16:9 and 21:9 supported, other ratios render correct after a restart
- DPI scaling above 125% is handled by the loader

## FAQ

## FAQ

**Is it external or internal?** Read the first line of this page, the mode is written there.

**Does it need a key?** No.

**Can I move the config to another PC?** Yes, copy config.json next to the loader.

**Will a patch break it today?** Possibly, offsets are refreshed with each release.

**Is the overlay visible in clips?** Only if streamproof is off.

## Architecture

## Architecture

The loader stays outside the game process and reads state through a handle, then paints an overlay window on top. Because nothing is injected, a game crash never takes the tool with it and the anti-cheat sees a normal desktop overlay.

The reader refreshes offsets on start, so a build works across restarts without a relaunch of Windows.