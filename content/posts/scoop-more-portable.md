---
title: "Making the Portable Toolkit More Portable"
description: "How to handle minor differences in configuration files between computers."
date: "2023-08-18"
tags:
  - Scoop
  - Windows
  - Developer Tips
---

One problem that may appear when creating a toolkit with [Scoop](https://scoop.sh) to be used between computers is the minor configuration differences necessary on different computers. For instance, your home directory may be different on a work computer vs your personal computer.

A simple solution is to create template files with placeholders that can be replaced with proper values after cloning the Scoop persist directory.

## Making template files

For any configuration file in your persist directory that will need to be different on different computers, create a duplicate of that file with the suffix **.template**. The original file should be added to the **.gitignore** file, and the **.template** file should be added to source control instead.

## Scripting the customizations

Two scripts can be created and then stored in the persist repository. One script will replace the machine-dependent values with some placeholder, and another script will expand the placeholder text with its proper value.

The following examples will replace a hard-coded user profile directory with the placeholder **%USERPROFILE%**. However, they can be expanded to cover more variables. I've chosen Powershell for the scripts because that is what Scoop already uses.

I refer to the script that replaces the hard-coded values with placeholders as the **compact** script, and the script that replaces the hard-coded values is the **expand** script.

### The compact script

Here is an example of a compact script. It simply recursively finds all files with a **.template** suffix. Then, it opens the original file (by removing the suffix) and scans for specific values that need to be replaced with placeholders.

```powershell
$files = Get-ChildItem -Recurse -Filter '*.template'

foreach ($f in $files) {
	$config = [System.Io.Path]::Join([System.Io.Path]::GetDirectoryName($f), [System.Io.Path]::GetFileNameWithoutExtension($f))
	Write-Host "$config -> $f"
	$winStyle = $env:USERPROFILE
	$unixStyle = $env:USERPROFILE.Replace('\', '/')
	(Get-Content $config).Replace($winStyle, "%USERPROFILE%", 'OrdinalIgnoreCase').Replace($unixStyle, "%USERPROFILE%", 'OrdinalIgnoreCase') | Set-Content $f
}
```

In this case, it uses the environment variable **USERPROFILE** to determine the home directory, which is a string that should be genericized. These strings are replaced with the placeholder **%USERPROFILE%**.

{{< notice note >}}
It is important to remember that on Windows, both '/' and '\\' can be used for directory path separators. That, along with case insensitivity, must be accounted for.
{{< /notice >}}

When any configuration changes are made, re-run the compact script to update the template file and then commit the changes.

### The expand script

The expand script does the reverse of the compact script, but it's a bit simpler because differences in path separators and case insensitivity don't need to be accounted for. Here is an example to complement the above compact script.

```powershell
$files = Get-ChildItem -Recurse -Filter '*.template'

foreach ($f in $files) {
	$config = [System.Io.Path]::Join([System.Io.Path]::GetDirectoryName($f), [System.Io.Path]::GetFileNameWithoutExtension($f))
	Write-Host "$f -> $config"
	$unixStyle = $env:USERPROFILE.Replace('\', '/')
	(Get-Content $f).Replace("%USERPROFILE%", $unixStyle) | Set-Content $config
}
```

{{< notice note >}}
Note that Unix-style directory separators are used. I find that these cause fewer problems since they won't need to be escaped ever.
{{< /notice >}}

## Summary

Hopefully, a couple of scripts like these can make your Scoop persistent configuration files more versatile. The ability to use the same developer tools and configurations on each computer you work on will lead to better efficiency and productivity. Thus, reducing any friction in making this happen is very valuable.
