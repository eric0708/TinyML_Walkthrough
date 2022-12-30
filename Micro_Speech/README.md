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

# Run Application
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
