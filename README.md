# SupaMap

A small settings app for the wired **SCUF Envision V2**, as an alternative to Corsair iCUE. No drivers, no admin rights, no account.

It edits the three profiles stored on the controller itself, so your changes work everywhere, even with the app closed. It can also pass [other gamepads](#other-controllers) on to games as an Xbox controller, with your own layout, deadzones and bindings, including their back paddles.

## Download

**[Download the latest version](https://github.com/ChristianAnselm/SuperMap-download/releases/latest)**: under **Assets**, get `SupaMap-<date>.zip`. The two "Source code" files GitHub adds only contain this page.

It runs on Windows 10 and 11, using the .NET Framework 4.8 that comes with Windows, so there's nothing else to install. The onboard-profile features need the wired SCUF Envision V2 (USB ID `1B1C:3A04`).

## Getting started

1. Extract the zip into a folder of its own, such as `Documents\SupaMap`. The app keeps its settings and backups next to itself, so don't run it from inside the zip.
2. Quit iCUE if it's running. Both programs talk to the controller, and iCUE may switch it over to its own settings.
3. Run `SupaMap.exe`. The app isn't code-signed, so Windows may say "Windows protected your PC". Click **More info**, then **Run anyway**.
4. Plug in the controller. Make your changes, then click **Save to controller**. Gamepad, deadzone and rumble changes apply at once and stay after unplugging.

**Coming from Envision Lite?** That was this app's old name. Extract the new zip into the same folder to keep your settings, bindings and backups, then delete the old `EnvisionLite.exe`. If you had **Start with Windows** on, it moves over to SupaMap the first time you run it.

Before every save, the app backs up the controller's settings to the `backups` folder. **Settings → Restore a backup…** puts any of them back.

## What it never does

- Replace drivers or install services. The only driver it can use is ViGEmBus, for the optional [Xbox controller mode](#xbox-controller-mode), and you install that yourself.
- Ask for admin rights.
- Connect to the internet, except to check for updates when you ask (**Settings → Updates**). Nothing is downloaded or installed for you.
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
| Settings | The profile's name, saving it to a file or loading one, Xbox controller mode, tray behaviour, Start with Windows (off by default), backups, update check |

The profile pills at the top choose which profile you're editing. A dot marks the one active on the controller, and **Make active** switches to it.

**Settings → Profile** can rename a profile (up to 26 characters, stored on the controller). It can also save a profile to a file, or load one into the slot. A file holds the paddle and SAX buttons, deadzones, rumble and bindings, so you can keep more than three. Click **Save to controller** afterwards to keep the change.

### On the controller or on the PC

- **Gamepad** targets for paddles and SAX buttons are stored on the controller. They work everywhere, even with the app deleted.
- **Everything else** (keys, mouse buttons, macros and every G-key binding) is done by the app, because the controller's firmware only knows gamepad buttons. These work only while the app runs, so closing the window then keeps it in the tray.
- **Repeat while held:** any key, mouse button or gamepad binding can repeat instead of being held. It presses once, then after a delay you choose repeats at a set rate until you let go. A paddle's gamepad button moves from the controller to the PC when it repeats, so it needs Xbox controller mode.

### Pad macros

A pad macro records everything the controller does for a moment (buttons, D-pad, analog triggers and both sticks) and plays it back with its original timing. Click **Record**, do the move on the controller, then click **Stop recording**. The list shows each step, including which way a stick moved and how far ("Move left stick up-left (100%)"), and you can add waits or delete steps.

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
- **Paddles:** up to four back paddles, which can be bound like any button: to an Xbox button, a key, a mouse button or a macro. The DualSense Edge's back buttons work without setup. For other pads, run **Set up buttons** and press the paddles when it asks at the end. That works when the pad reports its paddles to Windows as controls of their own. Some pads only map them to other buttons inside the controller, and then there's nothing separate to bind.

What it can't do:

- **Hide the real pad from games.** That needs another driver, which this app leaves out. A game that already supports the pad may see two controllers, so use Xbox controller mode for games that don't recognise it at all.
- **Rumble, gyro, touchpad and light bar** on these pads.
- **Remap pads that already are Xbox controllers** (Xbox pads, most third-party pads, a Victrix Pro BFG in PC mode). Hiding them from games would need a driver. Their **Buttons** page (under **Xbox controllers**) can still make any button also press a key or mouse button or play a key macro, with repeat; the game sees the original button too. If the pad has a mode switch, its PS4 or DirectInput mode lets SupaMap set it up fully, paddles included.
- **Bind an Xbox Elite controller's paddles.** Windows only reports them to the program in front, which during play is the game. The same goes for Xbox-style pads that map their paddles inside the controller. Map them in the controller's own app (Xbox Accessories for the Elite) instead.

## Not tried yet

- Real controllers other than the SCUF, including the DualShock 4, DualSense and DualSense Edge layouts, and paddles on any of them. These were tested on simulated input only.
- Whether G2–G4 really stop changing the volume when pressed on the controller.

Found a problem? Click **Copy controller details** (on the controller's Test page, or on the Xbox controllers page) and paste the result into an issue: [Open an issue](https://github.com/ChristianAnselm/SuperMap-download/issues).

## Uninstall

If you turned on **Start with Windows**, turn it off first. Then delete the folder. If you installed ViGEmBus, remove it from Windows' **Installed apps**.

## License

Free to download and use for personal, non-commercial purposes. Please don't sell it or share copies: share a link to this page instead. The full terms are in [LICENSE.txt](LICENSE.txt).

The protocol details were learned by reading [OpenLinkHub](https://github.com/jurkovic-nikola/OpenLinkHub) and [ZeroCue](https://github.com/N7Steve/ZeroCue); no code from either is included. Xbox controller mode uses [ViGEmBus](https://github.com/nefarius/ViGEmBus) by Nefarius, which is installed separately.

Not affiliated with, endorsed by or sponsored by Corsair or SCUF Gaming. SCUF, Envision and Corsair are trademarks of their respective owners.
