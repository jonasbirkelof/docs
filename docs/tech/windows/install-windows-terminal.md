---
title: Install Windows Terminal
---

This page will explain how to install Windows Terminal. You can download Windows Terminal using either **winget** or by downloading the binary from the [GitHub page](https://github.com/microsoft/terminal).

## Winget installation

Run this command to install:

```bash
winget install --id Microsoft.WindowsTerminal -e
```

??? info "Updating"
	
	The installation command is also used for updating Windows Terminal.

## Manual installation

<div class="steps" markdown>

1. Go to the [GitHub releases page](https://github.com/microsoft/terminal/releases).
1. Click on **Assets**.
1. Download the **.msixbundle** file.
1. Double click on the **.msixbundle** file you just downloaded to install.

</div>

## Configuration

You can navigate to **Settings** via the tab menu or by pressing ++ctrl+comma++ . Here you can make the settings you want for Windows Terminal och you can click on **Open JSON file** at the bottom left to open the **settings.json** file.

[Example config file](https://github.com/jonasbirkelof/docs/blob/master/files/windows-terminal/windows-terminal-settings.json).

You can set the individual shell icons. In the example config file you see what Icons I suggest, but feel free to download whatever you want.

[Download icons](https://icons8.com/icons).

## Starship

You can install [Starship](./install-starship.md) to get the most out of Windows Terminal by styling your command prompts with colors, fonts, symbols and more.