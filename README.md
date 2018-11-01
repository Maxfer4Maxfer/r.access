# R.Access

R.Access is an light and open source tool which allowes you keep terminal access to all of your devices placed behind firewalls, proxy and NAT.

R.Access is based on two open source projects [kmate](https://kmate.io) and [Dropbox-Uploader](https://github.com/andreafabrizi/Dropbox-Uploader).

* **Up and runnging:**  you never loose your  connection even after rebooting a remote device.

* **Access from anywhere at anytime:**  be in touch with your devices wherever you are. No need to set up VPN, Port Forwarding or have public IPs.

**Why it is called "R.Access"**

Firstly I was lookign for a convinient and free solution to access my home rassberry pi. That why "R". Now I put R.Access in my swiss army knife and use it everywhare where is no other way to reach remote servers e.g. servers behind firewalls or NAT without public IP or restriction for port forwarding. R becomes for Remote.


## Getting started

1. Remote machine

  Install and setup [Dropbox-Uploader](https://github.com/andreafabrizi/Dropbox-Uploader) as described  [here](https://www.andreafabrizi.it/2016/01/01/Dropbox-Uploader/).

  Or simply do

  ```bash
    sudo mv dropbox_uploader.sh /usr/local/sbin
    sudo chmod +x /usr/local/sbin/dropbox_uploader.sh
  ```

  Change initials variables specific for you installation
  ```bash
    NAME='hostname'                  #indentificator of your host
    OUTPUT_FILE="/tmp/tmate.url"     #file where connection string is stored
    DROPBOX_UPLOADER="/usr/local/sbin/dropbox_uploader.sh"
  ```

  Copy raccessd to /usr/local/sbin and set a right execution permission
  ```bash
    sudo mv raccessd /usr/local/sbin
    sudo chmod +x /usr/local/sbin/raccessd
  ```

  Add pereodical check you crontab
  ```bash
    crontab -e
      */5 * * * *  /usr/local/sbin/raccessd monitor
  ```
  Make shure that after manually ranning "/usr/local/sbin/raccessd monitor" you get tmate.url.<hostmane> file in you Dropbox App's directory.

2. Local machine

  Set up your Dropbox App's directory
  ```bash
    APP_DIR="$HOME/Dropbox/Apps/tmate.url"
  ```

  Copy raccess to /usr/local/sbin and set right execution permissions
  ```bash
    sudo vi /usr/local/sbin/raccess
    sudo chmod +x /usr/local/sbin/raccess
  ```

## Usage

  List all availabel remote tmate session
  ```bash
    raccess list
  ```
  Connect to a session
  ```bash
    raccess <session name>
  ```

## Donations

 If you want to support this project, please consider donating:
 * PayPal: https://paypal.me/MaxFe
