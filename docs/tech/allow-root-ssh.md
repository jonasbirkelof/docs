---
title: Allow SSH Login as Root User
---

This page will explain how to allow the root user to login via SSH.

!!! warning

	This feature is disabled by default for security reasons.

<div class="steps" markdown>

1. Open the SSH configuration file on your server:

	```bash
	sudo nano /etc/ssh/sshd_config
	```

1. Look for the line that says `PermitRootLogin` and remove the comment `#`.
1. By default, the value of `PermitRootLogin` is often set to `prohibit-password` or `no`. Change it to `yes` if you want to allow root login:

	```bash title="sshd_config"
	PermitRootLogin yes
	```
 
1. Restart the SSH Service to apply the changes:

	```bash
	sudo systemctl restart sshd
	```

</div>