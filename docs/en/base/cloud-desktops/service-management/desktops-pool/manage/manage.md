<info>

You can also [manage all desktops](../../manage-desktops/) created in the system for all pools.

</info>

## Viewing a list of desktop pools

1. Go to your VK Cloud [personal account](https://msk.cloud.vk.com/app/en).
1. Go to **Cloud Desktop** → **Desktop pools**.

   A list of previously created desktop pools is displayed.

   The status of the pool is displayed to the left of its name:

   - Green — **Available** for connecting new desktops.
   - Gray — **Unavailable** for connecting desktops.

## Managing pool desktops

### Reboot

<info>

Available for desktops, where VM is in an emergency state.

</info>

This is a group operation: if necessary, you can reboot multiple pool desktops by selecting them using checkboxes.

1. Go to your VK Cloud [personal account](https://msk.cloud.vk.com/app/en).
1. Go to **Cloud Desktop** → **Desktop pools**.
1. In the list of pools, click on the name of the desired pool.
1. Go to the **Desktops** tab.
1. Check the box for the desired desktop.
1. Click **More** and select the **Restart** option.
1. Confirm the action.

### Terminating a session

It is used to force the termination of the user's session.

<info>

The VM remains turned on at the end of the session.

</info>

This is a group operation: if necessary, you can terminate sessions on multiple pool desktops by selecting them using checkboxes.

1. Go to your VK Cloud [personal account](https://msk.cloud.vk.com/app/en).
1. Go to **Cloud Desktop** → **Desktop pools**.
1. In the list of pools, click on the name of the desired pool.
1. Go to the **Desktops** tab.
1. Check the box for the desired desktop.
1. Click **More** and select the **End session** option.
1. Confirm the action.

## Sending a message to pool users

This is a group operation: if necessary, you can send a message to users of several pools by selecting them using checkboxes.

1. Go to your VK Cloud [personal account](https://msk.cloud.vk.com/app/en).
1. Go to **Cloud Desktop** → **Desktop pools**.
1. Check the box for the desired pool.
1. Click the **Message to users** button.
1. In the window that appears, fill in the fields:

   - **Message type**: select one of the options: **Warning**, **Informational** or **Error**.
   - **Message text**: specify the information you want to convey to the pool users.

1. Click the **Send message** button.

## Deleting a desktop pools

<warn>

When deleting a desktop pool, pay attention to the following:

- The deleted pool cannot be restored.
- If there are desktops in the pool, they will also be deleted when the pool is deleted.
- When deleting the last pool in your project, all the settings for connecting to the user directory will also be deleted.

</warn>

This is a group operation: if necessary, you can delete several pools at once by selecting them using checkboxes.

1. Go to your VK Cloud [personal account](https://msk.cloud.vk.com/app/en).
1. Go to **Cloud Desktop** → **Desktop pools**.
1. Delete the pool using one of the following methods:

   - Click ![ ](/ru/assets/menu-icon.svg "inline") of the desired pool and select **Delete**.
   - Via the pool page:

     1. In the list of pools, select the pool you want to delete and click on its name.
     1. Go to the **Parameters** tab.
     1. Click ![Trash](assets/trash-icon.svg "inline") in the upper right corner of the tab.

1. Confirm the deletion.
