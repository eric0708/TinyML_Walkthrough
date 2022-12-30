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
