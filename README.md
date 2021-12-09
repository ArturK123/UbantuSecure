# Securing Ubuntu


## Basic
```
sudo apt-get update
```

## Install AnitVirus
```
sudo apt-get install clamav clamav-daemon
sudo freshclam
clamscan -r /
```


# Errors

## Unable to acquire the dpkg frontend lock
if solution 1 isn't working visit https://www.linuxfordevices.com/tutorials/ubuntu/fix-unable-to-acquire-the-dpkg-frontend-lock

### Solution 1
```
ps aux | grep -i apt
sudo kill <process_id>
```

## initialize: libfreshclam init failed
Visit [this](https://askubuntu.com/questions/1292583/clamav-freshclam-did-not-working) link for more details
