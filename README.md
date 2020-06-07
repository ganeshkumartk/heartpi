<h1 align="center"> HeartPi 💓🖱 </h1>
<h4 align="center">💓🌡IoT based Heart rate measurement using Raspberry pi, OpenCV and Thinkspeak dashboard</h4><br>

Monitoring of Heart Rate is a necessity in almost all the telemedicine fields. The cost of external sensors and the presuure appied by the sensors on the fragile skin of children and old age people invokes the demand for contacless monitoring of Heart Rate. The same can also be used for future research in Stress Monitoring, Measuring attentiveness while watching a video tutorial.

This Project developed records the live video of a single person using Raspberry Pi & Camera and gives a real time graph with the heart rate value in beats per minute. The values get automatically stored in a csv file for future use. The model also makes a person aware for high heart rate by Realtime Dashboard via ThinkSpeak API.

## Table of contents

* [Technology behind](#technology-behind)
* [Usage](#usage)
* [Project Setup](#project-setup)
* [ScreenShots](#screenshots)
* [Issues?](#issues)
* [Contribute?](#contribute)
* [Credits](#credits)
* [Contact](#contact)

## Technology behind

[Remote photoplethysmography (rPPG)](https://www.noldus.com/blog/what-is-rppg) enables contactless monitoring of human cardiac activities by detecting the pulse-induced subtle color variations on human skin surface using a multi-wavelength RGB camera. In recent years, several core rPPG methods have been proposed for extracting the pulse signal from a video. These include the following: 

* Blind source separation (BSS) (e.g., principal component analysis (PCA)-based and independent component analysis (ICA)-based, which use different criteria to separate temporal RGB traces into uncorrelated or independent signal sources to retrieve the pulse
* CHROMEANCE, which linearly combines the chrominance signals by assuming a standardized skin color to white-balance the images;
* PBV, which uses the signature of blood volume changes in different wavelengths to explicitly distinguish the pulse-induced color changes from motion noise in RGB measurements
* SR, which measures the temporal rotation of the spatial subspace of skin pixels for pulse extraction.


<p align="center">
  <img src="https://github.com/CoDeRgAnEsh/heartpi/blob/master/SS%20Pics/Capture.PNG?raw=true" alt="Pi-camera" width="400" height="800"/>
</p>
<h5 align="center"> rPPG Implementation via Blind Source seperation (PCA & FastICA) </h5> <br>


## Usage

* Connect your Pi Camera in Camera slot using Camera cable. Once installed test your pi camera for brightness and adjust. [See reference](https://projects.raspberrypi.org/en/projects/getting-started-with-picamera)
~~~bash
raspistill -o Desktop/image.jpg
~~~

<p align="center">
  <img src="https://www.arducam.com/wp-content/uploads/2020/02/raspberry-pi-camera-pinout-camera-2.png" alt="Pi-camera" width="400" height="400"/>
</p>
<h5 align="center"> Raspberry Pi connected with Picamera </h5> <br>

> 👉 _If your connecting your Usb camera, skip the first step and go ahead as Pi automatically installs drivers for camera._

### Project Setup

<p align="center">
  <img src="https://github.com/CoDeRgAnEsh/heartpi/blob/master/SS%20Pics/InkedMeasuring_Pulse_Rate_with_a_Webcam_-_a_Non-conact.pdf_LI.jpg?raw=true" alt="Project setup" width="400" height="400"/>
</p>
<h5 align="center"> Project setup </h5> <br>

* Open CLI(cmd prompt)/Terminal

* Git Clone this repo
~~~bash
git clone https://github.com/CoDeRgAnEsh/heartpi.git
~~~
* Do not have GIT? Download this as zip folder from Right Corner Option and extract it

* Open the directory of Cloned repo/Extracted folder
~~~bash
cd heartpi
~~~
* Install Python3.7 (Works on Python 3.7+ as some libraries are depreciated in Py2.7-Py3.5)
~~~bash
sudo apt-get install python3 python3-pip
~~~
* Install dependencies
~~~bash
pip install -r 'requirements.txt'
~~~
* Open [Heartrate.py](https://github.com/CoDeRgAnEsh/heartpi/blob/master/Heartrate.py) & Place Your Thinkspeak IO Credentials(if you wish to stream to your Dashboard) and Save.
~~~python
key ='YOUR_WRITE_KEY'
~~~
* Place the haarcascade_frontalface_default.xml file for face and forehead detection, if you wish to change the path you can update
~~~python
face_cascade = cv2.CascadeClassifier('/home/pi/<your-path>/haarcascade_frontalface_default.xml')
~~~
* Run Python script to get working at Raspberry Pi
~~~bash
python3 -W ignore Heartrate.py
~~~

## ScreenShots

<p align="center">
  <img src="https://github.com/CoDeRgAnEsh/heartpi/blob/master/SS%20Pics/Capture1.PNG?raw=true" alt="Heart rate Testing Pic" width="800" height="400"/>
</p>
<h5 align="center"> (a). Heart rate Testing (via SSH using VSCode ext in pi) </h5> <br>

<p align="center">
  <img src="https://github.com/CoDeRgAnEsh/heartpi/blob/master/SS%20Pics/Figure_5.png?raw=true" alt="Heart rate Power graph" width="400" height="400"/>
</p>
<h5 align="center"> (b). Heart rate Power Spectrum Graph </h5> <br>

<p align="center">
  <img src="https://github.com/CoDeRgAnEsh/heartpi/blob/master/SS%20Pics/Figure_2.png?raw=true" alt="Heart rate Power graph" width="400" height="400"/>
</p>
<h5 align="center"> (c). Heart rate variation mapped in RGB Channels using PCA & FastICA </h5> <br>

<p align="center">
  <img src="https://github.com/CoDeRgAnEsh/heartpi/blob/master/SS%20Pics/Thinkspeak.png?raw=true" alt="Heart rate Power graph" width="800" height="400"/>
</p>
<h5 align="center"> (d). Heart rate updated live in Thinkspeak Dashboard </h5> <br>


### Access Demo [ThinkSpeak Dashboard](https://thingspeak.com/channels/1076810)

### Project Report

[IoT based Heart Rate measurement system in Raspberry Pi, OpenCV and Thinkspeak dashboard](https://github.com/CoDeRgAnEsh/heartpi/blob/master/IoT_based_Noncontact_Heart_rate_Monitor_system_in_Raspberry_Pi_using_Webcam_MSM17B034.pdf)




## Credits

- [FastICA using CNN](https://github.com/jayantj1j/Heart-rate-estimation-from-video-using-CNN/blob/master/Project%20Report.pdf)
- [Remote Photoplethysmography: Evaluation of Contactless Heart Rate Measurement in an Information Systems Setting](http://air.newcastle.edu.au/AITIC_files/Paper_40.pdf)
- [Using Contactless Heart Rate Measurements for Real-Time Assessment of Affective States](http://link.springer.com/chapter/10.1007/978-3-319-41402-7_20)
- [Remote heart rate measurement using low-cost RGB face video: A technical literature review](https://www.researchgate.net/profile/Raymond_Chiong/publication/306285292_Remote_heart_rate_measurement_using_low-cost_RGB_face_video_A_technical_literature_review/links/58098ac808ae1c98c252637d.pdf)

## Issues

Facing issues, Pour [here](https://github.com/CoDeRgAnEsh/heartpi/issues).

## Contribute

Fixing issues and Upgrade, Pull out [PRs](https://github.com/CoDeRgAnEsh/heartpi/pulls).

## Contact

Mail me [msm17b034@iiitdm.ac.in](mailto:msm17b034@iiitdm.ac.in)
