---
title: "Best package sources"
showtoc: false
hideMeta: true
---

Here is a list of what I believe are the best sources for software packages that may not be in a Linux distribution's package manager. I also give my reasoning.

My general priority list is:

1. Does the software author have a preferred method?
2. Does a recent version exist in Flathub? Preferably authored by the original software author.
3. Does a recent version exist in Snap store? Preferably authored by the original software author.
4. Is a native package (DEB in my case) available from the software author?

I know a lot of people hate Snaps. I don't particularly blame them, but I try to be pragmatic about it. Firefox and Thunderbird come as Snaps in Kubuntu and I don't bother to change that. I've also found that the Snap store provides first-class support for some smaller packages, too. Usually command-line utilities that Flatpak doesn't support.

| Package | Source | Reason |
| ------- | ------ | ------ |
| Chezmoi | Snap store | Officially sanctioned by Chezmoi and up-to-date |
| Discord | DEB file from Discord's website | The Snap package isn't authored by Discord and the Flathub version doesn't detect game activity |
| Firefox | Snap store | I use Kubuntu and it preinstalls as a Snap |
| Heroic | Flathub | Provided by Heroic |
| Hugo | Snap store | Authored by Hugo themselves and always up-to-date |
| Jetbrains tools | Jetbrains Toolbox | It's the official source and it doesn't require root privileges |
| OpenRGB | DEB file from OpenRGB's website | I've never gotten the AppImage or Flatpak to detect my RGB properly |
| Steam | Flathub | Provided by Valve and a very popular Flatpak |
| Sublime Merge | First-party APT | Sublime provides packages via their own APT server |
| Sublime Text | First-party APT | Sublime provides packages via their own APT server |
| Thunderbird | Snap store | I use Kubuntu and it preinstalls as a Snap |
