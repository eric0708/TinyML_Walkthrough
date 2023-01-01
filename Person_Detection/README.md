# Person Detection

## Task Overview
Deploy a pretrained person detection model and act accordingly to the inference results

## Train Person Detection Model
The model used in the following processes is a provided pretrained model since the training of the model requires more training time and resources

## Run Sample Test
1. In terminal, copy and paste 
```
git clone https://github.com/tensorflow/tflite-micro.git
```
2. Requires `make` version to be greater than 3.82, use `gmake` instead by first running 
```
brew install make
```
3. Go into the `tflite-micro` directory by running 
```
cd tflite-micro
```
4. Run the following command to test the person detection model
```
gmake -f tensorflow/lite/micro/tools/make/Makefile test_person_detection_test
```
5. Run the following command to test the image provider
```
gmake -f tensorflow/lite/micro/tools/make/Makefile test_image_provider_test
```
6. Run the following command to test the detection responder
```
gmake -f tensorflow/lite/micro/tools/make/Makefile test_detection_responder_test
```

## Run Application
1. In terminal, enter the `tflite-micro` directory and run 
```
gmake -f tensorflow/lite/micro/tools/make/Makefile person_detection
```
2. Run the application binary using 
```
gen/osx_arm64_default/bin/person_detection
```
3. The output will be constant since the default `image_provider.cc` just returns dummy data


## Deploying to Arduino
1. Download the [Arduino IDE](https://www.arduino.cc/en/software)
2. Open the `Arduino IDE` application
3. Select `Tools -> Manage Libraries` and download `Harvard_TinyMLx` version 1.2.3-Alpha by TinyMLx Authors
4. Select `File -> Examples -> Harvard_TinyMLx -> person_detection` to open up all the sample code files
5. Run the following command to download the `Arducam Arduino library` from GitHub
```
git clone https://github.com/ArduCAM/Arduino.git
```
6. Copy the ArduCAM directory into the `Arduino/libraries` directory in the computer, whose location can be found through the `Sketchbook location` listed in `Arduino IDE -> Preferences`
7. Open `Arduino/libraries/ArduCAM/memorysaver.h` and comment out all `#define` statements except for `#define ARDUCAM_SHIELD_REVC` and `#define OV7675_CAM`
8. Select `Tools -> Manage Libraries` from `Arduino IDE` to search for and download the `JPEGDecoder` library version 1.8.0
9. Open `Arduino/libraries/JPEGDecoder/src/User_Config.h` and comment out `#define LOAD_SD_LIBRARY` and `#define LOAD_SDFAT_LIBRARY`
10. Assemble `ARDUINO Nano 33 BLE Sense Lite` and `OV7675 Camera Module` onto `Tiny Machine Learning Shield` and connect to computer using USB Cable
11. Select `Tools -> Board -> Boards Manager` and download `Arduino Mbed OS Nano Boards` by Arduino
12. Select `Tools -> Board -> Arduino Mbed OS Nano Boards -> Arduino Nano 33 BLE`
13. Select `Tools -> Port` and the corresponding port of the `Arduino Nano 33 BLE`
14. Click the upload button indicated by a right arrow on the upper left corner in the `Arduino IDE`
15. The Blue LED should start to repeatedly flash on and off, indicating it is inferencing
16. The Red and Green LEDs should flash on and off according to the inference results, red for no person detected and green for person detected
