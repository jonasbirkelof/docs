---
title: Starship
---

Starship lets you custimize you command line tool with icons, colors, fonts and more. Starship works well together with [Windows Terminal](./windows-terminal.md).

- Official website: [https://starship.rs](https://starship.rs)
- Tutorial by Christian Lempa: [https://www.youtube.com/watch?v=AK2JE2YsKto](https://www.youtube.com/watch?v=AK2JE2YsKto)

## Install Windows Terminal

Download and install [Windows Terminal](./windows-terminal.md).

```bash
winget install --id Microsoft.WindowsTerminal -e
```

## Install a Nerd Font

To display symbols correctly, we need to install a "[Nerd Font](https://www.nerdfonts.com/)", for instance [JetBrainsMono Nerd Font](https://github.com/ryanoasis/nerd-fonts/releases/download/v3.2.1/JetBrainsMono.zip). 

Install it just like a normal font and set it as default in Windows Terminal. Refer to the [configuration documentation](./windows-terminal.md#configuration) for an example config file.

```json title="settings.json"
{
    "profiles": 
    {
        "defaults": 
        {
            "font": 
            {
                "face": "JetBrainsMonoNL Nerd Font"
            }
		}
	}
}
```

## Install Starship

Install Starship using `winget`.

```bash
winget install starship
```

## Configure Starship

Create the file `C:\Users\<USERNAME>\.config\starship.toml`.

[Example config file](../files/starship/starship.toml)

## Initialize Starship

### Bash

<div class="steps" markdown>

1. Open **Bash** and type the following to reveal the path to the config file. In should be the user root directory `C:\Users\<USERNAME>`.

	```bash
	echo ~
	```

1. Navigate to that folder and create the file `.bash_profile`.

	```bash
	cd c:\Users\<USERNAME>
	```

	```bash
	nano .bash_profile
	```

1. Add this code at the bottom of the file:

	``` title=".bash_profile"
	eval "$(starship init bash)"
	```

1. In Windows Terminal `settings.json`, add the following code under `profiles`:

	```json title="settings.json"
	"list":
	[
		{
			"commandline": "%PROGRAMFILES%/Git/bin/bash.exe -i -l",
			"guid": "{1fc853bf-83b3-4555-9230-8b010466f547}",
			"hidden": false,
			"icon": "C:\\Users\\<USERNAME>\\Windows Terminal Icons\\icons8-git-100-white.png",
			"name": "Git Bash",
			"startingDirectory" : "%USERPROFILE%"
		}
	]
	```

	The `icon` property is optional.

</div>

### Command Prompt (cmd)

<div class="steps" markdown>

1. Install [Clink](https://chrisant996.github.io/clink/clink.html).

	```bash
	winget install clink
	```

1. Open the scripts directory `C:\Users\<USERNAME>\AppData\Local\clink`. 
Read more about file locations on the [documentation page](https://chrisant996.github.io/clink/clink.html#location-of-lua-scripts) if you experienses problems.

1. Create the file `starship.lua` and add the following code:

	``` title="starship.lua"
	load(io.popen('starship init cmd'):read("*a"))()
	```

</div>

### PowerShell

<div class="steps" markdown>

1. Open a PowerShell prompt and open the profile file in VS Code.

	```bash
	code $PROFILE
	```

1. Add the following code.

	```bash title="Microsoft.PowerShell_profile.ps1"
	Invoke-Expression (&starship init powershell)
	```

</div>