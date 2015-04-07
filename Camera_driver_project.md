### Introduction ###

The project would primarily involve studying the C3088 camera sensor module which uses OV6620 (Camera sensor from Omnivision). The OV6620 supports CIF resolution, which would be sufficient for any building any kind of surveillance/monitoring system. The challenge out here would be to be able to manage within 4K of internal SRAM and dump CIF/QCIF sized BMP images. The process of conversion from bayer format to BMP format would be handled by the uNiBoard v1.1 by doing some on-the-fly processing.


### References ###
1. [C3088 datasheet](http://uniboard.googlecode.com/files/C3088.pdf)

2. [OV6620 datasheet](http://uniboard.googlecode.com/files/ov6620DSLF.PDF)

3. [Sample project](http://uniboard.googlecode.com/files/C3088_interfacing_reference.pdf) (ATMega16 interfacing with C3088)

4. [BMP file format](http://en.wikipedia.org/wiki/BMP_file_format)

5. [Bayer image format](http://en.wikipedia.org/wiki/RAW_image_format)

6. [SD/MMC card interface](http://uniboard.googlecode.com/files/SD-MMC_reference_manual.pdf)

7. [AVRcam project](http://www.jrobot.net/Projects/AVRcam.html)

8. [CMUcam project](http://www.cmucam.org/)