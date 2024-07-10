# raspberrypi-vpn-server
This repository will help to setup a raspberry pi as a VPN server to access your home network wirelessly from anywhrere in the world.

- To setup the Raspberry Pi, refere to [this](https://github.com/sashanknjs/raspberrypi-setup) page.

Before beginning to install the VPN server on the Raspberry Pi, a couple of important things to note.

1) Ensure that your Internet Service Provider does not use **CGNAT**. Carrier-Grade NAT (CGNAT) is a technology used by Internet Service Providers (ISPs) to manage the limited number of IP addresses available. When you connect to the internet, your device gets a private IP address. The CGNAT system at the ISP then translates this private address into a shared public address. This allows multiple devices to use the same public IP, conserving the number of addresses needed. In case your ISP uses CGNAT, then the VPN server **would not work** in your case.

To check whether your ISP is utilizing CGNAT,
- Open up a web browser of your choice and enter the router's IP address in place of a URL and hit enter.
- On the router login page, enter your user credentials.
- Once you have access to the user dashboard, you must locate the WAN IP address. Check the IP address the router’s internet WAN interface is receiving.
- If this WAN IP lies in the range of 100.64.x.1 to 100.127.x.254, it could mean that you are behind CGNAT.
- Another way to confirm is to compare the WAN IP with the Public IP address. To find your public IP address, you can use this [link](https://whatismyipaddress.com/).
- If they do not match, it could also mean that you are behind CGNAT.

2) Ensure that your router supports **port forwarding**. This is crucial for the process since the vpn server only works by port forwarding method.

- To check for this, once again login to your router using the router IP address in the browser.
- Once you are logged in, check for a tab named Port forwarding or port mapping. If no such option is available, it may be possible that your router may not support port forwarding.
- To confirm, check on the internet if your particular model supports port forwarding.

With these two things out of the way, let's begin the installation process.

**VPN Server Installation:**

To begin the installation, Open a terminal and run the following commands

```
sudo apt update && sudo apt upgrade
```
```
sudo apt install curl
```
```
curl -L https://install.pivpn.io | bash
```

Once the installation begins, an installation screen appears. 

