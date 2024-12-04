---
title: Windows Terminal
---

This page will explain how to install Windows Terminal. You can download Windows Terminal using either **winget** or by downloading the binary from the [GitHub page](https://github.com/microsoft/terminal).

## Winget installation

Run this command to install:

```bash
winget install --id Microsoft.WindowsTerminal -e
```

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

??? note "settings.json example"

	```json
	{
		"$help": "https://aka.ms/terminal-documentation",
		"$schema": "https://aka.ms/terminal-profiles-schema",
		"actions": 
		[
			{
				"command": 
				{
					"action": "copy",
					"singleLine": false
				},
				"keys": "ctrl+c"
			},
			{
				"command": "paste",
				"keys": "ctrl+v"
			},
			{
				"command": 
				{
					"action": "splitPane",
					"split": "auto",
					"splitMode": "duplicate"
				},
				"keys": "alt+shift+d"
			},
			{
				"command": "find",
				"keys": "ctrl+shift+f"
			}
		],
		"copyFormatting": "none",
		"copyOnSelect": false,
		"defaultProfile": "{0caa0dad-35be-5f56-a8ff-afceeeaa6101}",
		"firstWindowPreference": "defaultProfile",
		"newTabMenu": 
		[
			{
				"type": "remainingProfiles"
			}
		],
		"profiles": 
		{
			"defaults": 
			{
				"colorScheme": "Tango Dark",
				"font": 
				{
					"face": "JetBrainsMonoNL Nerd Font"
				},
				"opacity": 85,
				"useAcrylic": false
			},
			"list": 
			[
				{
					"commandline": "%SystemRoot%\\System32\\cmd.exe",
					"experimental.retroTerminalEffect": false,
					"guid": "{0caa0dad-35be-5f56-a8ff-afceeeaa6101}",
					"hidden": false,
					"icon": "C:\\Users\\<USERNAME>\\Windows Terminal Icons\\icons8-windows-90.png",
					"name": "Command Prompt"
				},
				{
					"background": "#012456",
					"commandline": "%SystemRoot%\\System32\\WindowsPowerShell\\v1.0\\powershell.exe",
					"guid": "{61c54bbd-c2c6-5271-96e7-009a87ff44bf}",
					"hidden": false,
					"icon": "C:\\Users\\<USERNAME>\\Windows Terminal Icons\\icons8-powershell-100-blue.png",
					"name": "Windows PowerShell"
				},
				{
					"background": "#012456",
					"guid": "{574e775e-4f2a-5b96-ac1e-a2962a402336}",
					"hidden": false,
					"icon": "C:\\Users\\<USERNAME>\\Windows Terminal Icons\\icons8-powershell-100-white.png",
					"name": "PowerShell v.7",
					"source": "Windows.Terminal.PowershellCore"
				},
				{
					"commandline": "%PROGRAMFILES%/Git/bin/bash.exe -i -l",
					"guid": "{1fc853bf-83b3-4555-9230-8b010466f547}",
					"hidden": false,
					"icon": "C:\\Users\\<USERNAME>\\Windows Terminal Icons\\icons8-git-100-white.png",
					"name": "Git Bash",
					"startingDirectory": "%USERPROFILE%"
				},
				{
					"guid": "{51855cb2-8cce-5362-8f54-464b92b32386}",
					"hidden": false,
					"icon": "C:\\Users\\<USERNAME>\\Windows Terminal Icons\\icons8-ubuntu-96-white.png",
					"name": "Ubuntu",
					"source": "CanonicalGroupLimited.Ubuntu_79rhkp1fndgsc"
				}
			]
		},
		"schemes": 
		[
			{
				"background": "#022A33",
				"black": "#0C0C0C",
				"blue": "#0037DA",
				"brightBlack": "#767676",
				"brightBlue": "#3B78FF",
				"brightCyan": "#61D6D6",
				"brightGreen": "#16C60C",
				"brightPurple": "#B4009E",
				"brightRed": "#E74856",
				"brightWhite": "#F2F2F2",
				"brightYellow": "#F9F1A5",
				"cursorColor": "#FFFFFF",
				"cyan": "#3A96DD",
				"foreground": "#FFFFFF",
				"green": "#13A10E",
				"name": "JB",
				"purple": "#881798",
				"red": "#C50F1F",
				"selectionBackground": "#FFFFFF",
				"white": "#CCCCCC",
				"yellow": "#C19C00"
			}
		],
		"themes": [],
		"useAcrylicInTabRow": false
	}
	```

[Download the settings.json example file](../files/windows-terminal/windows-terminal-settings.json).

You can set the individual shell icons. In the example config file you see what Icons I suggest, but feel free to download whatever you want.

[Download icons](https://icons8.com/icons).

## Starship

You can install [Starship](./starship.md) to get the most out of Windows Terminal by styling your command prompts with colors, fonts, symbols and more.