# Create Network Connection Profile

Creating a network connection profile was essential in connecting my homelab server (Thinkpad T480) running Arch Linux to my router. The following steps are needed to achieve this:

1. Identify `DEVICE` (in this case, the router) to connect to.
```
nmcli device
```

2. Create the connection profile.
```
nmcli connection add type wifi ifname <DEVICE> con-name <name> ssid "SSID"
```
Replace `DEVICE` with the device identified at step 1, `name` with any chosen name (this is to identify the connection), and `SSID` with the SSID of the network you wish to connect to. You may see the following output once the connection has been successfully created: `Connection '<name>' successfully added`.

3. Set key management method.
```
nmcli connection modify <name> wifi-sec.key-mgmt wpa-psk
``` 

4. Add network passsword (replace `password` with the true network password).
```
nmcli connection modify <name> wifi-sec.psk "<password>"
```

5. Bring the connection up.
```
nmcli connection up <name>
```
Following output should show on successful activation: `Connection successfully activated`.
