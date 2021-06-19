# my-settings-Kingroon-KP3S

## Instructions

1. Clone Marlin repository with 2.0.9 tag.

```bash
git clone --depth 1 --branch 2.0.9 https://github.com/MarlinFirmware/Marlin.git buildspace
```

2. Replace configuration.

```bash
cat ./Marlin/Configuration.h > ./buildspace/Marlin/Configuration.h
cat ./Marlin/Configuration_adv.h > ./buildspace/Marlin/Configuration_adv.h
```

3. Build firmware.

```bash
cd buildspace
platformio run -e mks_robin_nano35 ; echo "done" >|/tmp/ipc
```

4. Prepare SD card to flash.

```bash
cp .pio/build/mks_robin_nano35/Robin_nano35.bin /media/sdcard/robin_nano.bin
```

5. Update firmware on KP3S.

- Poweroff your KP3S.
- Put SD card with `robin_nano.bin` into KP3S.
- Power on (You'll see `TFT Updating` on screen.)
