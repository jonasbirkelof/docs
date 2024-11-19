---
title: Set a Static IP
---

This page will explain how to set a static IP in Linux.

<div class="steps" markdown>

1. Get the network adaptor

	```bash
	ip link
	```

	Find the adaptor named `ethx`, `ensx` or something similar.

1. Get IP and subnet mask (and more). Use the adaptor from the previous step, for example `eth0`.

	```bash
	nmcli dev show eth0
	```

	```bash
	ifconfig eth0
	```

1. `cd` into `/etc/netplan` and run `ls` to see the config files. 

	```bash
	cd /etc/netplan
	ls
	```

1. Open the file named `01-netcfg.yaml` (or something similar) using nano **as root user**:

	```bash
	sudo nano 01-netcfg.yaml
	```

	```yaml title="01-netcfg.yml"
	network:
	version: 2
	ethernets:
		eth0:
		dhcp4: no
		addresses:
			- 192.168.1.100/24
		gateway4: 192.168.1.1
		nameservers:
			addresses:
			- 8.8.8.8
			- 1.1.1.1
	```

	- Change the address `192.168.1.100/24` to the desired IP.
	- Change `eth0` to the name of your network adaptor.

1. Apply the changes:

	```bash
	sudo netplan apply
	```

1. Check if it worked:

	```bash
	ip addr show eth0
	```