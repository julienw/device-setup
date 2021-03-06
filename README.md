# device-setup

To setup an Abigail device for the first time, clone the `abigail-device`, `wifi-setup`, and `user-setup` repositories and execute the setup scripts. Use the following commands:

```
sudo apt-get install -y git
git clone https://github.com/project-abigail/abigail-device
git clone https://github.com/project-abigail/wifi-setup
./abigail-device/bootstrap-scripts/raspberry-pi-setup.sh
./wifi-setup/setup-scripts/raspberry-pi-setup.sh
cd abigail-device; npm install; cd ..
cd wifi-setup; npm install; cd ..
```

Note: these scripts take approximately 1.5 hours to execute.

When the scripts are finished executing, run the following command:
```
sudo raspi-config
```
and choose 'Advanced Options' and then 'I2C' and then 'Yes' to enable the ARM I2C interface.

Then, reboot the device. After rebooting:

 * From a laptop, monitor available networks and connect to `Abigail wifi setup` when it appears in the list
 * Run the user-setup script to create users and the family group
   * `node user-setup/index.js` 
 * Copy the file containing the device web token to the device:
   * `scp user-setup/secret.json pi@raspberrypi.local:~/abigail-device`
 * Visit 10.0.0.1 in the browser to connect the device to wifi
 * Reboot the device

When the device starts up, you should hear the "hello" greeting.