![image](https://github.com/sashanknjs/raspberrypi-vpn-server/assets/168824530/52b2c300-a050-4e8d-884a-1fc65f56f91c)

- Press **ENTER** to continue. The next screen asks you to set a static ip address

![image](https://github.com/sashanknjs/raspberrypi-vpn-server/assets/168824530/7c1cdb15-c528-4eb0-874c-dc600b077a82)

- Once again press **ENTER**. Now, You will now be asked if you are using a DHCP reservation on your router.

![image](https://github.com/sashanknjs/raspberrypi-vpn-server/assets/168824530/6f68ff43-5f32-47de-afab-209761ca195a)

- If you don’t know what DHCP reservation is or how to use it, do not worry, just select **No** to continue. Note: To highlight the 'No' option, press the '**Tab**' key and when '**No**' is highlighted, press **Enter**.

- Next, it asks whether you want to use the current IP address as the static IP address. If you are happy press **ENTER** to continue.

![image](https://github.com/sashanknjs/raspberrypi-vpn-server/assets/168824530/a0d21b8d-0856-44d4-9c89-70685e4f0562)

- The next screen warns you that there is a chance your router will assign the IP address to another device. You can use DHCP reservations to avoid this. However, most routers are smart enough to prevent the problem. Press Enter to proceed to the next step.

![image](https://github.com/sashanknjs/raspberrypi-vpn-server/assets/168824530/10cadcf7-fbcf-4298-8251-f386bedd60e1)

- This screen will tell you that you need to specify a local user to store the WireGuard configuration files. Continue to the next screen by pressing the ENTER key.

![image](https://github.com/sashanknjs/raspberrypi-vpn-server/assets/168824530/defed6bb-607f-4a57-ac25-9be56cc92484)

- Usually, there is only one user which is automatically selected. I case you have more than 1, select the user by pressing **TAB** to move to the next user followed by **SPACEBAR** to select the user and press the **ENTER** key.

![image](https://github.com/sashanknjs/raspberrypi-vpn-server/assets/168824530/e12d49e5-6db0-4a94-9ab3-4cd29af93708)

- Now, there are two options presented for us to choose. OpenVPN and Wireguard. These are two different protocols on which your VPN server would work. Wireguard is comparitively newer, faster and more seccure compared to OpenVPN. Therefore, the Wireguard option is recommended. Wireguard is seleccted by default so just press **ENTER**.

![image](https://github.com/sashanknjs/raspberrypi-vpn-server/assets/168824530/67feb92e-14f4-41fc-8597-3750c79aa459)

- Next, the default wireguard port is displayed and you can modify it if you wish. However, it is recommended to be kept the same. Just press **ENTER** to continue.

![image](https://github.com/sashanknjs/raspberrypi-vpn-server/assets/168824530/20b9fac2-b83e-4c5f-b3d5-f36c2a3ad7c8)

- Next screen asks to confirm the port number. Press **ENTER** to continue.

![image](https://github.com/sashanknjs/raspberrypi-vpn-server/assets/168824530/96059177-4dc7-45d6-90f4-5e6986f7f2af)

- In the next screen, you are aksed to select a DNS provider from a list of options. You can select any one of these. To select the one option, press **TAB** to move to the next and once you reach the desired option, press **SPACEBAR** to select the option and press the **ENTER** key. The recommended DNS provider is Cloudfare as it is relatively speedy, and they purge their logs every 24 hours.

![image](https://github.com/sashanknjs/raspberrypi-vpn-server/assets/168824530/8ccd9ad8-fdf1-4658-9384-7a50e7322a15)

- For the next step, you are asked to select either the Public IP address or a DNS entry to access your Wireguard VPN. In this tutorial, let us proceed with Public IP address. Press **ENTER**.

![image](https://github.com/sashanknjs/raspberrypi-vpn-server/assets/168824530/fc76f1ca-6399-413d-8f87-4153e126e8ee)

- Now the server keys will be genereated. Press ENTER to continue.

- Next, you will be informed about installing unattended upgrades, just continue to the next screen.

![image](https://github.com/sashanknjs/raspberrypi-vpn-server/assets/168824530/5bc8e926-b951-42f4-83be-88aee41e4d13)

- Next, you will be asked to confim installing unattended upgrades, just continue to the next screen.

![image](https://github.com/sashanknjs/raspberrypi-vpn-server/assets/168824530/b2861e21-8396-43a6-b571-82181a0f65d4)

- You have successfully installed Pivpn.

![image](https://github.com/sashanknjs/raspberrypi-vpn-server/assets/168824530/8314abf0-bc26-46fd-9060-4d8c68c96869)

- You will now be asked to reboot the system. Press ENTER and your system will be rebooted.

**Configuring the Port Forwarding on your router**

Before using the VPN server, you need to create a Port Forwarding rule on your router. This is the most crucial step. If this is not done, even though you connect to the VPn, you would not be able to access the internet. 

- To create a port forwarding rule, open a browser on your PC and type the router IP address and login using the credentials. Once the interface appears, look for the port forwarding option and select it. It may be at different locations for different routers.
- Next, click on the **ADD** a new rule/mapping.
- Most of the routers ask for the following details which can be filled as follows:
  - **Name**: Wireguard
  - **Protocol**: UDP
  - port number: 51820
  - Destination IP address: ip adress of your Raspberry Pi
- Any other fields can be left blank. But the specified fields have to be filled exactly as mentioned.
- Save the rule. You have successfully cconfigured the port forwarding on your router.

**Setting up the VPN server**
- Once the system is rebooted, open a terminal and type the following command:
```
sudo pivpn add
```
- This will prompt you to add a new profile for the VPN. You will be asked to enter a name for the profile. Enter a name and press **ENTER**.

- The profile is created successffully.

**Connecting to the VPN from Mobile devices**

- To connect to the VPN on our mobile devices, you can install the Wireguard application from Google Play store or Apple App Store. 
- On your Raspberry Pi, open a terminal and type:
  ```
  pivpn -qr PROFILENAME
  ```
- replace PROFILENAME with the name created in the step above. This will generate a qr code.
- Open your Wireguard mobile application and select the QR code scanner and scan the QR code. It will prompt you to enter the profile name. Enter the profile name and it will automatically connect to the VPN. You can then toggle the VPN ON or OFF whenever you do or do not want to use the VPN.

**Connecting to the VPN from PC**

- On your Raspberry Pi, you will find the configuration file for the profile you created from the following directory:
```
/home/pi/config
```
- Replace 'pi' with your username in case it is different. The name of the file would be PROFILENAME.conf (the PROFILENAME would be the name of the profile you created). You need to copy the file and send it to your PC. You can do it using multiple ways for example using WinSCP. Different methods for sharing files is discussed here in more detail.
- To connect to the VPN from your PC, download and install the Wireguard client from [here](https://www.wireguard.com/install/).
- Open the Wireguard client and click on Add Tunnel on the bottom left of the screen

![image](https://github.com/sashanknjs/raspberrypi-vpn-server/assets/168824530/00d2e1af-dc6c-4885-b131-b934b19b3957)

- Select the configuration file you just copied. This automatically adds the profile. To connect to the vpn, select the profile on the left and click on 'Activate'. This activates the VPN.

Congratulations!!! Tou have successfully setup the Raspberry Pi as a VPN server.
