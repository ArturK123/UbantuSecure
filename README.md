# Securing Ubuntu


## Basic
```
sudo apt-get update
sudo apt upgrade
```

## Update FireFox Ubuntu
```
sudo apt install firefox
```
## Install, update, and uninstall Firefox from Mozilla PPA repository
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
