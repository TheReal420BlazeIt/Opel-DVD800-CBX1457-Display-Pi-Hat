# Raspberry Pi Hat for Opel DVD800 Navi Display
Raspberry Pi Hat for Opel DVD800 Navi Display using Sony CXB1457R GVIF Chip
![Raspberry Pi GVIF Hat](https://github.com/TheReal420BlazeIt/Opel_DVD800_Display_Pi_Hat/blob/56be2cc315e514791ff7a7c733535c60d4134883/img/pi_hat_2.jpeg)
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


