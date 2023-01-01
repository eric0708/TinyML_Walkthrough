# The "Hello World" of TinyML

## Task Overview
Train and deploy a model that is capable of predicting the sine values of inputs and changes the brightness of an LED according to the output values

## Train Sine Prediction Model
1. Run the `train_hello_world_model.ipynb` notebook, remember to restart runtime after installing the dependencies
2. Generally the same as the [train_hello_world_model.ipynb](https://github.com/tensorflow/tflite-micro/blob/main/tensorflow/lite/micro/examples/hello_world/train/train_hello_world_model.ipynb) sample notebook provided by TensorFlow
3. Modifications include adding print model summary functions and deleting the usage of passing the `experimental_op_resolver_type=tf.lite.experimental.OpResolverType.BUILTIN_REF` argument when initializing the TFLite interpreter to avoid errors
4. Creates a `model.cc` file that can be used to replace the ones used in the following sections

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
4. Run the command
```
gmake -f tensorflow/lite/micro/tools/make/Makefile test_hello_world_test
```

## Run Application
1. In terminal, enter the `tflite-micro` directory and run 
```
gmake -f tensorflow/lite/micro/tools/make/Makefile hello_world
```
2. Run the application binary using 
```
gen/osx_arm64_default/bin/hello_world
```

## Deploying to Arduino
1. Download the [Arduino IDE](https://www.arduino.cc/en/software)
2. Open the `Arduino IDE` application
3. Select `Tools -> Manage Libraries` and download `Harvard_TinyMLx` version 1.2.3-Alpha by TinyMLx Authors
4. Select `File -> Examples -> Harvard_TinyMLx -> hello_world` to open up all the sample code files
5. Select `Tools -> Board -> Boards Manager` and download `Arduino Mbed OS Nano Boards` by Arduino
6. Select `Tools -> Board -> Arduino Mbed OS Nano Boards -> Arduino Nano 33 BLE`
7. Select `Tools -> Port` and the corresponding port of the `Arduino Nano 33 BLE`
8. Click the upload button indicated by a right arrow on the upper left corner in the `Arduino IDE`
9. The LED should start to repeatedly fade on and off
10. Adjust the `kInferencesPerCycle` parameter defined in `arduino_constants.cpp` to modify how fast the LED fades
