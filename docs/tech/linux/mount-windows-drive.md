---
title: Mount a Windows Drive
---

This page explains how to mount a shared folder on Windows to Linux. Make sure that the folder you want to share from the PC is shared before you proceed.

<div class="steps" markdown>

1. Create a directory for the mounted drive.

	```bash
	sudo mkdir -p /mnt/shared_folder
	```

1. Mount the drive.
	
	```bash
	sudo mount -t cifs -o username=your_username,password=your_password //remote-pc-ip/shared_folder /mnt/shared_folder
	```

	- Change `your_username` and `your_password` to the Microsoft account credentials.
	- Change `//remote-pc-ip/shared_folder` to the path to the shared folder. 
		
		Example:	 share the whole `E:` drive named `Plex media` from a PC with IP `192.168.1.100`. The path to that drive is `//192.168.1.100/'Plex media'`.

	- Change `/mnt/shared_folder` to the path of the target folder you created before.

</div>