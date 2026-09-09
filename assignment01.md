# Assignment 01

* Author: B24080525 Chenxi Duan
* Environment: Windows 11 (amd64)
* Assisted by: ChatGPT

1. Install WSL (Windows Subsystem of Linux) with WinGet
```PowerShell
winget install -e --id Microsoft.WSL
```

2. Install Debian in WSL
```PowerShell
wsl --install -d Debian
```

3. Follow the instrction to create a local account

4. Set up proxy for Debian

First, change WSL's networking mode to 'mirrored' mode.
Direct to `%USERPROFILE%`, open `.wslconfig` with Notepad.
Insert the following entry into the config file.
```
[wsl2]
networkingMode=mirrored
```

Then, restart Debian and switch to super user.
Open `~/.bashrc` with vim, and insert the following commands.
```bash
export http_proxy="http://127.0.0.1:7897"
export https_proxy="$http_proxy"

export HTTP_PR0XY="$http_proxy"
export HTTPS_PR0XY="$https_proxy"

export no_proxy="localhost,127.0.0.1,::1"
export NO_PROXY="$no_proxy"
```

Where `7897` is the listening port of Clash Verge in Windows.

Save and quit vim and run the following command.
```bash
source ~/.bashrc
```

5. Install openssh

Since I choose WSL instead of VMware, I can start Debian directly from Windows Terminal, so openssh is not necessary.
But I still install it with following command.
```bash
sudo apt install openssh-server
```

Enter `Y` to confirm installation.

6. Set up assignment workspace

Follow the instructions @20140104王磊老师/github-作业提交.pdf , configure git.
Then clone repo and set up the workspace with following commands.
```bash
mkdir assignments
cd assignments
git clone https://github.com/Royat07/linux2026.git
cd linux2026
git checkout -b submission/B24080525-Chenxi-Duan
mkdir B24080525-Chenxi-Duan
```

7. Write this file

In Windows, open VSCode and connect to WSL: Debian (use hotkey: `Ctrl`+`Shift`+`P`).
Create and write this file.
Stage all, commit, and push to remote.