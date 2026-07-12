# 🚀 High-Performance RP2040 MicroPython Build

A custom-compiled MicroPython firmware for the Raspberry Pi Pico designed for high-performance robotics, featuring automatic dual-write crash prevention and built-in hardware reset controls.

## ✨ Key Features

* **Fixed Flash Allocation:** Custom-compiled at a hard 1MB storage boundary to permanently isolate the filesystem.
* **Anti-Corruption Engine:** Completely fixes the critical bug where the Pico panics and wipes/deletes your `main.py` file on reboot.
* **200MHz CPU Overclock:** Boosted clock speeds for lightning-fast motor control loops and hardware processing.
* **Slick Drive Identity:** Configured to mount cleanly as a reliable virtual drive, mimicking the seamless CircuitPython workflow.

---

## 💾 Installation

### Step 1: Flash the Firmware
1. Hold the **BOOTSEL** button on your Pico and plug it into your device.
2. *(Highly Recommended)* Drag and drop the `ERASE-FLASH.uf2` file (available in Releases) onto the **RPI-RP2** volume. Wait for the onboard LED to turn off. If the volume doesn't reappear automatically, unplug it, hold **BOOTSEL**, and plug it back in.
3. Drag and drop the custom `firmware.uf2` file from the latest release onto the **RPI-RP2** volume. 
4. The Pico will automatically reboot and mount as a new virtual drive. *Note: You can rename this drive to whatever you like!*

### Step 2: Configure `boot.py` (Hardware Reset Protection)
To enable the background BOOTSEL reset mechanism without yanking the USB cable:
1. Open the Pico drive, create a new text file, and open it in a text editor (like Notepad).
2. Copy and paste the code from the `boot.py` file found in our Releases. 
3. Click **File -> Save As**, name the file `boot.py`, set the type to **All Files (*.*)**, and save it directly to the root directory of the Pico drive.
4. ⚠️ **Important:** Do not modify the core logic inside `boot.py`, as breaking the hardware timer loop will disable the soft-reset feature!

### Step 3: Verify the Reset Mechanism
1. Unplug the Pico and plug it back in.
2. Press the physics **BOOTSEL** button on the board. The drive should instantly disappear and reappear. *(If it doesn't seem to refresh on your screen, click the refresh button in your file explorer).*

### Step 4: Upload Your `main.py` Code
1. Create a new text file on the root of the Pico drive.
2. Open it and paste your script (you can use the `main.py` blink example from our Releases to test).
3. Click **File -> Save As**, name the file `main.py`, change the save type to **All Files (*.*)**, and save it to the root of the drive.
4. Press the **BOOTSEL** button to reset the Pico and watch your code run at top speed!

---

## ⚠️ Safe Workflow Notice (Preventing OS Cache Corruption)

Because this firmware uses standard USB Mass Storage Class (MSC) to act as a flash drive, your host device (PC or Mobile Phone) may cache data in its RAM before physically writing it to the Pico. To guarantee you never corrupt your filesystem:

* **On Windows:** Always right-click the drive and click **Eject** before pressing the BOOTSEL reset button or unplugging the cable.
* **On Android/Mobile:** Swipe down your notification shade and tap **Unmount/Eject**, or use your phone's Files app to safely unmount the drive before resetting.
* **On Linux:** Always run the `sync` command in the terminal before resetting.

Once your host system confirms it is safe to remove, press **BOOTSEL** to execute your code safely!

**Also if Windows or Linux or any os says that there is a problem with the drive dont worry and if it promts you to fix the drive just click on that the main reason this can happen is if you dont eject the drive properly**.

---

## 🤝 Acknowledgments

* Special thanks to **Dan Halbert (danh)** from the core CircuitPython team for the critical reminder regarding host-side USB MSC block-level caching and corruption safety.
