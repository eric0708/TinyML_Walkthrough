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
