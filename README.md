# signalflow JUCE

Integrating [signalflow](https://github.com/ideoforms/signalflow) into a [JUCE](https://github.com/juce-framework/JUCE) plugin.


## Build

1. Install CMake (e.g. `brew install cmake` on mac), see [CMake](https://cmake.org).

2. Clone the repo and submodules
```
git clone --recurse-submodules git@github.com:acarabott/signalflow-juce.git
```


2. Build the project. e.g. to build an Xcode project do
```
cd signalflow-juce
cmake -G Xcode . -B ./build-xcode
```

3. Build and run the project

You should get a "Hello World" window and a mono 440hz sine wave in the left channel.
