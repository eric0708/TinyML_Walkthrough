# Train Sine Prediction Model
1. Run the `train_hello_world_model.ipynb` notebook, remember to restart runtime after installing the dependencies
2. Generally the same as the [train_hello_world_model.ipynb](https://github.com/tensorflow/tflite-micro/blob/main/tensorflow/lite/micro/examples/hello_world/train/train_hello_world_model.ipynb) sample notebook
3. Added print model summary functions and deleted the usage of passing the `experimental_op_resolver_type=tf.lite.experimental.OpResolverType.BUILTIN_REF` argument when initializing the TFLite interpreter to avoid errors

# Run Sample Test
1. In terminal, copy and paste 
```
git clone https://github.com/tensorflow/tflite-micro.git
```
2. Requires `make` version to be greater than 3.82, use gmake instead by first running 
```
brew install make
```
3. Go into the `tflite-micro` directory by running 
```
cd tflite-micro
```
4. Run 
```
gmake -f tensorflow/lite/micro/tools/make/Makefile test_hello_world_test
```

# Run Application
1. In terminal, enter the `tflite-micro` directory and run 
```
gmake -f tensorflow/lite/micro/tools/make/Makefile hello_world
```
2. Run the application binary using 
```
gen/osx_arm64_default/bin/hello_world
```

# Deploying to Arduino
1. Download the [Arduino IDE](https://www.arduino.cc/en/software)
2. Open the `Arduino IDE` application
3. Select `Tools -> Manage Libraries` and download `Harvard_TinyMLx` by TinyMLx Authors
4. Select `File -> Examples -> Harvard_TinyMLx -> hello_world` to open up all the sample code files
5. Select `Tools -> Board -> Boards Manager` and download `Arduino Mbed OS Nano Boards` by Arduino
6. Select `Tools -> Board -> Arduino Mbed OS Nano Boards -> Arduino Nano 33 BLE`
7. Select `Tools -> Port` and the corresponding port of the `Arduino Nano 33 BLE`
8. Click the upload button on the Arduino IDE
9. The LED should start to repeatedly fade on and off
10. Adjust the `kInferencesPerCycle` parameter defined in `arduino_constants.cpp` to modify how fast the LED fades
