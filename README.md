# PLR Klipper

YUMI_PLR for Klipper is a simple print recovery system for Klipper, a 3D printer firmware. It allows you to resume prints after a power loss or other types of MCU disconnection interruption. Please note there is no guarantee that it will work in 100% of cases because the Z-axis must not have moved, so do not touch the machine in case of a power cut.
YUMI_PLR для Klipper — это простая система восстановления печати для 3D-принтера с прошивкой Klipper. Она позволяет возобновить печать после отключения питания или других сбоев в работе микроконтроллера. Обратите внимание, что нет гарантии, что система сработает в 100 % случаев, так как ось Z не должна была сдвинуться с места, поэтому не прикасайтесь к принтеру в случае отключения питания.

## Prerequisites
Being on a user named 'pi' is mandatory. With the user pi, having already installed Klipper, Moonraker, and Mainsail (you can use Kiauh).
Наличие пользователя с именем 'pi' обязательно. Пользователь pi уже установил Klipper, Moonraker и Mainsail (можно использовать Kiauh).

To install YUMI_PLR Klipper, follow the steps below:
You must have created your Klipper installation with the user 'pi'; the script does not yet fully handle other cases.
Чтобы установить YUMI_PLR Klipper, выполните следующие действия:
Вы должны были создать установку Klipper с пользователем 'pi'; скрипт пока не поддерживает другие варианты.
 
## Installation
1. Clone the YUMI_PLR Klipper repository from GitHub to your local machine:
```bash
git clone https://github.com/Aleandr74/YUMI_PLR.git
cd YUMI_PLR
./install.sh
```

###start-gcode add in your slicer:
```bash
G31
save_last_file
SAVE_VARIABLE VARIABLE=was_interrupted VALUE=True
```

###end-gcode add in your slicer:
```bash
SAVE_VARIABLE VARIABLE=was_interrupted VALUE=False
clear_last_file
G31
```
###Before layer change G-gcode add in your slicer:
```bash
LOG_Z
```
6. To resume printing after a power cut, simply execute the 'RESUME_INTERRUPTED' macro in the MAINSAIL console or via the Macro button on the MAINSAIL dashboard.
7. Чтобы возобновить печать после отключения питания, просто выполните макрос RESUME_INTERRUPTED в консоли MAINSAIL или нажмите кнопку «Макрос» на панели управления MAINSAIL.

## Known Bugs:
The preview image of the gcode file is not rebuilt.
 




