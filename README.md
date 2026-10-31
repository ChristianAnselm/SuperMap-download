# SuperMap Lite

A small settings app for the wired **SCUF Envision V2**, as an alternative to Corsair iCUE. No drivers, no admin rights, no account.

It edits the three profiles stored on the controller itself, so your changes work everywhere, even with the app closed. It can also pass [other gamepads](#other-controllers) on to games as an Xbox controller, with your own layout, deadzones and bindings.

## Download

**[Download the latest version](https://github.com/ChristianAnselm/SuperMap-download/releases/latest)**: under **Assets**, get `EnvisionLite-<date>.zip`. The two "Source code" files GitHub adds only contain this page.

It runs on Windows 10 and 11, using the .NET Framework 4.8 that comes with Windows, so there's nothing else to install. The onboard-profile features need the wired SCUF Envision V2 (USB ID `1B1C:3A04`).

## Getting started

1. Extract the zip into a folder of its own, such as `Documents\Envision Lite`. The app keeps its settings and backups next to itself, so don't run it from inside the zip.
2. Quit iCUE if it's running. Both programs talk to the controller, and iCUE may switch it over to its own settings.
3. Run `EnvisionLite.exe`. The app isn't code-signed, so Windows may say "Windows protected your PC". Click **More info**, then **Run anyway**.
4. Plug in the controller. Make your changes, then click **Save to controller**. Gamepad, deadzone and rumble changes apply at once and stay after unplugging.

Before every save, the app backs up the controller's settings to the `backups` folder. **Settings → Restore a backup…** puts any of them back.

## What it never does

- Replace drivers or install services. The only driver it can use is ViGEmBus, for the optional [Xbox controller mode](#xbox-controller-mode), and you install that yourself.
- Ask for admin rights.
- Connect to the internet.
- Run in the background, unless you give a button a PC-side binding or turn on Xbox controller mode.
- Hook the keyboard, except while G2, G3 or G4 has a binding (see [G keys](#g-keys)).

## Features

| Page | What you can change |
|---|---|
| Buttons | Click a paddle, SAX button or G key on the diagram (or just press it) and choose:<br>**Gamepad:** A, B, X, Y, LB, RB, LT, RT, LS, RS or a D-pad direction (G keys also View and Menu)<br>**Keyboard:** a key or combo<br>**Mouse:** a mouse button<br>**Key macro:** a recorded key sequence<br>**Pad macro:** a recorded sequence of gamepad input<br>**Off** |
| Sticks | Inner and outer deadzone for each stick, with a live preview |
| Triggers | Start and end deadzone for each trigger, with a live preview |
| Rumble | Strength of each motor (0–100%) |
| Test | Live view of sticks, triggers, buttons, D-pad, profile button and the paddles |
| Settings | Xbox controller mode, tray behaviour, Start with Windows (off by default), backups |

The profile pills at the top choose which profile you're editing. A dot marks the one active on the controller, and **Make active** switches to it.

### On the controller or on the PC

- **Gamepad** targets for paddles and SAX buttons are stored on the controller. They work everywhere, even with the app deleted.
- **Everything else** (keys, mouse buttons, macros and every G-key binding) is done by the app, because the controller's firmware only knows gamepad buttons. These work only while the app runs, so closing the window then keeps it in the tray.

### Pad macros

A pad macro records everything the controller does for a moment (buttons, D-pad, analog triggers and both sticks) and plays it back with its original timing. Click **Record**, do the move on the controller, then click **Stop recording**. You can then add waits or delete steps.

Playback goes through the virtual Xbox controller, so pad macros need [Xbox controller mode](#xbox-controller-mode). Online games may treat input macros as cheating: check a game's rules before using them in multiplayer.

### G keys

The five G keys along the bottom edge can be bound like the paddles. On the controller itself, G2, G3 and G4 are Volume down, Volume up and Mute. While one of them has a binding, the app stops it changing the volume. Choose **Off** to silence one without binding anything.

### Xbox controller mode

Some games, such as Call of Duty, only accept Xbox controllers and report "no controller" for the Envision V2. To fix that:

1. Install [ViGEmBus 1.22.0](https://github.com/nefarius/ViGEmBus/releases/tag/v1.22.0), the open-source virtual gamepad driver. Installing it needs admin rights once.
2. Turn on **Settings → Show up as an Xbox controller**.

The app then adds a virtual Xbox 360 controller that copies everything the SCUF does, and passes the game's rumble back to the SCUF. The virtual controller only exists while the app runs. Games that read both kinds of controller may see two: turn the mode off for those, or pick the Xbox one in the game.

## Other controllers

Any other gamepad Windows recognises, over USB or Bluetooth, appears in the **Controllers** list. The app can't change settings stored inside these pads, but it can give each one:

- **A layout:** which button is A, which axis is the left stick, and so on. **Set up buttons** asks you to press each control in turn and takes about a minute. The DualShock 4 and DualSense have a built-in layout.
- **Its own virtual Xbox controller** (Settings, per pad), for games that don't recognise the pad.
- **Stick and trigger deadzones**, and the same bindings as the G keys.

What it can't do:

- **Hide the real pad from games.** That needs another driver, which this app leaves out. A game that already supports the pad may see two controllers, so use Xbox controller mode for games that don't recognise it at all.
- **Rumble, gyro, touchpad and light bar** on these pads.
- **Change pads that already are Xbox controllers.** They appear only as a live view.

## Not tried yet

- Real controllers other than the SCUF, including the DualShock 4 and DualSense layouts. These were tested on simulated input only.
- Whether G2–G4 really stop changing the volume when pressed on the controller.

Found a problem? [Open an issue](https://github.com/ChristianAnselm/SuperMap-download/issues).

## Uninstall

If you turned on **Start with Windows**, turn it off first. Then delete the folder. If you installed ViGEmBus, remove it from Windows' **Installed apps**.

## License

Free to download and use for personal, non-commercial purposes. Please don't sell it or share copies: share a link to this page instead. The full terms are in [LICENSE.txt](LICENSE.txt).

The protocol details were learned by reading [OpenLinkHub](https://github.com/jurkovic-nikola/OpenLinkHub) and [ZeroCue](https://github.com/N7Steve/ZeroCue); no code from either is included. Xbox controller mode uses [ViGEmBus](https://github.com/nefarius/ViGEmBus) by Nefarius, which is installed separately.

Not affiliated with, endorsed by or sponsored by Corsair or SCUF Gaming. SCUF, Envision and Corsair are trademarks of their respective owners.
