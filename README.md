# vpn

We will use our loved Raspbery Pi to create a VPN to our home network.

## 1.- Setting a Dynamic DNS Server using afraid.org

Create a Free Account, add a Subdomain.

  Type: A \
  Subdomain: yoursubdomainname \
  Domain: Choose your favourite one \
  Destination: 0.0.0.0 \
  
Click on Save \


## 2.- Install ddclient on your Raspberry Pi

```
sudo apt install ddclient
```

Press Enter until the installation is completed.
Edit the ddclient.conf
```
sudo nano /etc/ddclient.conf
```
Edit ddclient
```
sudo nano /etc/default/ddclient
```

Restart ddclient
```
sudo systemctl restart ddclient
```

Check on afraid.org if your subdomain changed from 0.0.0.0 to your Public IP address or use the below command
```
sudo systemctl status ddclient
```

Meke sure systemctl boots with your Raspberry Pi
```
sudo systemctl enable ddclient
```

## 3.- Port Forwarding on your RTR

Devide: Raspberry Pi
Protocol: UDP
Aplication: Other/Wireguard
Port: 51820
IPV4&IPV6

## 4.- Installing Wireguard VPN

```
sudo wget https://git.io/wireguard -O wireguard-install.sh && sudo bash wireguard-install.sh
```

hostname: Your Dinamyc DNS host created earlier
port: 51820
Client Name: Choose your favourite
DNS: Your favourite

## 5.- Connecting to your VPN

Mobile Phone:
  Download the Wireguard app and scan the QR Code

Computer: Copy the configuration files to your computer
  Create a Wireguard folder on your computer and copy the following files from your raspberry pi
  ```
sudo su
cp /root/*.conf /home/pi
```
From the powershell start a sftp session on your new Wireguard folder
```
get *.conf
```
Download Wireguard for Windows and import the configuration file


