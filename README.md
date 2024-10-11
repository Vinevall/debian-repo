# DO NOT USE THIS YET!


# Debian 13 Repository
A Debian 13 (trixie) repository for the Hyprland ecosystem and my commonly used audio and video applications.
Nautilus-hyprland is a simple python script that gives a hyprland menu to nautilus.

## Packages build for Debian 13
| Package | Version | Architecture |
| ----------- | ----------- |----------- |
| Hyprland | 0.44.1-4 | amd64 |
| SendMIDI | 1.3.1-1| amd64 |
| Wallust | 3.0.0-2 | amd64 |
| hyprwayland-scanner | 0.4.2-1 | amd64 |
| libaquamarine | 0.4.2-2 | amd64 |
| libhyprlang2 | 0.5.3-1 | amd64 |
| libhyprutils1 | 0.2.3-1 | amd64 |

## Todo
- [ ] i386 support
- [ ] arm64 support
- [ ] Carla
- [ ] Glow
- [ ] Grimblast
- [x] Hyprland
- [ ] Hyprlock
- [ ] hyprsunset
- [x] hyprwayland-scanner
- [x] libaquamarine
- [x] libaquamarine-dev
- [x] libhyprlang2
- [x] libhyprlang-dev
- [x] libhyprutils1
- [x] libhyprutils-dev
- [ ] nautilus-hyprland
- [ ] OBS-Studio
- [x] SendMIDI
- [ ] ShowMIDI
- [ ] Starship
- [x] Wallust
- [ ] xdg-desktop-portal-hyprland

## Disclaimer
If you don't copy the repository outside your home directory to, for example, the /opt directory, you will get a warning notice.
This is not an error. The "Notice:" at the beginning says that this is just a notice. There is nothing to fix, (almost) everything worked as expected.

Even when apt is run as root, it tries to download and read packages as a separate user _apt. It does that to increase security. To download packages, it has to interact with a potentially malicious server and it has to download and process data from that server. Such situations are one of the main cases in which there are vulnerabilities. So if there was a vulnerability in that part of apt's code, and if apt was running that code as root, the attacker could potentially run code on your system as root, i.e. they would have full control over your system. So apt runs this code as a user that's very restricted in what it is allowed to do.

## Usage

### Alternative 1
To use this repository on your Debian 13 installation, open your favourite terminal and begin installation with de-armouring the gpg-key for the apt repository:

```bash
wget -qO - https://raw.githubusercontent.com/Vinevall/debian-repo/refs/heads/main/debian-trixie-repo.gpg.key | sudo gpg --dearmor -o /etc/apt/keyrings/debian-trixie-repo.gpg
```

Change to the opt directory:
```bash
cd /opt
```

Clone the git repository as root to the opt directory:
```bash 
sudo git clone https://github.com/Vinevall/debian-repo.git
```

Create a list file in the source.list.d directory:
```bash 
echo "deb [arch=amd64 signed-by=/etc/apt/keyrings/debian-trixie-repo.gpg] file:/opt/debian-repo/apt/debian trixie main" | sudo tee /etc/apt/sources.list.d/trixi-hyprland_and_media.list > /dev/null
```

Update the apt database:
```bash
sudo apt update
```

Install package as usual.

### Alternative 2
To use this on your Debian 13 installation, open your favourite terminal and type:

```bash 
git clone https://github.com/Vinevall/debian-repo.git
```

Create debian-repo directory:

```bash
sudo mkdir -p /opt/debian-repo
```

Change into the copied repo directory:

```bash
$ cd /opt/debian-repo
```

Copy the repo to the /opt/debian-repo directory:

```bash
sudo cp -r <path_to_git_repo>/apt/debian .
```

Dearmor the gpg-key for apt:

```bash
cat <path_to_git_repo>/debian-trixie-repo.gpg.key | sudo gpg --dearmor -o /opt/debian-repo/debian-trixie-repo.gpg
```

Add the list file to apt:

```bash 
echo "deb [arch=amd64 signed-by=/opt/debian-repo/debian-trixie-repo.gpg] file:/opt/debian-repo/debian trixie main" | sudo tee /etc/apt/sources.list.d/trixi-hyprland_and_media.list > /dev/null
```

Update the repository:

`$ sudo apt update`

Install package of your choise:

`$ sudo apt install hyprland`
