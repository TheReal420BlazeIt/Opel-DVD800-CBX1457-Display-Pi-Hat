# Raspberry Pi Hat for Opel DVD800 Navi Display
Raspberry Pi Hat for Opel DVD800 Navi Display using Sony CXB1457R GVIF Chip

![Raspberry Pi GVIF Hat](https://github.com/TheReal420BlazeIt/Opel_DVD800_Display_Pi_Hat/blob/56be2cc315e514791ff7a7c733535c60d4134883/img/pi_hat_2.jpeg)
## Project
The reason for this project is because the original radio for my car (DVD800 Navi) is quite outdated. Old navigation maps, no Bluetooth playback, etc. So the idea was to use a Raspberry Pi as a head-unit. 
Because I like the aesthetic of the original centre console of my car, I decided to reverse engineer my car's radio original display, so it can be used with the Pi. 

![Android Auto on origional display](https://github.com/TheReal420BlazeIt/Opel_DVD800_Display_Pi_Hat/blob/02293e8a4e8393881985643bf354ae22a1c8a668/img/display_android_auto.jpeg)
![Display Part Number](https://github.com/TheReal420BlazeIt/Opel_DVD800_Display_Pi_Hat/blob/02293e8a4e8393881985643bf354ae22a1c8a668/img/display_part_number.jpeg)
## Parts
All the parts are easy to get at every electronics shop. Except for the CBX1457. It was quite hard to find the chip. I ended up with ordering one from AliExpress. Quite expensive (around 35 euro's), but it works like a charm. Another option is to salvage one from a car head-unit that uses the same video chip. I ordered the PCB from JLCPCB.

CBX1457 datasheet: https://datasheetspdf.com/pdf-down/C/X/B/CXB1457R-SonyCorporation.pdf

## Raspberry Pi config.txt
The Raspberry Pi needs to be configured to output RGB video over GPIO. To enable this, we need to add a couple of lines in the config.txt on the Pi boot partition:

    gpio=0-9=a2
    gpio=12-17=a2
    gpio=20-25=a2
        
    dtoverlay=dpi18
    overscan_left=0
    overscan_right=0
    overscan_top=0
    overscan_bottom=0
    framebuffer_width=480
    framebuffer_height=240
    enable_dpi_lcd=1
    display_default_lcd=1
    dpi_group=2
    dpi_mode=87
        
    dpi_output_format=286742
        
    dpi_timings=480 0 50 12 50 240 0 6 3 10 0 0 0 60 0 9000000 3

Documentation on Raspberry Pi DPI video: https://pip.raspberrypi.com/categories/685-whitepapers-app-notes/documents/RP-003471-WP/Using-a-DPI-display.pdf

## Other Vehicles
I only tested this setup on the DVD800 Navi display of an Opel Insignia. Other Opel/Vauxhall models with the same DVD800 Navi radio system should work the same (e.g. Astra/Zafira). This display uses RGB666 video input, so only 6 bits per color are used. 

This particular setup does not use bits 0 & 1 for each color on the CBX chip. For example: the Pi's red bit 0 goes to red bit 2 on the CBX chip.

The CBX1457 chip is capable of using RGB888 video, so for some vehicles this setup may be different. 

This hat may work on other car displays that use the CBX1457 transmitter in the head unit, however, the hardware/software setup may be different. The best option is to check your car's display datasheet & inspect the display driver PCB.


