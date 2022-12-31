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
5. Select `Tools -> Manage Libraries` from `Arduino IDE` to search for and download the `Arduino_LSM9DS1` library version 1.1.1 by Arduino
6. Open `Arduino/libraries/Arduino_LSM9DS1/src/LSM9DS1.cpp`, go to the function `LSM9DS1Class::begin()` and add the following line at the end of the function, right before the `return 1` statement
```
writeRegister(LSM9DS1_ADDRESS, 0x2e, 0xc0); // Set continuous mode
```
Next, go to the function `LSM9DS1Class::accelerationAvailable()` and comment out the following lines
```
if (readRegister(LSM9DS1_ADDRESS, LSM9DS1_STATUS_REG) & 0x01) {
  return 1;
}
```
Replace the above lines with the following
```
// Read FIFO_SRC. If any of the rightmost 8 bits have a value, there is data.
if (readRegister(LSM9DS1_ADDRESS, 0x2f) & 63) {
  return 1;
}
```
7. Select `Tools -> Manage Libraries` from `Arduino IDE` to search for and download the `ArduinoBLE` library version 1.3.2 by Arduino
8. Connect `ARDUINO Nano 33 BLE Sense Lite` to the computer using USB Cable
9. Select `Tools -> Board -> Boards Manager` and download `Arduino Mbed OS Nano Boards` by Arduino
10. Select `Tools -> Board -> Arduino Mbed OS Nano Boards -> Arduino Nano 33 BLE`
11. Select `Tools -> Port` and the corresponding port of the `Arduino Nano 33 BLE`
12. Click the upload button indicated by a right arrow on the upper left corner in the `Arduino IDE`
13. Hold the `ARDUINO Nano 33 BLE Sense Lite` by the USB with all the elements facing up and start writing numbers in the air
14. The Serial Monitor will output correspondingly when a number is written
