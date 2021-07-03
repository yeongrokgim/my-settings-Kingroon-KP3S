# my-settings-Kingroon-KP3S

## Hardware Configurations

- Kingroon KP3S 3.0 (Shipped with `Direct Titan Extruder`)
- BLTouch v3.1
  - Probe mount 3D model was downloaded from [thingiverse](https://www.thingiverse.com/thing:4816601)
  - replaced `Z Min` probe on the mainboard, keeping black-white color-coded pinouts.
- Installed landscape LCD mount
  - LCD mount 3D model was downloaded from [thingiverse](https://www.thingiverse.com/thing:4578390)
    - note: Tried to change `define TFT_ROTATION TFT_ROTATE_90` [configuration](./Marlin/Configuration.h:2689) seems not working properly
  - Printed those parts `tft1.stl`, `tft24.stl`, `tftbase.stl`

## Instructions

1. Clone Marlin repository with 2.0.9 tag.

    ```bash
    git clone --depth 1 --branch 2.0.9 https://github.com/MarlinFirmware/Marlin.git buildspace
    ```

1. Replace configuration.

    ```bash
    cat ./Marlin/Configuration.h > ./buildspace/Marlin/Configuration.h
    cat ./Marlin/Configuration_adv.h > ./buildspace/Marlin/Configuration_adv.h
    ```

1. Build firmware.

    1. Open VS Code 
    1. Install `Auto Build Marlin` extension
    1. Open `Auto Build Marlin` tab on extension bar on left side.
    1. Click `Show ABM Panel`
    1. Click `Build` on the right side of `mks_robin_nano35`

    OR Build manually

    ```bash
    cd buildspace
    platformio run -e mks_robin_nano35 ; echo "done" >|/tmp/ipc
    ```

1. Prepare SD card to flash.

    ```bash
    cp .pio/build/mks_robin_nano35/Robin_nano35.bin /media/sdcard/robin_nano.bin
    ```

1. Update firmware on KP3S.

    - Poweroff your KP3S.
    - Put SD card with `robin_nano.bin` into KP3S.
    - Power on (You'll see `TFT Updating` on screen.)

## TODO

Follow Instructions [here](https://teachingtechyt.github.io/)

- [x] PID Autotune
- [ ] First Layer
- [ ] Baseline Print
- [ ] Extruder E-steps Calibration
- [ ] Slicer Flow Calibration
- [ ] Stepper Motor Driver Current
- [ ] Retraction Tuning
- [ ] Temperature Tuning
- [ ] Accerlation Tuning
- [ ] Linear Advance
- [ ] XYZ steps Calibration

## Resources

- https://bubba.org/kp3s/
- https://www.thingiverse.com/thing:4604687
