# Debian 13 Repository
A local Debian 13 (trixie) repository for hyprland, bla, bla, bla and my commonly used audio and video applications


## Disclamber
If you don't copy the repo outside your home-directory to the /opt direcory, you will get a warning notice.
This is not an error. The "Notice:" at the beginning says that this is just a notice. There is nothing to fix, (almost) everything worked as expected.

Even when apt is run as root, it tries to download and read packages as a separate user _apt. It does that to increase security. To download packages, it has to interact with a potentially malicious server and it has to download and process data from that server. Such situations are one of the main cases in which there are vulnerabilities. So if there was a vulnerability in that part of apt's code, and if apt was running that code as root, the attacker could potentially run code on your system as root, i.e. they would have full control over your system. So apt runs this code as a user that's very restricted in what it is allowed to do.

Apt also tries to do that when it fetches package files not from a remote server but from somewhere in the local filesystem. In your case, it tried to use the _apt user to access /home/bestuser/Downloads/discord-0.0.17.deb. But that fails, because the _apt user isn't allowed to access your home directory. So apt instead accesss that file as root and it informs you about that.

In this situation (fetchting the package file locally) there's no security advantage in using the _apt user, so using root isn't problematic. 

## Packages build for Debian 13
- wallust

## Usage
To use this on your Debian 13 installation, open your favourite terminal and type:

`$ git clone https://github.com/Vinevall/debian-repo.git`


Create debian-repo directory:

`$ sudo mkdir -p /opt/debian-repo`


Change into the copied repo directory:

`$ cd /opt/debian-repo`


Copy the repo to the /opt/debian-repo directory:

`$ sudo cp -r <path_to_git_repo>/apt/debian .`


Dearmor the gpg-key for apt:

`$ cat <path_to_git_repo>/debian-trixie-repo.gpg.key | sudo gpg --dearmor -o /opt/debian-repo/debian-trixie-repo.gpg`


Add the list-file to apt:

`$ echo "deb [arch=amd64 signed-by=/opt/debian-repo/debian-trixie-repo.gpg] file:/opt/debian trixie main" | sudo tee /etc/apt/sources.list.d/trixi-hyprland_and_media.list > /dev/null`


