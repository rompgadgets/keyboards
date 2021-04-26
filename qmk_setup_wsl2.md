# QMK Setup for Windows 10 WSl2

Base install is on ubuntu 18.04
1. Upgrade to python 3.9
- add-apt-repository ppa:deadsnakes/ppa
- apt install python3.9
- apt install python3.9-distutils
- apt install python3.9-venv
- (Optional) setup a venv for qmk

2. Install qmk dependencies
- apt install avrdude
- apt install dfu-programmer
- apt install dfu-util
- apt instal gcc-avr
- apt install binutils-arm-none-eabi
- apt install libnewlib-arm-none-eabi
- apt install avr-libc
- apt install binutils-avr

3. Run QMK setup
- `
qmk setup
`

4. Build a QMK image
- `
qmk compile -kb clueboard/66/rev3 -km default
`

5. Install QMK Toolbox on Windows 10
- Flash the hex file created in step 4 (Navigate to `\\$wsl\\<location of wsl2 install of QMK>\\image.hex`)

# Build a new QMK image for fresh built IRIS rev4 to swap encoder locations
Once built we may need to flash firmware to enable or change  features.

1. For my Iris rev4 I need to set the encoder on the right side to be volume up/down instead of page up/down as I only installed a single encoder on the right side.
2. Copy the via directory located at `qmkfirmware/keyboards/keebio/iris/keymaps/via` to `viacustom`
3. Inside keymap.c change the index == 0 to index == 1 for the KC_VOLU/KC_VOLD encoder.
4. Now we need to build the new image to flash
- `
qmk compile -kb keebio/iris/rev4 -km viasig
`
5. Now flash each side of the keyboard with QMK toolbox or from the command line with the resulting image:
- `
keebio_iris_rev4_viasig.hex
`
6. Now you may have to reset any saved keymaps created previously with VIA but your encoder will now be correctly mapped.

# Changing the Bootloader
1. Start a new keymap for your keyboard.  In this example we will be modifying the Lily58 Pro. So in the keymap folder I started with the VIA as a base.
`
cp -R via/ viasig/
`
2. Find the pins to use for setting QMK_ESCAPE_INPUT and QMK_ESCAPE_OUTPUT.  I pulled these from the config.mk and used what should be the ESC key by picking the first COL and ROW entry.
3. Add those values to the config.mk and set the `BOOTLOADER = qmk-dfu` in the rules.mk
4. You can then build the bootloader only or all files from your new keymap directory using the production target
`make lily58:viasig:bootloader` or you can use `make lily58:viasig:production`
5. Flash the bootloader using your AVR ISP programmer.