# 💡 WLED-Installation auf ESP32 Supermini: Workaround-Anleitung

Falls Probleme bei der direkten Installation von **WLED** auf deinem [ESP32-Supermini](https://s.click.aliexpress.com/e/_c2vLv9IV) über den [offiziellen Web-Installer](https://install.wled.me/) auftreten, bietet diese Anleitung einen stabilen **Workaround** mithilfe von **Tasmota** als Zwischenschritt.

<details>
<summary>🇬🇧 Click here for the English version / Hier klicken für die englische Version</summary>

## 💡 WLED Installation on ESP32 Supermini: Workaround Guide

If you encounter issues installing WLED directly to your [ESP32-Supermini](https://s.click.aliexpress.com/e/_c2vLv9IV) via the [official web installer](https://install.wled.me/), this guide provides a stable workaround using **Tasmota** as an intermediate step.

---

## 🛠️ Step 1: Connect in Bootloader Mode

1. Use a **USB data cable** (not a power-only cable).
2. **Hold down** the **BOOT button** on the ESP32 Supermini.
3. Connect the ESP32 to your PC via USB **while holding** the button.
4. Release the BOOT button.

---

## ⚙️ Step 2: Flash Tasmota

1. Go to **[Tasmota Web Installer](https://tasmota.github.io/install/)**.
2. Install Tasmota using the recommended settings.
3. After the install is successful, **unplug** the ESP32 from your USB connection.

---

## 🌐 Step 3: Connect Tasmota to your Home WiFi

1. Reconnect the USB connection (do not hold the BOOT button this time).
2. Using your PC or phone, connect to the Tasmota Access Point automatically created by the ESP32.
3. A captive portal login page should pop up. Use it to select and connect to your regular Home WiFi network.

---

## 🔍 Step 4: Figure Out Your ESP32's IP

### Option 1: Router Settings
* Check your router's client list to find the IP address assigned to the Tasmota device.

### Option 2: Tasmota Console
1. Open **[Tasmota Web Installer](https://tasmota.github.io/install/)** again.
2. Connect to your ESP32, but this time open the **LOGS & CONSOLE**.
3. If the IP address has not appeared in the log, press **RESET DEVICE** at the bottom right.
4. The ESP32 will reboot and reconnect. You will see the assigned IP address in the logs (e.g., `192.168.2.194`).

---

## 🌈 Step 5: Install WLED

1. Open the IP address (e.g., `http://192.168.2.194`) in your browser to access the Tasmota web interface.
2. Go to **`Tools`** -> **`Console`**.
3. Input the following two commands, pressing **Enter** after each:

    ```
    SetOption78 1
    ```
    ```
    restart 1
    ```

4. Go to **[WLED Releases](https://github.com/wled/WLED/releases/)** and download the correct WLED binary for your specific ESP32 chip (e.g., `WLED_X.X.X_ESP32.bin`).
5. In the Tasmota page, go to **`Firmware Upgrade`**.
6. Click **`Choose File`** and select the WLED binary you downloaded.
7. Press **`Start Upgrade`**.

Once finished, your ESP32 Supermini has successfully been flashed with WLED. The device will disconnect, and a **WLED-AP** (Access Point) will be created. Proceed with the standard WLED setup (connect to the WLED-AP, configure your network, etc.).

</details>

---

## 🛠️ Schritt 1: Im Bootloader-Modus verbinden

1.  Verwende ein **USB-Datenkabel** (kein reines Ladekabel).
2.  **Halte** die **BOOT-Taste** auf dem ESP32 Supermini **gedrückt**.
3.  Verbinde den ESP32 **während des Gedrückthaltens** der Taste per USB mit deinem PC.
4.  Lasse die BOOT-Taste los.

---

## ⚙️ Schritt 2: Tasmota flashen

1.  Gehe zum **[Tasmota Web Installer](https://tasmota.github.io/install/)**.
2.  Installiere Tasmota mit den empfohlenen Einstellungen.
3.  Nach erfolgreicher Installation **trenne** den ESP32 von der USB-Verbindung.

---

## 🌐 Schritt 3: Tasmota mit deinem Heim-WLAN verbinden

1.  Verbinde das USB-Kabel erneut (dieses Mal nicht die BOOT-Taste gedrückt halten).
2.  Verbinde dich mit deinem PC oder Smartphone mit dem **Tasmota Access Point**, der automatisch vom ESP32 erstellt wurde.
3.  Eine Captive-Portal-Anmeldeseite sollte erscheinen. Verwende diese, um dein reguläres Heim-WLAN-Netzwerk auszuwählen und dich damit zu verbinden.

---

## 🔍 Schritt 4: IP-Adresse deines ESP32 herausfinden

### Option 1: Router-Einstellungen
* Überprüfe die Client-Liste deines Routers, um die dem Tasmota-Gerät zugewiesene IP-Adresse zu finden.

### Option 2: Tasmota-Konsole
1.  Öffne den **[Tasmota Web Installer](https://tasmota.github.io/install/)** erneut.
2.  Verbinde dich mit deinem ESP32, öffne jedoch dieses Mal **LOGS & CONSOLE**.
3.  Falls die IP-Adresse nicht im Protokoll angezeigt wurde, drücke unten rechts auf **RESET DEVICE**.
4.  Der ESP32 wird neu starten und sich wieder verbinden. Du siehst die zugewiesene IP-Adresse im Protokoll (z. B. `192.168.2.194`).

---

## 🌈 Schritt 5: WLED installieren

1.  Öffne die IP-Adresse (z. B. `http://192.168.2.194`) in deinem Browser, um auf die Tasmota-Weboberfläche zuzugreifen.
2.  Gehe zu **`Tools`** -> **`Console`**.
3.  Gib die folgenden zwei Befehle ein und drücke nach jedem **Enter**:

    ```
    SetOption78 1
    ```
    ```
    restart 1
    ```

4.  Gehe zu **[WLED Releases](https://github.com/wled/WLED/releases/)** und lade die korrekte WLED-Binärdatei für deinen spezifischen ESP32-Chip herunter (z. B. `WLED_X.X.X_ESP32.bin`).
5.  Gehe in der Tasmota-Seite zu **`Firmware Upgrade`**.
6.  Klicke auf **`Choose File`** und wähle die heruntergeladene WLED-Binärdatei aus.
7.  Drücke auf **`Start Upgrade`**.

Nach Abschluss wurde dein ESP32 Supermini erfolgreich mit WLED geflasht. Das Gerät trennt die Verbindung, und ein **WLED-AP** (Access Point) wird erstellt. Fahre mit der standardmäßigen WLED-Einrichtung fort (Verbindung zum WLED-AP herstellen, dein Netzwerk konfigurieren usw.).
