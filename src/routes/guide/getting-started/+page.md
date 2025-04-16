---
title: Getting Started
---

## Installing Mnemnk

This section explains how to get started with Mnemnk.
We'll also explain how to set up a basic lifelogging environment using Mnemnk, including the setup of Mnemnk App and Mnemnk Core Agents.

### Environment Setup

Before installing Mnemnk, you need to configure your environment and ensure several prerequisites are met for Mnemnk to function properly.

#### OS Selection

Mnemnk App is created using Tauri and can run on Windows, macOS, and Linux.
Among the Mnemnk Core Agents, the Mnemnk API agent can run on Linux, but the Mnemnk Application agent and the Mnemnk Screen agent currently don't support Linux.
This installation guide primarily focuses on setting up Mnemnk in a Windows environment.

#### Installing Various Build Tools

While pre-built binaries of Mnemnk App are available from GitHub, many agents, including Mnemnk Core Agents, assume that users have their own development environment.

The tools you need will vary depending on the agent.
For the installation described on this page, you'll need Git and Rust.

- [Git](https://git-scm.com/)
- [Rust](https://www.rust-lang.org/ja/learn/get-started)

### Installing Mnemnk App (Windows)

Download Mnemnk App from the [GitHub releases page](https://github.com/mnemnk/mnemnk-app/releases). The `_aarch64.dmg` file is for macOS, `_amd64.deb` is for Linux, and `_x64_en-US.msi` is for Windows.


![](/images/guide/getting-started/mnemnk-release-page.png)

If you see the following warning when opening the downloaded file, click "More info" and then click "Run anyway".

![](/images/guide/getting-started/windows-protect.png)

When you run it, a setup wizard will open. Follow the wizard to complete the installation.

![](/images/guide/getting-started/mnemnk-setup-wizard1.png)

![](/images/guide/getting-started/mnemnk-setup-wizard2.png)

You can install it anywhere you want.

![](/images/guide/getting-started/mnemnk-setup-wizard3.png)

Accept the UAC prompt when it appears.

![](/images/guide/getting-started/mnemnk-setup-wizard4.png)

Mnemnk App doesn't open a window just by launching it. You can confirm it's running in the system tray at the bottom right of your desktop.

To open the window, either select "Show" from the menu of the tray icon or double-click the icon created on the desktop.

### Configuring Mnemnk App

When you start Mnemnk for the first time, the Settings page will open. (If it doesn't appear, click the gear ⚙ icon.)


![](/images/guide/getting-started/settings.png)

At a minimum, you need to configure the Mnemnk Directory.

#### Mnemnk Directory

Specify an empty directory (folder) as the Mnemnk Directory. The following three directories will be created there:

- agent_flows: Where agent flows are saved.
- agents: Place agents here.
- data: Where the database and screenshots are saved.

:::warning
Directories in cloud storage (OneDrive, iCloud, etc.) are not recommended.
Database files might be corrupted.
:::

<Expansion title="Other Settings (Optional)" showIcon={false}>

#### Auto Start

When enabled, Mnemnk App will automatically start when you login.

#### Shortcut Keys

- Global Shortcut: Shortcut to invoke Mnemnk App.
- Fullscreen: Full-screen display
- Screenshot Only: Hide information in the daily view. The space key is set by default.
- Search: Go to the search page

#### Thumbnail Width / Height

The size of thumbnails used in the daily page. If only one is specified, the aspect ratio of the image will be preserved. The default is `Height = 36`.

#### Day Start Hour

Set what hour should be considered the start of a day on the daily page. The default is 0 (12:00 am). Night owls might find that with the default setting, late-night work is split between two days, so it's good to set this according to your bedtime.

If you change this setting, click Reindex YMD to reindex past data. (Don't close the app for a while after clicking.)

</Expansion>

### Installing Mnemnk Core Agents

[Mnemnk Core Agents](https://github.com/mnemnk/mnemnk-core-agents) is a collection of basic agents that are essential for utilizing Mnemnk as a lifelogging tool[^1].

- [Mnemnk Application](https://github.com/mnemnk/mnemnk-core-agents/tree/main/mnemnk-application): Outputs application activity
- [Mnemnk Screen](https://github.com/mnemnk/mnemnk-core-agents/tree/main/mnemnk-screen): Outputs screen captures
- [Mnemnk API](https://github.com/mnemnk/mnemnk-core-agents/tree/main/mnemnk-api): Acts as an API server to output information from external applications

Clone the repository into the "agents" directory that was created in the Mnemnk Directory you specified during Mnemnk App installation.

```sh
cd {You Mnemnk Directory}/agents
git clone https://github.com/mnemnk/mnemnk-core-agents.git
```

Build the executable binaries in the cloned directory.

```sh
cd mnemnk-core-agents
cargo build --release
```

Restart Mnemnk App, and open Core from the Agents menu in the upper right. You'll see that Application, API, and Screen have been added.

![](/images/guide/getting-started/agents-menu.png)

Choose Import from the File menu, and a file dialog will appear. Select `logging.json` from the `mnemnk-core-agents/` directory you cloned earlier.

The agents will be loaded in a stopped state, so press the play button ▶ at the bottom center to start the agents.

![](/images/guide/getting-started/screenshot-core-agents-imported.png)

When started, the agents' colors will brighten.

![](/images/guide/getting-started/screenshot-core-agents.png)

Select "Save" from the File menu to save the configuration. (It will be saved to `agent_flows/logging.json`)

Click Home at the left end of the navigation bar at the top of the screen, and reload (Ctrl+R). You'll notice that today's date has changed, indicating that data has been saved. 

![](/images/guide/getting-started/first-logging.png)

Click to check it out.

![](/images/guide/getting-started/first-daily-page.png)

Congratulations! 🎉

#### Setting Up Auto Start

Recording only happens while Mnemnk App is running in the background. To keep recording continuously, it's recommended to turn on "Auto Start" on the Settings page so that Mnemnk App starts when you login to the OS. Don't forget to Save and restart Mnemnk App after turning it on.

### Installing Mnemnk Browser Extension

What the author personally finds most useful is the integration with web browsing through the browser.
In fact, Mnemnk's development began with this feature[^2].

Using the [Mnemnk Browser Extension](https://github.com/mnemnk/mnemnk-browser-extension), page navigations in the browser are sent to the Mnemnk API and can be utilized by Mnemnk App.

To install it[^3]:

1. Open the release page and download `mnemnk-X.Y.Z-chrome.zip`.
2. Open Chrome's Manage extensions `chrome://extensions/`.
3. Turn on "Developer mode" in the upper right.
4. Drag and drop the downloaded zip file into the browser.

You can specify the address and token for the Mnemnk API agent in the options, but the defaults are fine. It's good to change these when you change the settings of the Mnemnk API agent.

### Summary

In this section, we learned how to install, set up, and run Mnemnk App. We also explained how to install Mnemnk Core Agents and the Mnemnk Browser Extension.
As you can see from the fact that even the basic lifelogging function of Mnemnk App is provided as an external program, the information Mnemnk App collects and how it is utilized depends on how you build your agents. You can use Mnemnk as a lifelogging tool as the author envisions, or not.

[^1]: Despite being labeled "Core," you actually don't need to install these if you're not aiming for lifelogging. We're also considering changing the name.

[^2]: Development initially began in March 2020 under the name "everything." That's a story for another time.

[^3]: We're also working on submitting it to the Chrome Web Store, but there are various procedures needed, such as having a homepage with a Privacy Policy...
