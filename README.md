## Forked from aront/radarr and adapted for SABnzbd
A docker container based on linuxserver/sabnzbd with mp4 automation baked in

### Modified from original
* Removed GID / UID from original assuming 911 from linuxserver sonarr/radarr
* Changed volumes and ports to reflect SABnzbd
* Changed automator path

### Usage

````
docker create \
    --name sabnzbd \
    --restart unless-stopped \
    -p 8080:8080 \
    -e TZ="America/Chicago"  \
    -v <path to data>:/config \
    -v <path to data>:/mp4_automator \
    -v <path to data>:/incomplete-downloads \
    -v <path to data>:/downloads \
    cgdntx/sabnzbd
    
mkdir <path to data>/mp4_automator && \
wget https://raw.githubusercontent.com/mdhiggins/sickbeard_mp4_automator/master/autoProcess.ini.sample -O <path to data>/mp4_automator/autoProcess.ini
````

### Parameters
See [https://hub.docker.com/r/linuxserver/sabnzbd/](https://hub.docker.com/r/linuxserver/sabnzbd/) for details.

### mkdir
Makes a symlink from sickbeard_mp4_automator to a config directory that is a volume for the container. If the host has a config file (autoProcess.ini) in the mounted volume, then sickbeard_mp4_automator will be able to use that. This is useful if you are running multiple containers but want to share the mp4 automation configuration between them. It also has the benefit of being able to modify the config from the host OS.
