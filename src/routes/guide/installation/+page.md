---
title: Installing Mnemnk
---
This page explains how to install Mnemnk.

Mnemnk App is created using Tauri and can run on Windows, macOS, and Linux.
These installation instructions focus primarily on setting up Mnemnk in a Windows environment.

## Installing Mnemnk App (Windows)

Download Mnemnk App from the [GitHub releases page](https://github.com/mnemnk/mnemnk-app/releases). The files ending with `_aarch64.dmg` are for macOS, `_amd64.deb` for Linux, and `_x64_en-US.msi` for Windows.

![](/images/guide/installation/mnemnk-release-page.png)

If you see the following warning when opening the downloaded file, click "More info" and then click "Run anyway".

![](/images/guide/installation/windows-protect.png)

When you run it, a setup wizard will open. Follow the wizard to complete the installation.

![](/images/guide/installation/mnemnk-setup-wizard1.png)

![](/images/guide/installation/mnemnk-setup-wizard2.png)

You can install it anywhere you want.

![](/images/guide/installation/mnemnk-setup-wizard3.png)

Accept the UAC prompt when it appears.

![](/images/guide/installation/mnemnk-setup-wizard4.png)

Mnemnk App doesn't open a window just by launching it. You can confirm it's running in the system tray at the bottom right of your desktop.

To open the window, either select "Show" from the menu of the tray icon or double-click the icon created on the desktop.

## Configuring Mnemnk App

When you start Mnemnk for the first time, the Settings page will open. (If it doesn't appear, click the gear ⚙ icon)

![](/images/guide/installation/settings.png)

At a minimum, you need to configure the Mnemnk Directory.

### Mnemnk Directory

Specify an empty directory (folder) as the Mnemnk Directory. The following three directories will be created there:

- agent_flows: Where agent flows are saved
- agents: Place custom agents here
- data: Where the database and screenshots are saved

:::warning
Do not use directories in cloud storage (OneDrive, iCloud, etc.).
In the worst case, database files might get corrupted.
:::

After specifying the directory, you can leave the other settings at their defaults. Click "Save" and close Mnemnk App. When you restart it, the three directories mentioned above will be created in your specified location.

<Expansion title="Other Settings (Optional)" showIcon={false}>

### Auto Start

When enabled, Mnemnk App will automatically start when you login to your system.

### Shortcut Keys

- Global Shortcut: Shortcut to invoke Mnemnk App
- Fullscreen: Toggle full-screen display
- Screenshot Only: Hide information in the daily view. The space key is set by default
- Search: Open the search page

### Thumbnail Width / Height

The size of thumbnails used in the daily page. If only one dimension is specified, the image's aspect ratio will be maintained. If not specified, the default height is 36.

### Day Start Hour

Set what hour should be considered the start of a day on the daily page. The default is 0 (12:00 am). For night owls, the default setting may split late-night work between two days, so it's good to set this according to your bedtime.
(If you want to change past data as well, click Reindex YMD)

</Expansion>

## Summary

In this page, we explained how to install, launch, and run Mnemnk App.
