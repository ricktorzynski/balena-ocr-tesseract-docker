## Balena OCR Tesseract Docker app

Allows uploading of an image for OCR using Tesseract and deployed using Docker. This project uses Flask, a light weight web server framework, which should be used for development purposes only. OpenCV is used to reduce noise in the image for better processing by pytesseract.  Originally deployed in a Docker container on AWS - this version is revised to be deployed to BalenaCloud to a Jetson Nano device.

To get this project up and running, you need to signup for a balena account [here][signup-page] and set up a device - here is a [Getting Started tutorial][gettingStarted-link]. On balenaCloud, click "Create application", choose device, select deploy to Nvidia Jetson Nano(BETA) device.  You could also deploy to a Raspberry Pi 3.  Then select Development for the environment and select Ethernet for connection - I tried to use Ethernet + Wifi, but it is difficult to get to wifi to work properly, so I connected the Jetson Nano using Ethernet connection. The Jetson Nano does not come with built in wifi.  Then download the created Balena OS image and using Balena Etcher, burn the image onto a SD card.  Put the SD card in the Jetson Nano, plug in the ethernet and power up the Jetson Nano.  If you use a barrel connector for power, remember to add a J48 jumper to toggle the power supply. Once you are set up with balena, you will need to clone this repo locally:
```
$ git clone https://github.com/ricktorzynski/balena-ocr-tesseract-docker.git
```
Then add your balena application's remote:
```
$ git remote add balena username@git.balena-cloud.com:username/myapp.git
```
and push the code to the newly added remote:
```
$ git push balena master
```
It will take a few minutes for the code to push. While you wait, enable the device URLs so you can see the server outside of the local network. This option can be toggled on the device summary page, pictured below or in the `Actions` tab in your device dashboards.

![Enable device URL](/img/balenacloud.png)

If you go to the public URL enabled above, you should see:
![app index](/img/balenacloud2.png)

And if you upload an image to be OCRed, you should see:
![ocr](/img/balenacloud3.png)

balenaCloud is a great way to test and manage deployments of apps to entire FLEETS of IoT devices!

Here is a link to the original [ocr-tesseract-docker] project that was deployed to AWS.

[balena-link]:https://balena.io/
[signup-page]:https://dashboard.balena-cloud.com/signup
[gettingStarted-link]:http://balena.io/docs/learn/getting-started/
[ocr-tesseract-docker]:https://github.com/ricktorzynski/ocr-tesseract-docker
