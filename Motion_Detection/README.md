# Run Sample Test
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
4. Run the following command to test the motion detection model
```
gmake -f tensorflow/lite/micro/tools/make/Makefile test_magic_wand_test
```
5. Run the following command to test the accelerometer handler
```
gmake -f tensorflow/lite/micro/tools/make/Makefile test_gesture_accelerometer_handler_test
```
6. Run the following command to test the gesture predictor
```
gmake -f tensorflow/lite/micro/tools/make/Makefile test_gesture_predictor_test
```
7. Run the following command to test the output handler
```
gmake -f tensorflow/lite/micro/tools/make/Makefile test_gesture_output_handler_test
```

# Run Application
1. In terminal, enter the `tflite-micro` directory and run 
```
gmake -f tensorflow/lite/micro/tools/make/Makefile magic_wand
```
2. Run the application binary using 
```
gen/osx_arm64_default/bin/magic_wand
```
3. There will not be any output since there is no accelerometer data available

# Deploying to Arduino
1. Download the [Arduino IDE](https://www.arduino.cc/en/software)
2. Open the `Arduino IDE` application
3. Select `Tools -> Manage Libraries` and download `Harvard_TinyMLx` by TinyMLx Authors
4. Select `File -> Examples -> Harvard_TinyMLx -> magic_wand` to open up all the sample code files
5. Select `Tools -> Manage Libraries` from `Arduino IDE` to search for and download the `Arduino_LSM9DS1` library version 1.0.0 by Arduino

9. Open `Arduino/libraries/JPEGDecoder/src/User_Config.h` and comment out `#define LOAD_SD_LIBRARY` and `#define LOAD_SDFAT_LIBRARY`
10. Assemble `ARDUINO Nano 33 BLE Sense Lite` and `OV7675 Camera Module` onto `Tiny Machine Learning Shield` and connect to computer using USB Cable
11. Select `Tools -> Board -> Boards Manager` and download `Arduino Mbed OS Nano Boards` by Arduino
12. Select `Tools -> Board -> Arduino Mbed OS Nano Boards -> Arduino Nano 33 BLE`
13. Select `Tools -> Port` and the corresponding port of the `Arduino Nano 33 BLE`
14. Click the upload button indicated by a right arrow on the upper left corner in the `Arduino IDE`
15. The Blue LED should start to repeatedly flash on and off, indicating it is inferencing
16. The Red and Green LEDs should flash on and off according to the inference results, red for no person detected and green for person detected

