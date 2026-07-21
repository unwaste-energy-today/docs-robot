---
description: >-
  Install the Unwaste Robot application in your local Home Assistant
  environment.
---

# Local installation

This page describes installing the Unwaste application (add-on) in Home Assistant.

***

## Add the Unwaste repository

1. Open Home Assistant → **Settings** → **Apps** → **Install app**.
2. Open the menu (top left) → **Repositories**.
3. Add the Unwaste repository URL and click **Add**:

**https://gitlab.com/unwaste/public/unwaste-haos-repository-production**

4. Close the dialog. From the same menu, select **Check for updates**.
5. **Refresh the browser page** — Home Assistant does not reload the store automatically; the Unwaste add-on may not appear until you refresh.

***

## Install the application (add-on)

1. Find **Unwaste** on the add-on list and open it.
2. Click **Install** and wait for installation to finish.

***

## Configure the application

On the add-on **Configuration** tab:

* **Use external database** — leave off to use the built-in database (default).
* When **Use external database** is on, fill in server address, port, user, password, database name, and SSL as required.

When **Use external database** is off, leave the database connection fields empty.

See [Robot settings](<../Configuration/Robot settings.md>) for details.

***

## Start the add-on

On the add-on **Info** tab, enable:

* **Start on boot**
* **Watchdog** (recommended)
* **Show in sidebar** (recommended — opens the Unwaste panel)

Click **Start**. Open the Unwaste panel from the sidebar to complete [Initial configuration](initial-configuration.md).
