# Securing Ubuntu


## Basic
```
sudo apt-get update && sudo apt upgrade && sudo apt dist-upgrade
```

## Change Update Config

Navigate to Aplications < Software & Updates < Updates

![this is an image](https://raw.githubusercontent.com/ArturK123/UbantuSecure/main/Screen%20Shot%202021-12-09%20at%205.52.08%20PM.png)

## Auto Update
use man dpkg-reconfigure for more, or visit [this](https://askubuntu.com/questions/590898/what-is-dpkg-reconfigure-and-how-is-it-different-from-dpkg-configure) link
```
sudo apt install unattended-upgrades
sudo dpkg-reconfigure --priority=low unattended-upgrades
```

## Update FireFox

### Option 1
```
firefox --version
sudo apt install firefox
```
### Option 2
For more info visit [this](https://linuxconfig.org/how-to-install-uninstall-and-update-firefox-on-ubuntu-20-04-focal-fossa-linux) website

First, we need to add the Mozilla signing key to our system:
```
sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys A6DCF7707EBC211F
```

Next, add Mozilla’s PPA repository and update the list of available packages in apt:
```
sudo apt-add-repository "deb http://ppa.launchpad.net/ubuntu-mozilla-security/ppa/ubuntu focal main"
sudo apt update
```

Finally, if all went well up till now, install the latest version of Firefox with this command:
```
sudo apt install firefox
```



## Install AnitVirus

For more info visit [this](https://www.unixmen.com/installing-scanning-clamav-ubuntu-14-04-linux/) website
```
sudo apt-get install clamav clamav-daemon
sudo freshclam
clamscan -r /
```
## List Open Ports

search before removing
```
sudo ss -tupln
```

## Configure UFW

Do this after updating everything ufw probably blocks FireFoxes Port
```
sudo apt install ufw
sudo ufw status
sudo ufw enable
```

## Block Pings
```
sudo nano /etc/ufw/before.rules
```

![this is an image](https://raw.githubusercontent.com/ArturK123/UbantuSecure/main/Screen%20Shot%202021-12-09%20at%205.27.19%20PM.png)

Add the folowing line to the spot on the image

```
-A ufw-before-input -p icmp --icmp-type echo-request -j DROP
```

Restart UFW

```
sudo ufw reload
```

## Pam Files

### Step 1

install pam
```
cd ../.. && cd /etc/pam.d/ && sudo apt install libpam-cracklib
sudo nano common-password
```
### Step 3

add `remember=5` to end of pam_unix.so

add `ucredit=-1 lcredit=-1 dcredit=-1 ocredit=-1` to pam_cracklib.so

### Step 4

```
sudo nano ../login.defs
```

Change `PASS_MAX_DAYS 90`

Change `PASS_MIN_DAYS 10`

Change `PASS_WARN_AGE 7`

### Step 5
```
sudo nano common-auth
```

Add `auth required pam_tally2.so deny=5 onerr=fail unlock_time=1800` at the end of the file

## Find Hiden Files
look through all /home/users
```
ls -la
```



# Errors

## Unable to acquire the dpkg frontend lock
if solution 1 isn't working visit [this](https://www.linuxfordevices.com/tutorials/ubuntu/fix-unable-to-acquire-the-dpkg-frontend-lock) webiste

### Solution 1
```
ps aux | grep -i apt
sudo kill <process_id>
```

## initialize: libfreshclam init failed
Visit [this](https://askubuntu.com/questions/1292583/clamav-freshclam-did-not-working) link for more details
```
sudo systemctl stop clamav-freshclam.service
```
