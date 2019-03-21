# Instructions to set up the all Manuel's repos
Currently there are three repos available:

Name | Purpose
---- | -------
antergos-m | Packages created by Manuel
antergos-maur | A selection of AUR packages
antergos-mup | Packages to update some Antergos packages

The following instructions show how to get started with the repos.

## Edit /etc/pacman.conf
Add all (or a selection) of the following repo definitions:
```
# Prebuilt and up to date AUR packages for Antergos.
# Place this before the [antergos] repo definition since these packages are meant to replace
# matching packages of the Antergos repo.
[antergos-mup]
Server = https://github.com/manuel-192/antergos-mup/raw/master
SigLevel = Required


# Packages created and published by Manuel.
# Place this repo preferably in the end of the file since these packages shouldn't conflict with other repos.
[antergos-m]
Server = https://github.com/manuel-192/antergos-m/raw/master
SigLevel = Required


# Selection of prebuilt packages from AUR.
# Place this repo preferably in the end of the file since these packages shouldn't conflict with other repos.
[antergos-maur]
Server = https://github.com/manuel-192/antergos-maur/raw/master
SigLevel = Required
```
## Add the maintainer's gpg key to your system
but only if you trust the maintainer and these packages!<br><br>
Run the following commands (unless you haven't already done so):
```
sudo pacman-key --recv-keys A1F1B5187D25904B
sudo pacman-key --lsign-key A1F1B5187D25904B
```
You should see token **manuel-192** inside the output of the these last commands.
If not, check that the added key was correct.

That's it! The hard part is done, and now the new repos are available for your package manager.
## Last but not least
Update your repos and packages:
```
sudo pacman -Syyu
```
This command should show also the new package database files (that you added) including the corresponding \<database\>.sig file.
<br><br>
In case of any error, please check that you have copied the repo definitions exactly as they are above. And check that the imported gpg key was correct.<br>
You can see what gpg keys you have installed with:
```
gpg --list-keys --keyid-format LONG
```
And don't forget to enjoy!

