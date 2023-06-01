This code was adapted from the original, developed by Seeed Studio: 
 - https://wiki.seeedstudio.com/xiao_esp32s3_camera_usage/#project-i-making-a-handheld-camera

**Important changes:**
- It is not necessary to to cut off J3 on the XIAO ESP32S3 Sense expansion board. It is possible to use the XIAO's SD Card Reader. For that you need use SD_CS_PIN as 21.
- The camera buffer data should be captured as RGB565 (raw image) with a 240x240 frame size  to be displayed on the round display. This raw image should be converted to jpeg before save in the SD card. This can be done with the line: 
  - esp_err_t ret = frame2jpg(fb, 12, &out_buf, &out_len) 
- The XCLK_FREQ_HZ should be reduced from 20KHz to 10KHz in order to prevent the message "no EV-VSYNC-OVF message" that appears on Serial Monitor (probably due the time added for JPEG conversion. 

Adapted by MRovai @02June23