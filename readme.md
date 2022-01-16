# marbastlib
A library collecting MX and Choc style footprints, as well as various other parts used to design custom keyboards. It is maintained by [ebastler](https://github.com/ebastler/) and [MarvFPV](https://github.com/marvfpv). It is made in/for KiCAD 6.0 stable version. KiCAD 5.x is not supported, and KiCAD 6.99 nightly is not tested. You can use my (significantly smaller) [legacy lib](https://github.com/ebastler/kicad-keyboard-parts.pretty) for KiCAD 5.x.

We try to offer 3D models for as many footprints in this library as possible, creating our own models where none exist. All components for which we have models available have them linked into the footprint - please place the submodule either directly into your kicad project folder, or one level above. The models will show up correctly in either case.

For now I would recommend using the `untested` branch, as many footprints are untested, but most of them are almost certain to work. Please double-check the dimensions before ordering, though. We will update the `main` branch whenever we prototype new footprints from this lib. To select a specific branch for a submodule, add it as usual with `git submodule add https://github.com/ebastler/marbastlib`, then edit `.gitmodules` to look like this:

    [submodule "marbastlib"]
	    path = marbastlib
	    url = https://github.com/ebastler/marbastlib
	    branch = untested

The third line has to be added and will determine the branch your submodule is following. After this, initialize and update it to the latest remote branch with `git submodule update --init --remote`.

### **We do not assume any responsibility for broken PCBs or damaged derived from errors in this library. Use at your own risk, and please open an issue or pull-request if you encounter any errors.**

## Update notes:

Update note (17.01.2022): Flattened the commit history after a cleanup to make the library easier to maintain. This should not have any impact on working with it. Removed the 2x1.6mm crystal footprint as it exists within KiCAD 6 base libs. Changed silkscreen layers for hotswap sockets. Moved MX hotswap footprints and HRO Type-C M-14 from `untested` to `main`, after they were confirmed working on a prototype. Updated the readme to include an explanation how to switch submodule branches.

Update note (11.12.2021): Dedicated SK6812 MINI-E footprints have been removed, and the SK6812 MINI-E symbol has been adapted to fit 6028R footprints. The pin numbering between 6028R and SK6812 MINI-E differs, so please take care to only use the updated symbol with these footprints, or your pinout will be wrong. The symbol included in marbastlib-mx will work, together with any of the 6028R footprints.

## Symbol Libs
### marbastlib-mx
* MX_Stab - a symbol used to place keyboard stabilizers
* [**UNTESTED**] LED_6028R - symbol with preassigned footprint for reverse mount 6028 RGB LEDs
* [**UNTESTED**] SK6812MINI-E - symbol with preassigned footprint for reverse mount adressable SK6812MINI-E RGB LEDs

### marbastlib-various
* BAV70_Small - a smaller version of the regular BAV70 symbol(easier to use in keyboard matrices)
* TP4056 - a cheap and easily available 1S battery charging chip
* DW01A - a cheap and easily available 1S battery protection chip
* FS8205 - a dual MOSFET used in the DW01A ref implementation
* joystick_analog - symbol for a analog, dual pot thumbstick, comes pre-assigned with a PSP-1000 thumbstick footprint
* TXB0101 - a bidirectional levelshifter
* nRF52840_holyiot_18010 - a symbol for the holyiot 18010 nRF52840 BLE module
* WS2812B-MINI - symbol with preassigned footprint for WS2812B-MINI
* WS2812_2020 - symbol with preassigned footprint for WS2812B-2020 and WS2812C-2020
* [**UNTESTED**] STM32WB5MMG - a small form factor package including STM32WB chip and antenna
* [**UNTESTED**] MAX77751 - a 1S LiIon battery management chip
* [**UNTESTED**] IS31FL3741A - a 39x9 LED multiplex driver

## Footprint libs
### marbastlib-choc
All switch and stab footprints in this lib include plate cuts on User.Eco2, as well as placement hints for both choc (User.Eco1) and MX (User.Drawings) switch spacing. LED and Stab footprints are not standalone, but intended to be combined with a switch footprint.
* [**UNTESTED**] SW_choc - solder-footprints for Kailh Choc (v1 only) switches
* [**UNTESTED**] SW_choc_HS - hotswap-footprints for Kailh Choc (v1 only) switches
* [**UNTESTED**] STAB_choc - footprint for Kailh Choc 2u stabilizers
* [**UNTESTED**] LED_choc_6028R(-FLIPPED) - add-on footprint for Kailh Choc with [6028](https://www.alibaba.com/product-detail/SMD-6028-Smd-Led-RGB-color_60283039151.html) and adressable SK6812MINI-E RGB LEDs
* [*SPECIALTY*] SW_choc_Reversible_1u - reversible footprints for Kailh Choc (v1 only) switches
* [*SPECIALTY*] SW_choc_MxCombo_1u - combo footprints for Kailh Choc (v1 only) and Cherry MX style switches
* [*SPECIALTY*] LED_choc_WS2812_2020-E(-FLIPPED) - experimental add-on footprint for Kailh Choc with reverse mounted WS2812_2020 - hand soldering only, use with caution
* [*SPECIALTY*] PLATE_choc - experimental footprint intended to be added to a choc switch so the switch footprint can be snapped off - allowing the PCB to double-function as a plate

### marbastlib-mx
All switch and stab footprints in this lib include plate cuts on User.Eco2, as well as placement hints for MX switch spacing (User.Drawings). LED and Stab footprints are not standalone, but intended to be combined with a switch footprint.
* SW_MX - solder-footprints for Cherry MX switches
* SW_MX_HS - hotswap-footprints for Cherry MX switches
* LED_MX_3mm(-FLIPPED) - add-on footprint for Cherry MX switches with 3mm single color LEDs
* STAB_MX - footprint for Cherry MX PCB-mount stabilizers
* STAB_MX_P - footprint for Cherry MX PCB-mount stabilizers mit plated screw holes
* [**UNTESTED**] LED_MX_6028R(-FLIPPED) - add-on footprint for Cherry MX switches with [6028](https://www.alibaba.com/product-detail/SMD-6028-Smd-Led-RGB-color_60283039151.html) and adressable SK6812MINI-E RGB LEDs
* [*SPECIALTY*] SW_MX_Reversible_1u - reversible solder-footprints for Cherry MX switches
* [*SPECIALTY*] LED_MX_WS2812_2020-E(-FLIPPED) - experimental add-on footprint for Cherry MX switches with reverse mounted WS2812_2020 - hand soldering only, use with caution
* [*SPECIALTY*] PLATE_MX - experimental footprint intended to be added to a Cherry MX switch so the switch footprint can be snapped off - allowing the PCB to double-function as a plate

### marbastlib-various
* nRF52840_holyiot_18010 - 3 different footprints for the holyiot 18010 nRF52840 BLE module
* SW_ESP3020 - footprint for ESP3020 SMD 2-way-switches
* LED_WS2812_2020 - footprint for WS2812B-2020 and WS2812C-2020
* [**UNTESTED**] ANT_2.4_IFA - Bluetooth IFA antenna, designed following a guide of Cypress: https://www.cypress.com/file/136236/download'
* [**UNTESTED**] SW_MSK12C02-HB - footprint for MSK12C02-HB SMD 2-way-switches
* [**UNTESTED**] joystick_psp1000 - footprint for a PSP-1000 thumbstick
* [**UNTESTED**] LED_6028R - footprint for [6028 RGB LEDs](https://www.alibaba.com/product-detail/SMD-6028-Smd-Led-RGB-color_60283039151.html) and adressable SK6812MINI-E reverse mount RGB LEDs
* [*SPECIALTY*] LED_WS2812_2020_rearmount - experimental footprint for reverse mounted WS2812_2020 - hand soldering only, use with caution
* [**UNTESTED**] MAX77751 - a 1S LiIon battery management chip
* [**UNTESTED**] QFN-60_EP_7x7_Pitch0.4mm - footprint needed for IS31FL3741A
* [**UNTESTED**] STM32WB5MMG - a small form factor package including STM32WB chip and antenna
* CON_TC2030_Outlined - footprint for a Tag-Connect TC2030 header
* USB_C_Receptacle_HRO_TYPE-C-31-M-14 - footprint for a HRO Koreaparts mid-mount USB-C 2.0 receptacle
* [**UNTESTED**] CON_MJ-4PP-9 - footprint for a 3.5mm TRRS connector
* [**UNTESTED**] CON_MJ-4PP-9_Reversible - reversible footprint for a 3.5mm TRRS connector
* ProMicro - footprint for an Arduino Pro Micro (or other compatible MCU breakout board)
* ProMicroReversible - reversible footprint for an Arduino Pro Micro (or other compatible MCU breakout board)
* SplitkbTentingPuck - footprint for a splitkb Tenting Puck
* SW_kailh_big_1u - footprint for a Kailh x Novelkeys Big Switch

## 3D Models
Many of these were provided by someone else. I do not hold any rights for those and owe the original designers big thanks. These models are NOT covered by the license applied to the rest of the repo. If no source is provided, I designed the model myself, using datasheet specs as far as possible. If your file is in this repo and you would like it gone, please contact me. I included them to make it easier to use the models directly from the library, but will request the original designer's wish!

 * SK6812Mini-E
 * WS2812B-2020
 * MJ-4PP-9
 * Seiko Epson FA-128
 * MSK12C02-HB
 * WS2812 Mini / SK6812 Mini ([source](https://grabcad.com/library/smd-ws2812b-led-1))
 * Alps SKQG style SMD switch ([source](https://grabcad.com/library/5mm-button-switch-1))
 * 1206 SMD polyfuse ([source](https://grabcad.com/library/0zcj0075af2e-1))
 * JST SH (2, 4, 5, 6, 8 pins) ([source](https://grabcad.com/library/jst-sh-smd-connectors-1/details?folder_id=3903823))
 * HRO TYPE-C-31-M-12 ([source](https://grabcad.com/library/type-c-31-m-12-1))
 * HRO TYPE-C-31-M-14([source](https://grabcad.com/library/hro-usb-type-c-31-m-14-1))
 * holyiot 18010 nRF52840 (thanks darryldh)
 * Alps EC11E and EC11N series 3D models ([source](https://tech.alpsalpine.com/e/products/cad.html))
 * Kailh Hotswap socket (MX style) ([source](https://grabcad.com/library/kailh-hotswap-mx-1))
 * Kailh Hotswap socket (Choc style) ([source](https://grabcad.com/library/kailh-1350-socket-2))
 * PSP-1000 Joystick (thanks [Hendrik](https://github.com/HendrikRoth))