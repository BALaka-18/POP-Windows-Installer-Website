# SETUP

Step-by-step installation instructions for POP. Pick the section for your platform and follow it in order - each step lists exactly what to expect, and what to do if something goes wrong before moving to the next step.

For general information about what POP is and how it behaves, see [README.md](./README.md). This file is setup only.

---

## Table of contents

- [Windows - Installer Setup](#windows---installer-setup)
- [macOS - Installer Setup](#macos---installer-setup)
- [Uninstalling](#uninstalling)

---

## Windows - Installer Setup

This is the easiest path on Windows - no terminal, no Node.js, no build step. You're installing a pre-built application.

### Step 1 - Download the installer

Go to the official website for the Windows version - [POP: Power Of Pausing](https://bit.ly/4eNCaCX)

**What can go wrong:**
- **Your browser flags the download as potentially unsafe.** Some browsers warn on any `.exe` download by default, regardless of the file. This is a generic browser warning, not specific to POP - click "Keep" or "Keep anyway" to proceed.

### Step 2 - Run the installer

Double-click `Break.Reminder.Setup.1.0.0.exe`.

**What can go wrong:**
- **"Windows protected your PC" (SmartScreen warning) appears, with the app shown as from an "Unknown publisher."** This happens because the installer isn't signed with a paid Windows code-signing certificate (I'm a broke developer in grad school on loan, be kind) - it does not mean anything is wrong with the file. To proceed:
  1. Click **More info** (small text link, easy to miss)
  2. A **Run anyway** button appears - click it
  3. Setup continues normally from here
- **Nothing happens when you double-click.** Check your Downloads folder - some browsers append a `(1)` or similar to repeated downloads, or the file may have downloaded with a `.exe.download` temporary extension that needs to finish first. Wait for the download to fully complete, then try again.

### Step 3 - Complete the install wizard

Follow the prompts: choose an install location (or accept the default), confirm. Unlike a single-click installer, POP's installer lets you choose **Start Menu shortcut** and **Desktop shortcut** options along the way - both are recommended.

**What can go wrong:**
- **"Access denied" or a permissions error during install.** Right-click `Break.Reminder.Setup.1.0.0.exe` and choose **Run as administrator**, then try again. This is occasionally needed depending on your Windows account's permission level and where you're installing to.

### Step 4 - Launch POP

Open POP from the Start Menu or Desktop shortcut. A small green icon should appear in your system tray (bottom-right of your screen, near the clock).

**What can go wrong:**
- **You don't see the tray icon.** Click the small **^** (up arrow) near the clock to expand hidden tray icons - POP may be tucked in there. You can drag it out from that overflow area to keep it permanently visible.
- **The app seems to open and immediately close, with no tray icon appearing at all.** This usually indicates a corrupted installer download. Delete `Break.Reminder.Setup.1.0.0.exe`, re-download it from the Releases page, and try Step 2 again. If it persists, open an issue on the repository with your Windows version (`Settings → System → About`).

### Step 5 - (Optional) Enable Start on login

Right-click the tray icon → **Settings** → toggle **Start on login** → it saves automatically.

**What can go wrong:**
- **The toggle doesn't seem to do anything.** This setting takes effect on your *next* login, not immediately - it won't retroactively launch POP for your current session. Log out and back in (or restart) to confirm it worked.

You're done. POP is now installed and running on a 30-minute break interval by default.

---

## macOS - Installer Setup

This is the easiest path on macOS — no terminal, no Node.js, no build step. You're installing a pre-built application, the same way as the Windows section above.
 
### Step 1 — Download the .dmg
 
Go to the official website for the Windows version - [POP: Power Of Pausing](https://bit.ly/4eNCaCX)
 
**What can go wrong:**
- **Your browser shows a generic "this type of file can harm your computer" warning.** Some browsers warn on any `.dmg` download by default, regardless of the file. This isn't specific to POP — click "Keep" or "Keep anyway" to proceed.
- **The download says "check your internet connection" partway through, even though your connection is fine.** This usually means the download was interrupted or came through an intermediary that mangled the file (this happens with some messaging apps if the `.dmg` was shared that way rather than downloaded directly from Releases). Re-download directly from the Releases page link above.
### Step 2 — Open the .dmg
 
Double-click the downloaded `POP.dmg`. A Finder window appears showing the **POP** app icon next to a shortcut to your **Applications** folder.
 
**What can go wrong:**
- **Nothing happens when you double-click.** Check your Downloads folder — the file may still be finishing its download. Wait for it to complete, then try again.
### Step 3 — Install POP
 
Drag the **POP** icon into the **Applications** folder shown in that same Finder window.
 
**What can go wrong:**
- **Dragging POP into Applications says it already exists.** You've installed POP before. Either delete the old version from Applications first, or just let this drag overwrite it (macOS will ask to confirm — choose **Replace**).
### Step 4 — Eject the disk image
 
Once the drag finishes, eject the mounted `.dmg` — right-click it on your Desktop (or in the Finder sidebar) and choose **Eject**, or click the eject icon next to it in Finder's sidebar. This just ejects the disk image; it does not delete the app, since it's already copied into Applications.
 
### Step 5 — First launch
 
Open **Applications**, find **POP**, double-click it.
 
**What can go wrong:**
 
- **macOS says POP "is damaged and can't be opened," or "cannot be opened because it is from an unidentified developer."** Both messages point to the same underlying cause — this is Gatekeeper, macOS's built-in protection against unsigned apps, and neither wording means the file is actually corrupted. Because POP isn't signed with a paid Apple Developer certificate ($99/year), downloading it through a browser (which is exactly what Step 1 does) attaches a "quarantine" flag that triggers this warning. It's expected, not a sign anything is wrong.
  Two ways to proceed:
  **Option A — Terminal (fastest, and works even when the dialog only offers "Eject Disk Image"):**
```bash
  xattr -cr /Applications/POP.app
```
  Run this once — it must target the copy in `/Applications`, not the one still sitting in a mounted `.dmg` — then open POP normally. No more warning, ever, for this copy of the app.
 
  **Option B — System Settings:**
  1. Try to open POP once (it'll be blocked)
  2. Go to **System Settings → Privacy & Security**
  3. Scroll down — you'll see a message like *"POP was blocked to protect your Mac"* with an **Open Anyway** button next to it
  4. Click **Open Anyway**, then confirm once more in the dialog that follows
  5. POP opens normally from this point forward
- **No icon appears in the menu bar after opening.** Check the right side of your menu bar carefully — POP's icon is a small monochrome leaf silhouette, intentionally subtle so it matches other system icons. If your menu bar is very full, some icons may be hidden; macOS doesn't have a built-in overflow drawer like Windows does, so you may need to close another menu bar app temporarily to make room, or use a third-party menu bar organizer if you use one already.
### Step 6 — (Optional) Enable Start on login
 
Click the POP menu bar icon → **Settings** → toggle **Start on login**.
 
**What can go wrong:**
- **macOS shows its own permission prompt about login items.** This is normal — approve it. Without approval, the toggle will appear on but won't actually launch POP at your next login.
You're done. POP is now installed in Applications and running on a 30-minute break interval by default.
 
> **Building it yourself instead?** If you'd rather build POP from source — useful if you want to inspect or modify the code, or if no pre-built `.dmg` is available for your architecture — see [Running from Source](#running-from-source-any-os) below, which includes a one-step build script (`setup-mac.sh`) for macOS specifically.

**What can go wrong:**

- **macOS says POP "cannot be opened because it is from an unidentified developer," or blocks it outright with no clear option to proceed.** This is Gatekeeper, macOS's built-in protection against unsigned apps. Because POP isn't signed with a paid Apple Developer certificate, this can appear - though if you followed Step 2's instruction to use `git clone` rather than downloading a `.dmg` through a browser, you may not see this warning at all, since the quarantine flag Gatekeeper checks for is typically only set on files that came through a browser download.

  If you do see it, two ways to proceed:

  **Option A - System Settings:**
  1. Go to **System Settings → Privacy & Security**
  2. Scroll down - you'll see a message like *"POP was blocked to protect your Mac"* with an **Open Anyway** button next to it
  3. Click **Open Anyway**, then confirm once more in the dialog that follows
  4. POP opens normally from this point forward, every time

  **Option B - Terminal (one line, slightly faster):**
  ```bash
  xattr -cr /Applications/POP.app
  ```
  Run this once, then open POP normally from Applications - no more warning.

- **No icon appears in the menu bar after opening.** Check the right side of your menu bar carefully - POP's icon is a small monochrome leaf silhouette, intentionally subtle so it matches other system icons. If your menu bar is very full, some icons may be hidden; macOS doesn't have a built-in overflow drawer like Windows does, so you may need to close another menu bar app temporarily to make room, or use a third-party menu bar organizer if you use one already.

### Step 6 - (Optional) Enable Start on login

Click the POP menu bar icon → **Settings** → toggle **Start on login**.

**What can go wrong:**
- **macOS shows its own permission prompt about login items.** This is normal - approve it. Without approval, the toggle will appear on but won't actually launch POP at your next login.

You're done. POP is now installed in Applications and running on a 30-minute break interval by default.

---

## Uninstalling

**Windows:** `Settings → Apps → Installed apps`, find Break Reminder, click **Uninstall**.

**macOS:** open **Applications**, drag `POP.app` to the Trash.
