# Ferris sweep36

This variant of the Sweep uses 36 keys, with a direct pin schematics. As such, this is compatible only with elite-cs because pro-micros do not have enough pins.
Thanks to @sadekbaroudi for his help creating the first revision of this. He made changes ever since but the original schematics for this can be found in the [first commit](https://github.com/sadekbaroudi/sweeeeep/commit/1d4b781be16a39c897f15d12a209444b45fadd66) of his repo: [sadekbaroudi/sweeeeep](https://github.com/sadekbaroudi/sweeeeep).

The reason why this is named `sweep36` and not `sweeeeep` is because the pinout changed since the first commit.

## Original Readme and description

Please see the [original project's github page](https://github.com/davidphilipbarr/Sweep)

Initial [EE_HANDS](https://docs.qmk.fm/#/feature_split_keyboard?id=handedness-by-eeprom) make examples for this keyboard (after setting up your build environment):

    make sweep36:default:dfu-split-left
    make sweep36:default:dfu-split-right

Subsequent make example for both sides:

    make sweep36:default

[Bootmagic lite](https://docs.qmk.fm/#/feature_bootmagic?id=bootmagic-lite) is also configured on the top right key for the right halve.
