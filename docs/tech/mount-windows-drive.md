---
title: Mount a Windows Drive
---

This page explains how to mount a shared folder on Windows to Linux. Make sure that the folder you want to share from the PC is shared before you proceed.

## Persisting mount

<div class="steps" markdown>

1. Create a directory where the drive will be mounted, for example in root `/` or in `/mnt`.

	```bash
	cd /
	```

	```bash
	sudo mkdir Media
	```

1. Open fstab:

	```bash
	sudo nano /etc/fstab
	```

1. Add the following at the bottom of the file.

	```
	//<IP>/<SHARE/FOLDER_NAME> <MOUNT_FOLDER> <SHARE_TYPE> username=<USERNAME>,password=<PASSWORD> 0 0
	```

	- Change `<IP>/<SHARE/FOLDER_NAME>` to the path of your shared folder that you want to mount. If you use a share on e.g. TrueNAS, you put the name of the share.
	- Change `<MOUNT_FOLDER>` to the path of the folder you created earlier.
	- Change `<SHARE_TYPE>` to the chare type.
	- Change `<USERNAME>` and `<PASSWORD>` to the credentials nedded to access the shared folder. It can be the Windows user account credentials or the user credentials for the network share.
	- The two `0`'s at the and should always be present and means that the mount should not be becked up and that it should not be checked by `fscheck` (filesystem check) since it does not handle wetwork shares anyway.

	```title="Example"
	//192.168.1.1/Media /Media cifs username=user,password=password 0 0
	```

1. Save the file and exit. Now the folder will be mounted when the VM boots.

1. Check if the mount worked by `cd` into the directory and run `ls`:

	```bash
	cd /Media
	```

	```bash
	ls
	```

1. Restart the VM for the changes to take effect.

	```bash
	sudo reboot
	```

	!!! tip

		You can run `sudo mount -a` if you want to reload the mounts withoud rebooting.

</div>

## Non-persisting mount

This method is not recommended in most cases.

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
		
		Example: share the whole `E:` drive named `Plex media` from a PC with IP `192.168.1.100`. The path to that drive is `//192.168.1.100/'Plex media'`.

	- Change `/mnt/shared_folder` to the path of the target folder you created before.

</div>