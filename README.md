![PiJARR](/pijarr.png)

[![GitHub Repo stars](https://img.shields.io/github/stars/pijarr/pijarr)](https://github.com/pijarr/pijarr/stargazers)
[![GitHub Repo issues](https://img.shields.io/github/issues/pijarr/pijarr)](https://github.com/pijarr/pijarr/issues)

# PiJARR

PiJARR is a shell script designed to simplify the installation and configuration of a suite of media management tools on Debian-based distributions. This script is compatible with various systems, including Debian 11 (bullseye), Debian 12 (bookworm), Raspberry Pi OS, Ubuntu, Pop!\_OS, Kali Linux, and more. It supports both ARM (Raspberry Pi) and Intel/AMD **x64** architectures.

### WHAT ARR THEY?

PiJARR streamlines the deployment of the following applications:

- [**Jackett**](https://github.com/Jackett/Jackett): Integrates your favorite torrent trackers with a unified API.
- [**Sonarr**](https://github.com/Sonarr/Sonarr): Acts as an Internet PVR for Usenet and BitTorrent, automating TV show downloads.
- [**Radarr**](https://github.com/Radarr/Radarr): Manages movie collections for Usenet and BitTorrent users.
- [**Lidarr**](https://github.com/Lidarr/Lidarr): Organizes music collections from Usenet and BitTorrent sources.
- [**Readarr**](https://github.com/Readarr/Readarr): Manages ebook collections, catering to both Usenet and BitTorrent users.
- [**Prowlarr**](https://github.com/Prowlarr/Prowlarr): Serves as an indexer manager/proxy, integrating with applications like Sonarr, Radarr, Lidarr, and Readarr.
- [**Bazarr**](https://github.com/morpheus65535/bazarr): Enhances Sonarr and Radarr by managing and downloading subtitles.
- [**FlareSolverr**](https://github.com/FlareSolverr/FlareSolverr): A proxy server to bypass Cloudflare and DDoS-GUARD protection, enabling access to protected torrent sites.

### LATEST UPDATE

- [x] **FlareSolverr Integration**: Added FlareSolverr to bypass Cloudflare protection on torrent indexers. Runs in Python 3.13 virtual environment with Xvfb for headless browser operation.
- [x] **qBittorrent Password Management**: Automatically configures qBittorrent with a secure default password (`admin`/`pijarr`) instead of relying on random temporary passwords. Fixes login issues with qBittorrent 4.6.1+.
- [x] Added support for Sonarr v4.
- [x] Integrated an installation option for qBittorrent-nox, a headless torrent client, defaulting to port 8080.
- [x] Expanded functionality to include Bazarr installation.
- [x] Enhanced script with code cleanup and improved validation.

### TEST ENVIRONMENTS

PiJARR has been tested in the following setups:

```terminal
System OS.........: Debian GNU/Linux 13 (trixie)
System Kernel.....: 6.12.57-amd64
System Arch.......: x86_64
System Proc.......: Intel(R) Core(TM) i7
```

```terminal
System OS.........: Debian GNU/Linux 12 (bookworm)
System Kernel.....: 6.1.0-rpi7-rpi-v8
System Arch.......: aarch64
System Proc.......: Raspberry Pi 4
```

#### Raspberry Pi testing version  

[raspberrypi.com/software/operating-systems/](https://www.raspberrypi.com/software/operating-systems/)
```terminal
Raspberry Pi OS Lite
Release date: December 11th 2023
System: 64-bit
Kernel version: 6.1
Debian version: 12 (bookworm)
```

### NOTES

- **Testing Environment**: The script has been primarily tested on clean, vanilla Debian installations. While it should work on other Debian-based OSes, minor adjustments might be needed. Please note that due to changes in package sources, occasional breaks can occur. This project is updated in my spare time and is not actively monitored or maintained.

- **Desktop Environment**: No desktop environment like GNOME or KDE is required. The script is designed to run headless on a minimal Debian installation with basic system tools.

- **Hardware Recommendations**: The script is compatible with Raspberry Pi 3, but installation and performance may be slow. For optimal performance, a Raspberry Pi 4, other x64 hardware, or a virtual machine is recommended.

- **Installation Notes**: Larger dependencies, such as Mono, may appear to stall or hang during installation, especially on slower hardware like Raspberry Pi 3. However, they will eventually complete.

- **Bazarr Dependencies**: Bazarr requires additional Python packages. It will be configured to run in a Python virtual environment (venv) to avoid dependency conflicts.

- **FlareSolverr Dependencies**: FlareSolverr requires Python 3.13 and Chrome/Chromium browser. It will be configured to run in a Python virtual environment (venv) with Xvfb for headless browser operation. Python 3.13 is installed via the deadsnakes PPA.

- **qBittorrent Default Password**: The script now automatically configures qBittorrent-nox with default credentials (`admin`/`pijarr`) to resolve login issues with qBittorrent 4.6.1+. **IMPORTANT**: Change this password immediately after your first login for security. You can change the password in the WebUI under Tools → Options → Web UI.

- **Application Removal**: The removal script will delete everything in `/var/lib/{appname}` and `/opt/{appname}`. Please note that the removal process only works if the application was originally installed using the PiJARR script.

- **Headless Torrent Client**: The menu now includes [qbittorrent-nox](https://github.com/qbittorrent/qBittorrent) (headless BitTorrent client). This client is suitable for machines without a graphical desktop environment. For those who need a desktop GUI torrent client, you can install them using the `apt` command as shown below:
  
```terminal
# qBittorrent desktop GUI torrent client
sudo apt install qbittorrent
```

```terminal
# transmission desktop GUI torrent client
sudo apt install transmission
```

### EXAMPLE - MENU OPTIONS

Below is an example of the menu options presented by the PiJARR script:

```terminal

    ▓▓▓▓▓▓▓▓▓▓▓▓ ▓▓▓▓         ▓▓▓▓ ▓▓▓▓▓▓▓▓▓▓▓▓ ▓▓▓▓▓▓▓▓▓▓▓▓ ▓▓▓▓▓▓▓▓▓▓▓▓
    ▓▓▓▓    ▓▓▓▓              ▓▓▓▓ ▓▓▓▓    ▓▓▓▓ ▓▓▓▓    ▓▓▓▓ ▓▓▓▓    ▓▓▓▓
    ▓▓▓▓▓▓▓▓▓▓▓▓ ▓▓▓▓ ▓▓▓▓    ▓▓▓▓ ▓▓▓▓▓▓▓▓▓▓▓▓ ▓▓▓▓▓▓▓▓▓▓▓▓ ▓▓▓▓▓▓▓▓▓▓▓▓
    ▓▓▓▓         ▓▓▓▓ ▓▓▓▓    ▓▓▓▓ ▓▓▓▓    ▓▓▓▓ ▓▓▓▓  ▓▓▓▓   ▓▓▓▓  ▓▓▓▓
    ▓▓▓▓         ▓▓▓▓ ▓▓▓▓▓▓▓▓▓▓▓▓ ▓▓▓▓    ▓▓▓▓ ▓▓▓▓   ▓▓▓▓▓ ▓▓▓▓   ▓▓▓▓▓

==============
 Menu Options 
==============

1.  Install ALL (jackett sonarr lidarr radarr readarr prowlarr bazarr flaresolverr)
2.  Install jackett only
3.  Install sonarr only
4.  Install lidarr only
5.  Install radarr only
6.  Install readarr only
7.  Install prowlarr only
8.  Install bazarr only
9.  Install flaresolverr only

10. Install qbittorrent-nox (headless BitTorrent client)

11. Remove ALL (jackett sonarr lidarr radarr readarr prowlarr bazarr flaresolverr)
12. Remove jackett only
13. Remove sonarr only
14. Remove lidarr only
15. Remove radarr only
16. Remove readarr only
17. Remove prowlarr only
18. Remove bazarr only
19. Remove flaresolverr only

20. Remove qbittorrent-nox

21. Show active services
22. Show application default ports
23. Show application source urls

24. Exit

```

### DEFAULT APP PORT NUMBERS

Once all applications are installed and the services are started they can be accessed at the following port numbers:

```terminal
Jackett:         http://hostip:9117
Sonarr:          http://hostip:8989
Lidarr:          http://hostip:8686
Radarr:          http://hostip:7878
Readarr:         http://hostip:8787
Prowlarr:        http://hostip:9696
Bazarr:          http://hostip:6767
FlareSolverr:    http://hostip:8191
qBittorrent-nox: http://hostip:8080 (admin/pijarr)
```

**Note**: The qBittorrent-nox default credentials are `admin`/`pijarr`. Remember to change the password after your first login!

### USAGE

#### **Method 1 (Quick easy setup):**

Use the wget or curl command lines shown below for quick setup.

```terminal
sudo sh -c "$(wget -qO- https://raw.githubusercontent.com/pijarr/pijarr/main/setup.sh)"
```

```terminal
sudo sh -c "$(curl -fsSL https://raw.githubusercontent.com/pijarr/pijarr/main/setup.sh)"
```

#### **Method 2:** Clone and run locally

(Optional) This method allows you to edit and customize the script as needed.

```terminal
git clone https://github.com/pijarr/pijarr.git
sudo sh pijarr/setup.sh
```
