
# DGUS-reloaded (for Klipper) DWIN_SET, CR6Community Edition
<img src="https://github.com/user-attachments/assets/bd558039-6adc-4223-a1a7-f82a2d4f3871" alt="Home Screen" width="180" height="320">
<img src="https://github.com/user-attachments/assets/6b18f104-7bdf-492c-8975-a885a7761071" alt="ZOffset Screen" width="180" height="320">
<img src="https://github.com/user-attachments/assets/8f058b3d-4a0a-4c5d-b825-0e167c32e92f" alt="ABL Screen" width="180" height="320">
<img src="https://github.com/user-attachments/assets/1a2df1ad-7fd8-4d04-8f1c-f8648cd6a2e3" alt="PID Tuning Screen" width="180" height="320">

<img src="https://github.com/user-attachments/assets/1d66360d-592c-44f6-9bf9-efef93a1ee99" alt="Change Filament Screen" width="180" height="320">
<img src="https://github.com/user-attachments/assets/3cb87043-a336-48d8-89c0-f32ac613a1b6" alt="Delete File Screen" width="180" height="320">
<img src="https://github.com/user-attachments/assets/40c1e416-c654-4c1e-a515-7bdb79ab9b6a" alt="Print Menu Screen" width="180" height="320">
<img src="https://github.com/user-attachments/assets/a1c58c88-d9fa-495b-ac4f-879d8d30f462" alt="Print Status Screen" width="180" height="320">

This DWIN touchscreen firmware is designed and compiled to run on the portrait-mode T5L 272x480 pixel DWIN displays provided stock with Creality CR6-SE and CR6-MAX FDM printers.

