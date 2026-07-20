# Sharing an Unwaste Robot

### Overview

Sharing an **Unwaste Robot** allows the owner to grant another Unwaste Cloud user access to the same installation.

This functionality is primarily intended for:

* installers supervising client installations,
* technicians providing support,
* companies managing internal energy systems.

Sharing is a cloud-level access control mechanism. It does not transfer ownership and does not affect billing or account status.

***

### What sharing allows

When you share an Unwaste Robot with another user:

* The robot appears in their robot list immediately.
* They gain access to the full configuration and operational interface.
* They can modify settings, control devices, and change system configuration.
* They can view the complete historical data (statistics, graphs, alerts) from the beginning.

There is no limitation to historical data visibility.

Important:\
Actions performed by shared users are indistinguishable from actions performed by the owner. There is currently no action-level attribution.

***

### What shared users cannot do

A shared user:

* Cannot share the Unwaste Robot further with other users.
* Does not see the **Share Robot** panel.
* Cannot disconnect the robot from the cloud (this function is available only in the local interface).

The owner remains the only user who can manage sharing.

***

### How to share the Unwaste Robot

Sharing is performed from the **Cloud** tab of the Unwaste Robot settings.

1. Open the robot in the Unwaste Cloud interface.
2. Go to the **Cloud** section.
3. Locate the **Share Robot** panel.
4. Enter the email address of the user.
5. Click **Create**.

<figure><img src="../../.gitbook/assets/Screenshot_sharing_robot.png" alt=""><figcaption></figcaption></figure>

#### Email requirements

* The email must have a valid email format.
* The email must correspond to an existing Unwaste Cloud account.
* Sharing with your own email is blocked (the system will return an error indicating the account is already the owner).

The system does not send invitation emails. If the account does not exist, the share attempt fails with an error.

After successful sharing:

* The robot appears immediately in the other user’s robot list.
* Access is active without additional confirmation.

***

### Share name behavior

When sharing a robot, you provide a name under which it will appear for the shared user.

Important details:

* This name is the initial display name for that user.
* The shared user can change this name.
* If the shared user changes the name, the updated name is also visible to the owner in the sharing list.
* The owner cannot directly edit the share name (except by removing and recreating the share, which is not recommended).

This design allows installers managing many installations to assign clear identifiers (for example client names or addresses).

***

### Managing shared access

The **Share Robot** panel displays a table of all users who currently have access.

The table includes:

* Share name
* User (email address)
* Action (Remove)

The owner can remove access at any time by clicking **Remove**.

Revocation behavior:

* Access is removed immediately.
* The robot immediately stops accepting commands from that user.
* The robot disappears from the user’s robot list shortly after.
* No notification is currently sent to the removed user.

There is currently no defined limit to the number of users a robot can be shared with.

***

### Ownership and visibility

The owner of the robot is the account that originally connected the Unwaste Robot to the cloud.

Owner information (account email) is visible in the Cloud settings section for both the owner and shared users.

Sharing does not transfer ownership. The owner retains full control over access management.

***

### Lifecycle behavior

If the owner:

* Disconnects the Unwaste Robot from the cloud, or
* Deletes their Cloud Account,

all shared users immediately lose access and the robot disappears from their lists.

***

### Notes / Important

* Shared users receive broad configuration access. Only share with trusted accounts.
* There is no activity log distinguishing owner and shared user actions.
* Sharing does not affect ownership or billing.
* Access changes (granting or removing) take effect immediately.
