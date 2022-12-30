# Run Sample Test
1. In terminal, copy and paste `git clone https://github.com/tensorflow/tflite-micro.git`
2. Requires "make" version to be greater than 3.82, run `brew install make` and use gmake instead
3. Go into the "tflite-micro" directory by running `cd tflite-micro`
4. Run `gmake -f tensorflow/lite/micro/tools/make/Makefile test_hello_world_test`

# Run Application
1. In terminal, run `gmake -f tensorflow/lite/micro/tools/make/Makefile hello_world` from the "tflite-micro" directory
2. Run the application binary using `gen/osx_arm64_default/bin/hello_world`

# Deploying to Arduino
1. Download the [Arduino IDE](https://www.arduino.cc/en/software)
2. Select "Tools" -> "Manage Libraries" and download "Harvard_TinyMLx" by TinyMLx Authors
3. Select "File" -> "Examples" -> "Harvard_TinyMLx" -> "hello_world" to open up all the sample code files
4. Select "Tools" -> "Board" -> "Boards Manager" and download "Arduino Mbed OS Nano Boards" by Arduino
5. Select "Tools" -> "Board" -> "Arduino Mbed OS Nano Boards" -> "Arduino Nano 33 BLE"
6. Select "Tools" -> "Port" and the corresponding port of the "Arduino Nano 33 BLE"
7. Click the upload button on the Arduino IDE
8. The LED should start to repeatedly fade on and off
9. Adjust the "kInferencesPerCycle" parameter defined in "arduino_constants.cpp" to modify how fast the LED fades
