🌟 Key Features

☆ Fixed Flash Allocation: Custom-compiled at a hard 1MB storage boundary . 

☆ Completely fixes the bug where the Pico panics and wipes/deletes your main.py file on reboot.

*CPU Overclocked to 200MHz

☆ Slick Drive Identity: Set up to cleanly mount as a reliable virtual drive just like Circuitpython 

💾 Installation

(1)Hold the BOOTSEL button on your Pico and plug it into your computer.

(BEFORE DOING THE NEXT STEP ITS BETTER TO DRAG AND DROP THE ERASE-FLASH.UF2 FILE FROM RELEASES AND ON THE PICO WAIT FOR THE LED TO TURN OFF THEN THE RPI-RP2 VOLUME MAY APPEAR AUTOMATICALLY OTHERWISE HOLD BOOTSEL)

(2)Drag and drop the firmware.uf2 file from this repository releases onto the RPI-RP2 volume.

(3)Once it reboots, open the drive, drop your main.py code in, and watch it run at top speed without ever losing your files again!
YOU ALSO MAY RENAME THE DRIVE TO WHATEVER YOU LIKE

ITS THAT EASY

next in uploading code go to the pico's drive and create a text file then name it into boot
now copy and paste the code(the code is available  IN RELEASES boot.py file)  (reset mechanism using BOOTSEL button)


now in notepad click File-Save As then file name boot.py,then change save as type to all files and save it to the root directory of the pico drive not the RPI-RP2 drive

NOW UNPLUG THE PICO AND PLUG IT BACK IN AND THE DRIVE SHOULD POP UP AGAIN NOW PRESS THE BOOTSEL BUTTON AND THE DRIVE SHOULD DISAPPEAR AND APPEAR AGAIN (IF NOT PRESS THE REFRESH BUTTON IN EXPLORER)

now to upload our main.py code create a new txt file there change its name to main then open it in notepad and paste the code (availabe in releases main.py file)

then file-save as,then name -main.py and change save as type to all files (this is way we upload code here it applies for any code) and save it to the root of the pico,now if you look at the pico the led wont blink,beacuse there is one more step that is to press the BOOTSEL button to reset the pico ans thats the end of this readme

***********************______**************************THE END**************************************************************************
