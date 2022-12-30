# Run Sample Test
1. In terminal, copy and paste `git clone https://github.com/tensorflow/tflite-micro.git`
2. Requires make version to be greater than 3.82, run `brew install make` and use gmake instead
3. Go into the "tflite-micro" directory by running `cd tflite-micro`
4. Run `gmake -f tensorflow/lite/micro/tools/make/Makefile test_hello_world_test`

# Run Application
1. In terminal, run `gmake -f tensorflow/lite/micro/tools/make/Makefile hello_world`
2. Run the application binary using `gen/osx_arm64_default/bin/hello_world`
