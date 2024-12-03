---
title: Remove Edge From the Taskbar
---

![](./images/ms-edge-ban.png)

If Microsoft Edge is automaticlly pinned to the taskbar after rebooting the PC, even after removing it, try these steps.

## Disable startup

<div class="steps" markdown>

1. Open Task Manager by right clicking on the start menu icon in the taskbar or by using the key combination ++ctrl+shift+esc++.

2. Open the **Startup** tab.

3. Right click on **Microsoft Edge** and select **Deactivate**.

</div>

Reboot your PC.

## Edit Layout Modification

<div class="steps" markdown>

1. Open the file:

    `%userprofile%\AppData\Local\Microsoft\Windows\Shell\LayoutModification.xml`

1. Search for the following line of code and delete it:

    ```xml title="LayoutModification.xml"
    <taskbar:UWA AppUserModelID="Microsoft.MicrosoftEdge_8wekyb3d8bbwe!MicrosoftEdge" />
    ```

1. Save and close the file.

</div>

Reboot your PC.