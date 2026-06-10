# Installing Google Antigravity 2.0 on Chromebook (ChromeOS Linux)

This repository contains the setup configurations, launcher shortcut scripts, and step-by-step documentation for deploying **Google Antigravity 2.0** locally within the ChromeOS Linux developer environment.

<a href="https://youtu.be/S9D3hCkunfE">
  <img src="antigravity-Chromebook-play.jpg" width="720" alt="EP2">
</a>

[How to Install Google Antigravity 2.0 on Chromebook](https://youtu.be/S9D3hCkunfE)

This guide walk you through enabling your development container, configuring the **Command Line Interface (CLI)** version (`agy`), deploying the native **Desktop Graphical User Interface (GUI)** version, and creating a native app icon shortcut.

---

## 🛠️ Prerequisites & Requirements
* **Device:** A Chromebook with an x86_64 processor that supports the native ChromeOS Linux Environment.
* **Storage Allocation:** At least **10 GB** of custom disk space dedicated to your Linux partition (required for platform dependencies, agent caching, and IDE runtime files).
* **Network:** Active internet connection for Google OAuth terminal loops and package syncs.

---

## 🚀 Step-by-Step Installation Guide

### Step 1: Enable the Chromebook Linux Environment
Before running local platform binaries, you must activate the underlying Debian container on ChromeOS:
1. Navigate to your Chromebook **Launcher** ➔ open **Settings**.
2. Scroll to the bottom of the left-hand panel and click on **About ChromeOS** ➔ **Developer Options**.
3. Next to **Linux Development Environment**, click **Turn On**.
4. During configuration prompts, specify a custom disk size allocation of **at least 10 GB**.
5. Once installation finishes, a terminal instance running under the default container (`penguin`) will automatically open.

---

### Step 2: Install the Antigravity CLI (`agy`)
The platform uses an interactive command-line assistant to handle configurations and dependencies. Execute the official setup script directly inside your Linux terminal:

```bash
curl -fsSL [https://antigravity.google/cli/install.sh](https://antigravity.google/cli/install.sh) | bash

```
---

### Step 3: Add the CLI Binary to Your Active PATH
To allow the terminal to recognize the agy command globally from any active directory path, update your shell profile configurations:

```bash
echo 'export PATH="$HOME/.local/bin:$PATH"' >> ~/.bashrc && source ~/.bashrc
```
---

> [!TIP]
> Verify your shell registration path by typing `agy` into the terminal. You will be prompted to authenticate your local instance using your Google Account details via a standard browser OAuth loop.

---

### Step 4: Download and Prepare the Desktop GUI Folder
To bypass the default web portal limitations and execute actions natively in a sandbox layout, pull down the desktop files:
1. Go to the official website: **Google Antigravity Platform (https://antigravity.google)**.
2. Download the **Linux version x64** zip package file.
3. Open the ChromeOS **Files** application, click **Downloads**, and unzip the directory package.
4. Right-click the extracted folder and select **Share with Linux**.
5. Alternatively, shift the unzipped directory straight into the local file container workspace manually using your terminal environment:
```bash
cp -r /mnt/chromeos/MyFiles/Downloads/antigravity ~/antigravity

```
---

### Step 5: Move the Extracted GUI Folder to `/opt`
To maintain standard application structures and ensure proper global user access across the subsystem, move the platform workspace to your shared opt folder:
```bash
sudo mv ~/antigravity /opt/antigravity

```
---

### Step 6: Make the Desktop App Executable
Update the read, write, and execute permissions of the main desktop engine layer so your system registers the file correctly as a runnable application package:
```bash
sudo chmod +x /opt/antigravity/antigravity

```
---

### Step 7: Create Your Chromebook Launcher Shortcut (`.desktop` File)
To start the editor visually from your ChromeOS shelf or search menu without keeping a terminal path continuously active, generate an application desktop shortcut file.

1. Synchronize your package lists and install the terminal text editor interface tool `nano` if it is not already configured in your container:
```bash
sudo apt-get update && sudo apt-get install nano
```

2. Establish the local applications reference storage path and open a new configuration shortcut file:
```bash
mkdir -p ~/.local/share/applications
nano ~/.local/share/applications/antigravity.desktop
```

3. Copy and paste the exact configuration properties block layout directly into the editor view:
```bash
[Desktop Entry]
Version=1.0
Type=Application
Name=Antigravity
Comment=Agentic Editor
Exec=/opt/antigravity/antigravity --no-sandbox
Icon=/opt/antigravity/resources/app/resources/linux/code.png
Terminal=false
Categories=Development;IDE;
```

> [!IMPORTANT]
> The inclusion of the `--no-sandbox` parameter execution argument inside the string flag block is mandatory. Chromebook containers run on isolated microVM spaces that do not permit double-nested sandboxing profiles by default; omitting this string will cause the UI initialization layer to crash.

4. To close out and write your file alterations to the workspace, press `Ctrl + X`, hit `Y` to verify compilation tracking updates, and press `Enter`.

---

## 🎉 Launching the Desktop Workspace
Your configuration layout is completely optimized! To pull up the developer application interface:
1. Hit the physical **Search / Launcher** button on your keyboard.
2. Drill down into the custom **Linux Apps** application directory group drawer.
3. Tap the brand-new native **Antigravity** icon launch shortcut to access your multi-agent sandbox profile.

---

## 📚 A Woman's Guide to Winning in Tech

If you enjoyed this repo, check out the book **A Woman's Guide to Winning in Tech** — blending sharp humor with practical career strategies to help women navigate tech on their own terms.

- [Book Website](https://winningintech.com/)
- [Amazon](https://amzn.to/3YxHVO7)
- [Instagram](https://www.instagram.com/winning.tech)
- [Facebook](https://www.facebook.com/winningintech)
