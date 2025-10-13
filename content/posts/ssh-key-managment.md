---
title: "Getting KDE to remember your SSH key passphrase"
summary: "How to prevent needing to type your SSH passphrase all the time"
date: "2025-10-12"
tags:
  - KDE
  - Linux
---

If you use your SSH private key a lot, for example, with Git, it can be nice to have KDE remember your SSH key passphrase for you. There are a couple steps required for that to work. Here they are for KDE using KDE Wallet.

## Install the SSH askpass interface

Make sure you have KDE's interface to SSH askpass, **ksshaskpass**, installed.  Make a note of where it is installed. I know on OpenSUSE, it's not in the PATH, but in **/usr/libexec/ssh/**.

## Configure SSH

Next, configure SSH to add keys to the KDE wallet. Do this by adding `AddKeysToAgent yes` to **~/.ssh/config**.

## Setup ssh-askpass/ksshaskpass

Finally, a couple environment variables need to be setup to configure **ksshaskpass** correctly. To set these environment variables, I add them to a file under **~/.config/environment.d** called **ssh.conf**. Here is the contents of that file that shows the two environment variables that need to be set:

```
SSH_ASKPASS=/usr/libexec/ssh/ksshaskpass
SSH_ASKPASS_REQUIRE=prefer
```

For the **SSH_ASKPASS** variable, use the location to **ksshaskpass** that you noted from the first step.

> [!TIP]
> I add this file to my [Chezmoi](https://www.chezmoi.io/) repository.

## Conclusion

Don't forget to log out and then log back in so the environment variables will be updated. Now you should only need to type your SSH key passphrase in one more time to add it to the wallet.

Enjoy!
