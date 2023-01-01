# Wake-Word Detection

## Task Overview
Train and deploy a model that reacts accordingly upon the detection of wake-words("yes" or "no" in this example)

## Train Speech Recognition Model
1. Run the `train_micro_speech_model.ipynb` notebook
2. Generally the same as the [train_micro_speech_model.ipynb](https://github.com/tensorflow/tflite-micro/blob/main/tensorflow/lite/micro/examples/micro_speech/train/train_micro_speech_model.ipynb) sample notebook provided by TensorFlow
3. Modifications include modifying the notebook in order for it to run without errors in a tensorflow 2.x environment instead of 1.x
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
4. Run the following command to test the micro speech model
```
gmake -f tensorflow/lite/micro/tools/make/Makefile test_micro_speech_test
```
5. Run the following command to test the audio provider
```
gmake -f tensorflow/lite/micro/tools/make/Makefile test_audio_provider_test
```
6. Run the following command to test the feature provider
```
gmake -f tensorflow/lite/micro/tools/make/Makefile test_feature_provider_mock_test
```
7. Run the following command to test the command recognizer
```
gmake -f tensorflow/lite/micro/tools/make/Makefile test_recognize_commands_test
```
8. Run the following command to test the command responder
```
gmake -f tensorflow/lite/micro/tools/make/Makefile test_command_responder_test
```

## Run Application
1. Change the `audio_provider.cc` file with the one provided in this directory, which enables the application to run for MacOS
2. Copy the following code snippet into the end of `Makefile.inc`
```
ifeq ($(TARGET), osx)
  LINKER_FLAGS := \
    -framework Foundation \
    -framework AudioToolbox

  MICROLITE_LIBS += $(LINKER_FLAGS)
  MICRO_SPEECH_HDRS += tensorflow/lite/micro/examples/micro_speech/simple_features/simple_model_settings.h
endif
```
3. In terminal, enter the `tflite-micro` directory and run 
```
gmake -f tensorflow/lite/micro/tools/make/Makefile micro_speech
```
4. Run the application binary using 
```
gen/osx_arm64_default/bin/micro_speech
```
5. The output window should indicate when "yes" or "no" is spoken, or show that the sound is "silence" or "unknown"

## Deploying to Arduino
1. Download the [Arduino IDE](https://www.arduino.cc/en/software)
2. Open the `Arduino IDE` application
3. Select `Tools -> Manage Libraries` and download `Harvard_TinyMLx` version 1.2.3-Alpha by TinyMLx Authors
4. Select `File -> Examples -> Harvard_TinyMLx -> micro_speech` to open up all the sample code files
5. Connect `ARDUINO Nano 33 BLE Sense Lite` to the computer using USB Cable
6. Select `Tools -> Board -> Boards Manager` and download `Arduino Mbed OS Nano Boards` by Arduino
7. Select `Tools -> Board -> Arduino Mbed OS Nano Boards -> Arduino Nano 33 BLE`
8. Select `Tools -> Port` and the corresponding port of the `Arduino Nano 33 BLE`
9. Click the upload button indicated by a right arrow on the upper left corner in the `Arduino IDE`
10. The LED should start to repeatedly flash on and off, indicating it is inferencing
11. The RGB LEDs will light up accordingly to input sounds, green for "yes", red for "no", and blue for "unknown"
