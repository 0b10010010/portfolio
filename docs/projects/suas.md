#SUAS Design Team
##[Image Analysis](https://github.com/0b10010010/ImageAnalysis)

The following screenshot shows the user interface I developed in order to load, crop, classify, geolocate, and export target images taken during the flight. The process is based on HITL (Human In The Loop).
![](../img/suas_gui.png)

The operator can check incoming images for targets which are colored alphanumeric characters printed on some shapes. Then the operator can scroll in and out to inspect the image and drag to crop the target along with its metadata to export out for submission. The GUI will return calculated GPS coordinates of each targets within the image.

The system is based on an OBC (Onboard Computer), STM32L4 Nucleo, camera, and GPS receiver. When the voltage of hotshoe on camera goes low, or high depending on the camera, triggers an interrupt routine on a microcontroller to send the last known filtered GPS location as serial data over USB. Then the OBC will convert serial data into a text file with new GPS coordinates on camera trigger appended. The directory where images and GPS data are stored is mirrored with another directory on GCS (Ground Control Station).

The following is an example output:
```text
Image index: 1 Date:2020/2/1 18:16:32:200239166 lat/lon: 39.2027969,-96.5458908
Image index: 2 Date:2020/2/1 18:16:35:400238232 lat/lon: 39.2027969,-96.5442504
Image index: 3 Date:2020/2/1 18:16:38:200237413 lat/lon: 39.2027931,-96.5458908
Image index: 4 Date:2020/2/1 18:16:41:400236475 lat/lon: 39.2027931,-96.5458908
```


