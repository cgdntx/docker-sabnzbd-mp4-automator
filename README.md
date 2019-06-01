## Forked from aront/radarr and adapted for SABnzbd
A docker container based on linuxserver/sabnzbd with sickbeard mp4 automator prerequisites baked in

### Modified from original
* Removed GID / UID from original assuming 911 from linuxserver sonarr/radarr
* Changed volumes and ports to reflect SABnzbd
* Changed automator path
* Removed auto-download / symlinks for sickbeard mp4 automator in favor of manual load

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
````

### Parameters
See [https://hub.docker.com/r/linuxserver/sabnzbd/](https://hub.docker.com/r/linuxserver/sabnzbd/) for details.

### Configuration
Download code from https://github.com/mdhiggins/sickbeard_mp4_automator to persistent mount directory for 'mp4_automator'.  
Run 'chmod +x -R <mp4_automator persistent volume on host>'
Point scripts in SABnzbd general to /mp4_automator.  
Configure according to https://github.com/mdhiggins/sickbeard_mp4_automator#sabnzbd-setup


