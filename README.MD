# Ender3 Pro Klipper/Mainsail configs

## Setup

- Ender 3 Pro (2022)
  - Creality [CR-Touch](https://www.creality3dofficial.com/products/creality-cr-touch)
  - Creality Hot Bed Leveling Column [Silicone Bed Mounts](https://duckduckgo.com/?q=creality+silicone+bed+mounts&t=newext&atb=v371-1&iax=images&ia=images)
  - [Aluminum wheels](https://duckduckgo.com/?q=ender+3+aluminum+leveling+wheels&t=newext&atb=v371-1&iar=images&iax=images&ia=images&iai=https%3A%2F%2Fimages-na.ssl-images-amazon.com%2Fimages%2FI%2F719ko8GM16L._SL1000_.jpg)
  - Creality [Ender-3 V2/S1/Neo display](https://www.walmart.com/ip/Creality-Ender-3-V2-4-3-Inch-Screen-LCD-Display-Screen-kit-for-Ender-3-V2-with-V4-2-2-V4-2-7-Mainboard-3D-Printer-Black/796002397?wmlspartner=wlpa&selectedSellerId=101099794)
  - Creality [Spider 3.0 Pro High temp/flow hotend](https://store.creality.com/products/spider-v3-high-temperature-and-high-flow-hotend-pro)
  - [Capricorn PTFE Tube](https://www.captubes.com)
  - Creality [Dual-Z upgraded kit](https://www.amazon.com/Official-Creality-Upgrade-Stepper-3D/dp/B09N8QQDSP)
    - Careful with the knock-offs - Not as good overall in my experience.
  - Creality [enclosure](https://www.amazon.com/s?k=creality+ender+3+enclosure)
    - Get what works for you
  - Creality 4.2.2 (GD)
    - Firware
        - Marlin
            - Stock
            - Custom
            - [MRisco](https://github.com/mriscoc/Ender3V2S1)
        - KLipper
            - Custom setup on X86 Linux
            - MainsailOS on RPI4 w/Display
  - [CURRENT] BTT [SKR Mini E3 V3](https://bigtree-tech.com/blogs/news/new-release-bigtreetech-skr-mini-e3-v3-0-control-board)
    - Firmware
        - Marlin
            - Default
            - MRisco
                - Wont work with updated display w/o custom cable
                    - [Build](https://www.smith3d.com/skr-mini-e3-v2-v3-on-ender-3-v2-ender-3-s1-lcd-dwin-knob-screen/)
                    - [Buy](https://www.amazon.com/dp/B092JBHDYC?psc=1&ref=ppx_yo2ov_dt_b_product_details)
        - Klipper
            - MainsailOS
                - RPI4 with official [Touch Display](https://www.raspberrypi.com/products/raspberry-pi-touch-display/) and case

## Klipper
E-Steps
- Retract filament up stepper motor
- Undo stepper motor side of bowden tube
- Cut flust with pneumatic fitting
- Issue the following Klipper Console commands
  > M83

  > G1 E100 F100

  - This will extrude filiment.
  - You are requesting 100mm but what you get may vary
  - Measure the filament
  - Get the `rotation_distance` value from the extruder as found in printer.cfg
  - Do some math: `rotation_distance` = `rotation_distance` * (`actual_length` * `requested_length`)
    - `rotation_distance` from printer.cfg
    - `actual_lenght` of the filiment you measured
    - `requested_lengh` is what we requested which is `100`
  - Update `rotation_distance` in the printer.cfg file with this new value.
  - Click `Save & Restart`
- Repeat the commands to extract 100mm of filament and measure.
  - It should be close to 100mm
  - if not just do the math again and update the config file.
  - Repeat as necessary