Initially refactored and extended from the T5UID1 DGUS-reloaded firmware by Desuuuu which is available from [this repository](https://github.com/Desuuuu/DGUS-reloaded-Klipper).  

At release 0.3, completely refactored again, to closely resemble the [CF6.1 Community Firmware](https://github.com/CR6Community/CR-6-touchscreen) in look, feel, terminology, and workflow logic.


## Disclaimer
**This software is provided without any warranty. You are solely responsible for your use of it.**

## Features
This firmware was inspired by the CR6Community Firmware touchscreen firmware, but it is NOT as feature-rich as the CR6Community Firmware. 

Features present in this version of the UI include:
* Support for _most_ workflows best performed standing at the printer 
* Emergency Stop (M112) button on every screen
* Ability to Tune some printer settings during a print
* PID autotuning for both Nozzle and for Bed, with SAVE_CONFIG option
* Pre-defined Material heat settings for PLA, PETG and ABS
* Screen Display Brightness adjustment
* Pause/Resume/Cancel print controls 
* Support for M73 message display during printing
* SET_GCODE_OFFSET Z for current print session
* Support for manual leveling, for those who have retrofit bed wheels
* Run ABL with option to SAVE_CONFIG (default) Profile
* Display name of file currently being printed
* Display elapsed time since starting current print

NEW at v0.3.8:
* Reprint last job
* Enable|Disable Runout Sensor
* Printer halts and prompts for filament, if Runout Sensor is Enabled AND Filament is not detected

NEW at v0.3.9:
* New Z Offset calibration screen
* LOAD|REMOVE default Bed Mesh profile feature added to the ABL screen. Also supports viewing other profiles, if loaded via CONSOLE
* Enhanced Manual Leveling screen - also supports ABL users with ability to test/measure gaps at each corner + in center of bed
* Able to see status of - and Enable|Disable - the Runout sensor while printing or paused.  

NEW at v0.4.1:
* Added displays of Print Time Remaining and Print Time Elapsed
* Moved Gcode Offset to the Tune screens only added LED On/Off to the Print Status and Print Paused screens
* Added more controls to the Print Finished screen, to support post-print workflows
    
NEW at v0.4.2:
* Replaces Repeat Last Print functionality with a full scroll/select/print capability for all .gcode files on the Virtual SD Card.
* Removed from beta and released as STABLE.

NEW at v0.4.3
* Adds a Delete File function to the Print_Menu page. 
  * Includes an "Are you sure?" popup to Confirm/Cancel each request
  * Shrinks the Refresh button to make space for the new button on the page

NEW at v0.4.4
* Modifies the Information page to display the current version of the DGUS-Reloaded Klipper component
* Adds an information icon to the Home page, to help users discover and access the Information page
* Corrects a compilation error which may have prevented switching to the Please wait... page, when Homing in version 0.4.3.

NEW at v0.4.5
* Adds Firmware Retraction controls to the Prepare and Printing Tune pages
* Adds Material Presets editing capability to the SetUp page
* Modifies the Automatic Bed Leveling page layout and brightens the mesh values display

>> **CAUTION:** The automatic bed-leveling function provided with this firmware ONLY works correctly if you also configure your printer.cfg to perform a 5x5 bed mesh.  If you do not want to use a 5x5 mesh, do not use this ABL function.

Coming Soon:
* Colour-coded bed mesh display, with user-definable threshold of how flat you consider to be "green".
* Extruder rotation distance calibration aid (similar to e-steps calibration on Marlin CF6.1, but Klipper does not support automating the update, at the final step.)

## Compatibility
This firmware **should** be compatible with any configuration of CR6-SE or CR6-MAX printer, regardless of whether that machine is fully stock or substantially modified. (It even includes a manual leveling screen, for those of you who have installed manual bed-leveling wheels.)

Testing is done on the following machine:

* Creality CR6-SE, modified with:
    - a Creality ERA 1.1.0.3 motherboard
    - a direct drive Orbiter v1.5 extruder with Moons pancake motor
    - a Dragon HF hotend
    - a PEI flexible magnetic sheet print bed

## Prerequisites
For this DWIN_SET to work with your printer, you must also:
- Install the latest version of MainsailOS
- Tailor your Klipper installation, MainsailOS configuration and Cura
- Flash the applicable pre-compiled Klipper.bin file provided for you in the other repo. 

[All of the instructions for achieving the above are provided with the matching Klipper component release, here.](https://github.com/Thinkersbluff/dgus-reloaded_klipper)

## How to Customize the UI Look and Feel
You can make modifications to the DWIN_SET firmware by opening the `DWprj.hmi` file in **DGUS Tools**.  The tool, developer's documents and Tutorial URLs have been added to the repository at this release, to help anyone who would like to learn how this is done.

You can edit the graphics using a simple bitmap editing tool, like Windows PAINT.

After finishing your modifications, you will need to press the *Generate* command from the DGUSTool File menu to update the 3 required binary files (13TouchFile.bin, 14ShowFile.bin and 22_Config.bin) in the DWIN_SET folder.
If you modified any of the screen layouts, icons or buttons, you will also need to use the ICL tool to regenerate the applicable ICL file(s) (intuitively named: 24_icons.icl, 27_buttons.icl, 32_screens.icl, 30_progress_left.icl and 37_progress_right.icl).

You can then flash your touchscreen using the resulting `DWIN_SET` folder.

## Functional Changes Also Require Edits To Modified Klipper Files
Please note, that to actually add/delete/modify functionality, you will also need to make the necessary changes to the applicable modified Klipper files.

If you add any data variable display widgets to any of the screens, you also need to edit the DGUS-reloaded Klipper file pages.cfg in ~/klipper/klippy/extras/t5uid1/dgus-reloaded, so that the data will be refreshed and maintained when that screen is being displayed.

If you wish to modify the nozzle and bed temperature presets for PLA, ABS and/or PETG, you will need to modify the file _init_.py in the folder ~/klipper/klippy/extras/t5uid1/dgus-reloaded, so that the program will initialize those variables with the values of your choosing.

## Additional background info is available in the Desuuuu/DGUS-reloaded-Klipper-config Wiki
* [Flashing the firmware](https://github.com/Desuuuu/DGUS-reloaded-Klipper/wiki/Flashing-the-firmware)
* [Print status](https://github.com/Desuuuu/DGUS-reloaded-Klipper/wiki/Print-status)
* [Print progress display](https://github.com/Desuuuu/DGUS-reloaded-Klipper/wiki/Print-progress-display)

## How to Contribute

CR6Community Firmware features NOT present in this release may be developed in future releases, but no schedule commitment is possible for such extensions.  Users who are able to define and develop such modifications are welcome to fork this repository and to submit Pull Requests or to open Discussions or Issues as appropriate, to propose those changes.

## Credits
| Material                                                                       | Author                                                    | Modified | License                                                               |
|:------------------------------------------------------------------------------:|:---------------------------------------------------------:|:--------:|:---------------------------------------------------------------------:|
| [DGUS-RELOADED DWIN UI](https://github.com/Desuuuu/DGUS-reloaded-Klipper)      | [Desuuuu](https://github.com/Desuuuu)                     | Yes      | [GPLv3](http://www.gnu.org/licenses/gpl-3.0.html)   
| [Klipper logo](https://github.com/KevinOConnor/klipper)                        | [KevinOConnor](https://github.com/KevinOConnor)           | Yes      | [GPLv3](http://www.gnu.org/licenses/gpl-3.0.html)                     |
| [Feather icons](https://feathericons.com/)                                     | [Cole Bemis](https://twitter.com/colebemis)               | Yes      | [MIT](https://github.com/feathericons/feather/blob/master/LICENSE)    |
| [3D Printing Line icons](https://www.iconfinder.com/iconsets/3d-printing-line) | [Sam Baines](https://www.iconfinder.com/conceptbaines)    | Yes      | [CC-BY 3.0](https://creativecommons.org/licenses/by/3.0/legalcode)    |
| [Fan icon](https://thenounproject.com/term/fan/1153915/)                       | [Atif Arshad](https://thenounproject.com/atifarshad/)     | Yes      | [CC-BY 3.0](https://creativecommons.org/licenses/by/3.0/us/legalcode) |
| [Snow icon](https://thenounproject.com/term/snow/1959859/)                     | [Shashank Singh](https://thenounproject.com/rshashank19/) | Yes      | [CC-BY 3.0](https://creativecommons.org/licenses/by/3.0/us/legalcode) |
| [Electric Motor icon](https://thenounproject.com/term/electric-motor/2734486/) | [Verry](https://thenounproject.com/verry.dsign.creative)  | Yes      | [CC-BY 3.0](https://creativecommons.org/licenses/by/3.0/us/legalcode) |
| [Probe icon](https://thenounproject.com/term/probe/1841345/)                   | [Mohamed Mbarki](https://thenounproject.com/mb.icons)     | Yes      | [CC-BY 3.0](https://creativecommons.org/licenses/by/3.0/us/legalcode) |
| [Wheel icon](https://thenounproject.com/term/wheel/92430/)                     | [Deivid Sáenz](https://thenounproject.com/deivid.saenz)   | Yes      | [CC-BY 3.0](https://creativecommons.org/licenses/by/3.0/us/legalcode) |
| [Ruler icon](https://thenounproject.com/term/ruler/1738925/)                   | [Three Six Five](https://thenounproject.com/365)          | -        | [CC-BY 3.0](https://creativecommons.org/licenses/by/3.0/us/legalcode) |
| [Wrench icon](https://www.flaticon.com/free-icons/preferences)                | [Freepik - Flaticon](https://www.flaticon.com)            | Yes      | [Free-Use](https://www.freepikcompany.com/legal?&_ga=2.208290896.334573684.1672634783-793280358.1672634783&_gl=1*bcixj4*fp_ga*NzkzMjgwMzU4LjE2NzI2MzQ3ODM.*fp_ga_1ZY8468CQB*MTY3MjYzNDc4My4xLjEuMTY3MjYzNDgzMC4xMy4wLjA.*test_ga*NzkzMjgwMzU4LjE2NzI2MzQ3ODM.*test_ga_523JXC6VL7*MTY3MjYzNDc4My4xLjEuMTY3MjYzNDgzMS4xMi4wLjA.#nav-flaticon-agreement) |
Emergency Stop icon copied from [KlipperScreen](https://github.com/jordanruthe/KlipperScreen) | [Jordan Ruthe](https://github.com/jordanruthe)  | Yes        | [CC-BY 3.0](https://creativecommons.org/licenses/by/3.0/us/legalcode) |

## License
[GPLv3](http://www.gnu.org/licenses/gpl-3.0.html)
