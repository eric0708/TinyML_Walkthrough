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

# Run Application
1. In terminal, enter the `tflite-micro` directory and run 
```
gmake -f tensorflow/lite/micro/tools/make/Makefile person_detection
```
2. Run the application binary using 
```
gen/osx_arm64_default/bin/person_detection
```
3. The output will be constant since the default `image_provider.cc` just returns dummy data
