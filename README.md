# POP - Power Of Pausing 🌿

POP is a lightweight, open-source desktop application that interrupts your screen on a fixed schedule and gives you a concrete reason to stop looking at it - drink water, stretch, walk around, or rest your eyes - before automatically handing control back to whatever you were doing.

It is not a browser extension and it is not a website. It is a native desktop app (built with Electron) that lives in your system tray on Windows or your menu bar on macOS, runs entirely on your own machine, and stores nothing anywhere except a small local settings file on your own disk.

This document explains what POP is, how it behaves, where to find detailed setup instructions, and answers to the questions people most commonly run into. For step-by-step installation, see **[SETUP.md](./SETUP.md)** - this file is about understanding the app, not installing it.

---

## Table of contents

- [What POP does](#what-pop-does)
- [Where to go to set it up](#where-to-go-to-set-it-up)
- [What you can configure](#what-you-can-configure)
- [Privacy and data](#privacy-and-data)
- [FAQ](#faq)
- [License](#license)

---

## What POP does

Most break reminder tools rely on a notification banner that's easy to glance at and dismiss without actually doing anything. POP is built around a different assumption: a reminder you can ignore in half a second isn't really a reminder, it's noise. So instead, POP briefly takes over your screen.

On a timer you control (30 minutes by default), POP gives you a 30-second heads-up, then dims your entire screen to black and shows a short card with one randomly chosen activity and a countdown. After the countdown ends - or if you choose to skip - your screen returns exactly to where you left off, and the cycle starts again.

The four activities POP rotates between:

- 💧 **Drink water** - a prompt to hydrate
- 🧘 **Stretch** - loosen your shoulders and neck
- 🚶 **Walk** - step away for a couple of minutes
- 👁️ **Rest your eyes** - look at something 20 feet away for 20 seconds

One is chosen at random each time a break fires, so breaks don't become a predictable, ignorable pattern.

---

## Where to go to set it up

This file (`README.md`) is documentation about the project. The actual installation steps - for Windows, for macOS, and for running from source on any platform - live in **[SETUP.md](./SETUP.md)**.

A quick map of what you'll find there, depending on what you're trying to do:

| You want to... | Go to this section in SETUP.md |
|---|---|
| Install POP on Windows, no terminal needed | **Windows - Installer Setup** |
| Build and install POP on macOS | **macOS - Installer Setup** |
| Fix an error you hit during any of the above | The **"What can go wrong"** subsection under that same step |

---

## What you can configure

Right-click (Windows) or click (macOS) the POP icon in your tray/menu bar, then choose **Settings**:

| Setting | Range | Default |
|---|---|---|
| Work interval | 5–120 minutes | 30 minutes |
| Break duration | 1–30 minutes | 5 minutes |
| Enabled | on/off | on |
| Start on login | on/off | off |

Settings are saved immediately and persist across restarts. There is no "save and restart the app" step required.

---

## Privacy and data

POP makes no network requests of any kind. There is no analytics, no telemetry, no crash reporting service, no update-checking ping - nothing leaves your machine, ever.

Uninstalling POP removes the application; the config.json file is small enough that most uninstallers leave it behind by default (standard behavior for almost all apps) - you can delete that folder manually if you want a completely clean removal.

---

## FAQ

**Is POP free?**
Yes, entirely. No paid tier, no trial period, no feature gating.

**Does POP collect any data?**
No. See [Privacy and data](#privacy-and-data) above - nothing leaves your machine.

**Why does the break screen go fully black instead of just showing a notification?**
A notification is too easy to dismiss without actually taking the break - so the break itself is a full-screen interruption, which reliably gets the intended five minutes back even when you're deep in focus and would otherwise swipe a notification away on reflex. The 30-second heads-up *before* the break is a regular OS notification, since at that stage it's just a courtesy warning, not the break enforcement itself.

**I saw the 30-second warning notification but the break still happened. Is that a bug?**
No - that's intended behavior. The warning is purely informational, with nothing to click and no way to cancel the upcoming break from it. If you want to skip a break, wait for the black screen to appear and click "Skip this break" there instead.

**Does POP work on Linux?**
For now, POP is only for Windows and macOS. Issues and PRs are welcome if you want to build the Linux version with me!

**Will POP slow down my computer or drain my battery?**
No. Between breaks, POP is just a tray/menu bar icon and a single idle timer - there's no polling, no background processing, no GPU usage. The black break screen itself is a simple static window with one CSS animation; it has no meaningful performance cost either.

**I'm on Windows and saw a "Windows protected your PC" warning. Is the installer safe?**
Yes - this is Windows SmartScreen flagging the installer simply because it isn't signed with a paid code-signing certificate, not because anything is actually wrong with it. Full explanation and the bypass steps are in [SETUP.md](./SETUP.md).

**I'm on macOS and the app won't open / says it's from an "unidentified developer."**
See the Gatekeeper section in [SETUP.md](./SETUP.md) - there's a quick fix, and if you built the app yourself from a `git clone` (rather than downloading a pre-built `.dmg`), you likely won't hit this at all.

**How do I uninstall POP?**
Windows: **Settings → Apps → Installed apps**, find POP, uninstall - same as any other Windows program.
macOS: drag `POP.app` out of your **Applications** folder to the Trash.

**Can I contribute or report a bug?**
Yes - this is open source. Open an issue or pull request on the repository.

---

## License

MIT - see [LICENSE](./LICENSE). 
