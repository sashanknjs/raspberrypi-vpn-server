# raspberrypi-vpn-server
This repository will help to setup a raspberry pi as a VPN server to access your home internet from anywhere in the world

**Hardware:**
- Raspberry Pi any model works fine but preferably Raspberry Pi 3 or above with atleast 1GB RAM.
- SD Card (8GB or above)
- Power Adapter
- HDMI to HDMI cable (for Rasperry Pi 2,3 and 3B+) or Micro HDMI to HDMI (for Rasperry Pi 4 and 5)
- Ethernet cable
- USB Mouse and Keyboard
- Monitor (Display)

**OS:** Rasperry Pi OS - 32 or 64 bit (Desktop or lite)

**Setup**
- Dowload the [Raspberry Pi Imager](https://www.raspberrypi.com/software/) on your PC. Once installed, connect the SD card to your PC and open the imager.

![image](https://github.com/sashanknjs/raspberrypi-vpn-server/assets/168824530/e4db8c6a-5a05-406c-83e6-2720833afc71)

- Before installing the OS, a few settings such as username and password, Wifi credentials and SSH options can be modified

![image](https://github.com/sashanknjs/raspberrypi-vpn-server/assets/168824530/e9278451-c6b4-411b-aae1-5f8c65a5fa55)

![image](https://github.com/sashanknjs/raspberrypi-vpn-server/assets/168824530/41914cf2-a0d2-46d8-9177-ee1bf1285c78)

- Once the OS in installed on the SD card, eject it from your PC and istall it onto the Raspberry Pi. Also, connect the Raspberry Pi to power and using the HDMI cable, connect it to a display.
- In case you did not enter the WIFI credentials, connecct the Raspberry Pi to your WIFI router using the Ethernet cable.
- Connect the USB Mouse and Keyboard to the Raspberry Pi.

**VPN Server Installation:**

Open a terminal and run the following command

```
curl -L https://install.pivpn.io | bash
```
