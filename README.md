# 💡 WLED Installation on ESP32 Supermini: Workaround Guide



If you encounter issues installing WLED directly to your [ESP32-Supermini](https://s.click.aliexpress.com/e/_c2vLv9IV) via the [official web installer](https://install.wled.me/), this guide provides a stable workaround using **Tasmota** as an intermediate step.



## 🛠️ Step 1: Connect in Bootloader Mode



1.  Use a **USB data cable** (not a power-only cable).

2.  **Hold down** the **BOOT button** on the ESP32 Supermini.

3.  Connect the ESP32 to your PC via USB **while holding** the button.

4.  Release the BOOT button.



## ⚙️ Step 2: Flash Tasmota



1.  Go to **[Tasmota Web Installer](https://tasmota.github.io/install/)**.

2.  Install Tasmota using the recommended settings.

3.  After the install is successful, **unplug** the ESP32 from your USB connection.



## 🌐 Step 3: Connect Tasmota to your Home WiFi



1.  Reconnect the USB connection (do not hold the BOOT button this time).

2.  Using your PC or phone, connect to the Tasmota Access Point automatically created by the ESP32.

3.  A captive portal login page should pop up. Use it to select and connect to your regular Home WiFi network.



## 🔍 Step 4: Figure Out Your ESP32's IP



### Option 1: Router Settings

* Check your router's client list to find the IP address assigned to the Tasmota device.



### Option 2: Tasmota Console

1.  Open **[Tasmota Web Installer](https://tasmota.github.io/install/)** again.

2.  Connect to your ESP32, but this time open the **LOGS & CONSOLE**.

3.  If the IP address has not appeared in the log, press **RESET DEVICE** at the bottom right.

4.  The ESP32 will reboot and reconnect. You will see the assigned IP address in the logs (e.g., `192.168.2.194`).



## 🌈 Step 5: Install WLED



1.  Open the IP address (e.g., `http://192.168.2.194`) in your browser to access the Tasmota web interface.

2.  Go to **`Tools`** -> **`Console`**.

3.  Input the following two commands, pressing **Enter** after each:



    ```

    SetOption78 1

    ```

    ```

    restart 1

    ```



4.  Go to **[WLED Releases](https://github.com/wled/WLED/releases/)** and download the correct WLED binary for your specific ESP32 chip (e.g., `WLED_X.X.X_ESP32.bin`).

5.  In the Tasmota page, go to **`Firmware Upgrade`**.

6.  Click **`Choose File`** and select the WLED binary you downloaded.

7.  Press **`Start Upgrade`**.



Once finished, your ESP32 Supermini has successfully been flashed with WLED. The device will disconnect, and a **WLED-AP** (Access Point) will be created. Proceed with the standard WLED setup (connect to the WLED-AP, configure your network, etc.).
