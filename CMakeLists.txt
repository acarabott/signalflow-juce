cmake_minimum_required(VERSION 3.15)

project(AUDIO_PLUGIN_EXAMPLE VERSION 0.0.1)

set(CMAKE_OSX_ARCHITECTURES "x86_64")

add_subdirectory(./external/JUCE)                    # If you've put JUCE in a subdirectory called JUCE

include_directories(
        ./external/signalflow/source/include
        ./external/signalflow/source/lib
)

juce_add_plugin(AudioPluginExample
        # VERSION ...                               # Set this if the plugin version is different to the project version
        # ICON_BIG ...                              # ICON_* arguments specify a path to an image file to use as an icon for the Standalone
        # ICON_SMALL ...
        # COMPANY_NAME ...                          # Specify the name of the plugin's author
        # IS_SYNTH TRUE/FALSE                       # Is this a synth or an effect?
        # NEEDS_MIDI_INPUT TRUE/FALSE               # Does the plugin need midi input?
        # NEEDS_MIDI_OUTPUT TRUE/FALSE              # Does the plugin need midi output?
        # IS_MIDI_EFFECT TRUE/FALSE                 # Is this plugin a MIDI effect?
        # EDITOR_WANTS_KEYBOARD_FOCUS TRUE/FALSE    # Does the editor need keyboard focus?
        # COPY_PLUGIN_AFTER_BUILD TRUE/FALSE        # Should the plugin be installed to a default location after building?
        PLUGIN_MANUFACTURER_CODE Juce               # A four-character manufacturer id with at least one upper-case character
        PLUGIN_CODE Dem0                            # A unique four-character plugin id with exactly one upper-case character
        # GarageBand 10.3 requires the first letter to be upper-case, and the remaining letters to be lower-case
        FORMATS AU VST3 Standalone                  # The formats to build. Other valid formats are: AAX Unity VST AU AUv3
        PRODUCT_NAME "Audio Plugin Example")        # The name of the final executable, which can differ from the target name


target_sources(AudioPluginExample
        PRIVATE

        ./external/signalflow/source/src/buffer/buffer.cpp
        ./external/signalflow/source/src/buffer/buffer2d.cpp
        ./external/signalflow/source/src/core/config.cpp
        ./external/signalflow/source/src/core/core.cpp
        ./external/signalflow/source/src/core/graph-monitor.cpp
        ./external/signalflow/source/src/core/graph.cpp
        ./external/signalflow/source/src/core/random.cpp
        ./external/signalflow/source/src/core/renderer.cpp
        ./external/signalflow/source/src/core/util.cpp
        ./external/signalflow/source/src/node/analysis/cross-correlate.cpp
        ./external/signalflow/source/src/node/analysis/onset-detector.cpp
        ./external/signalflow/source/src/node/analysis/vamp.cpp
        ./external/signalflow/source/src/node/buffer/beat-cutter.cpp
        ./external/signalflow/source/src/node/buffer/buffer-looper.cpp
        ./external/signalflow/source/src/node/buffer/buffer-player.cpp
        ./external/signalflow/source/src/node/buffer/buffer-recorder.cpp
        ./external/signalflow/source/src/node/buffer/feedback-buffer-reader.cpp
        ./external/signalflow/source/src/node/buffer/feedback-buffer-writer.cpp
        ./external/signalflow/source/src/node/buffer/grainsegments.cpp
        ./external/signalflow/source/src/node/buffer/granulator.cpp
        ./external/signalflow/source/src/node/buffer/segment-player.cpp
        ./external/signalflow/source/src/node/envelope/adsr.cpp
        ./external/signalflow/source/src/node/envelope/asr.cpp
        ./external/signalflow/source/src/node/envelope/detect-silence.cpp
        ./external/signalflow/source/src/node/envelope/envelope.cpp
        ./external/signalflow/source/src/node/envelope/line.cpp
        ./external/signalflow/source/src/node/envelope/rect.cpp
        ./external/signalflow/source/src/node/fft/continuous-pv.cpp
        ./external/signalflow/source/src/node/fft/convolve.cpp
        ./external/signalflow/source/src/node/fft/fft.cpp
        ./external/signalflow/source/src/node/fft/fftnode.cpp
        ./external/signalflow/source/src/node/fft/find-peaks.cpp
        ./external/signalflow/source/src/node/fft/ifft.cpp
        ./external/signalflow/source/src/node/fft/lpf.cpp
        ./external/signalflow/source/src/node/fft/noise-gate.cpp
        ./external/signalflow/source/src/node/fft/phase-vocoder.cpp
        ./external/signalflow/source/src/node/fft/tonality.cpp
        ./external/signalflow/source/src/node/io/input/abstract.cpp
        ./external/signalflow/source/src/node/io/input/soundio.cpp
        ./external/signalflow/source/src/node/io/output/abstract.cpp
        ./external/signalflow/source/src/node/io/output/dummy.cpp
        ./external/signalflow/source/src/node/io/output/soundio.cpp
        external/signalflow/source/src/node/io/output/juce.cpp
        ./external/signalflow/source/src/node/node-monitor.cpp
        ./external/signalflow/source/src/node/node.cpp
        ./external/signalflow/source/src/node/operators/add.cpp
        ./external/signalflow/source/src/node/operators/amplitude-to-decibels.cpp
        ./external/signalflow/source/src/node/operators/channel-array.cpp
        ./external/signalflow/source/src/node/operators/channel-mixer.cpp
        ./external/signalflow/source/src/node/operators/channel-select.cpp
        ./external/signalflow/source/src/node/operators/comparison.cpp
        ./external/signalflow/source/src/node/operators/divide.cpp
        ./external/signalflow/source/src/node/operators/frequency-to-midi-note.cpp
        ./external/signalflow/source/src/node/operators/midi-note-to-frequency.cpp
        ./external/signalflow/source/src/node/operators/multiply.cpp
        ./external/signalflow/source/src/node/operators/pow.cpp
        ./external/signalflow/source/src/node/operators/round-to-scale.cpp
        ./external/signalflow/source/src/node/operators/round.cpp
        ./external/signalflow/source/src/node/operators/scale.cpp
        ./external/signalflow/source/src/node/operators/subtract.cpp
        ./external/signalflow/source/src/node/operators/sum.cpp
        ./external/signalflow/source/src/node/operators/trigonometry.cpp
        ./external/signalflow/source/src/node/oscillators/constant.cpp
        ./external/signalflow/source/src/node/oscillators/impulse.cpp
        ./external/signalflow/source/src/node/oscillators/lfo.cpp
        ./external/signalflow/source/src/node/oscillators/saw-lfo.cpp
        ./external/signalflow/source/src/node/oscillators/saw.cpp
        ./external/signalflow/source/src/node/oscillators/sine-lfo.cpp
        ./external/signalflow/source/src/node/oscillators/sine.cpp
        ./external/signalflow/source/src/node/oscillators/square-lfo.cpp
        ./external/signalflow/source/src/node/oscillators/square.cpp
        ./external/signalflow/source/src/node/oscillators/triangle-lfo.cpp
        ./external/signalflow/source/src/node/oscillators/triangle.cpp
        ./external/signalflow/source/src/node/oscillators/wavetable.cpp
        ./external/signalflow/source/src/node/processors/clip.cpp
        ./external/signalflow/source/src/node/processors/delays/allpass.cpp
        ./external/signalflow/source/src/node/processors/delays/comb.cpp
        ./external/signalflow/source/src/node/processors/delays/onetap.cpp
        ./external/signalflow/source/src/node/processors/delays/stutter.cpp
        ./external/signalflow/source/src/node/processors/distortion/resample.cpp
        ./external/signalflow/source/src/node/processors/distortion/sample-and-hold.cpp
        ./external/signalflow/source/src/node/processors/distortion/squiz.cpp
        ./external/signalflow/source/src/node/processors/distortion/waveshaper.cpp
        ./external/signalflow/source/src/node/processors/dynamics/compressor.cpp
        ./external/signalflow/source/src/node/processors/dynamics/gate.cpp
        ./external/signalflow/source/src/node/processors/dynamics/maximiser.cpp
        ./external/signalflow/source/src/node/processors/dynamics/rms.cpp
        ./external/signalflow/source/src/node/processors/filters/biquad.cpp
        ./external/signalflow/source/src/node/processors/filters/eq.cpp
        ./external/signalflow/source/src/node/processors/filters/moog.cpp
        ./external/signalflow/source/src/node/processors/filters/svf.cpp
        ./external/signalflow/source/src/node/processors/fold.cpp
        ./external/signalflow/source/src/node/processors/panning/azimuth-panner.cpp
        ./external/signalflow/source/src/node/processors/panning/channel-panner.cpp
        ./external/signalflow/source/src/node/processors/panning/spatial-environment.cpp
        ./external/signalflow/source/src/node/processors/panning/stereo-balance.cpp
        ./external/signalflow/source/src/node/processors/panning/stereo-panner.cpp
        ./external/signalflow/source/src/node/processors/panning/stereo-width.cpp
        ./external/signalflow/source/src/node/processors/smooth.cpp
        ./external/signalflow/source/src/node/processors/wetdry.cpp
        ./external/signalflow/source/src/node/processors/wrap.cpp
        ./external/signalflow/source/src/node/registry.cpp
        ./external/signalflow/source/src/node/sequencing/clock-divider.cpp
        ./external/signalflow/source/src/node/sequencing/counter.cpp
        ./external/signalflow/source/src/node/sequencing/euclidean.cpp
        ./external/signalflow/source/src/node/sequencing/flipflop.cpp
        ./external/signalflow/source/src/node/sequencing/impulse-sequence.cpp
        ./external/signalflow/source/src/node/sequencing/index.cpp
        ./external/signalflow/source/src/node/sequencing/latch.cpp
        ./external/signalflow/source/src/node/sequencing/sequence.cpp
        ./external/signalflow/source/src/node/stochastic/logistic.cpp
        ./external/signalflow/source/src/node/stochastic/pink-noise.cpp
        ./external/signalflow/source/src/node/stochastic/random-brownian.cpp
        ./external/signalflow/source/src/node/stochastic/random-choice.cpp
        ./external/signalflow/source/src/node/stochastic/random-coin.cpp
        ./external/signalflow/source/src/node/stochastic/random-exponential-dist.cpp
        ./external/signalflow/source/src/node/stochastic/random-exponential.cpp
        ./external/signalflow/source/src/node/stochastic/random-gaussian.cpp
        ./external/signalflow/source/src/node/stochastic/random-impulse-sequence.cpp
        ./external/signalflow/source/src/node/stochastic/random-impulse.cpp
        ./external/signalflow/source/src/node/stochastic/random-uniform.cpp
        ./external/signalflow/source/src/node/stochastic/stochastic-node.cpp
        ./external/signalflow/source/src/node/stochastic/white-noise.cpp
        ./external/signalflow/source/src/patch/patch-node-spec.cpp
        ./external/signalflow/source/src/patch/patch-registry.cpp
        ./external/signalflow/source/src/patch/patch-spec.cpp
        ./external/signalflow/source/src/patch/patch.cpp
        ./external/signalflow/source/lib/json11/json11.cpp



        ./src/PluginEditor.cpp
        ./src/PluginProcessor.cpp)

target_compile_definitions(AudioPluginExample
        PUBLIC
        # JUCE_WEB_BROWSER and JUCE_USE_CURL would be on by default, but you might not need them.
        JUCE_WEB_BROWSER=0  # If you remove this, add `NEEDS_WEB_BROWSER TRUE` to the `juce_add_plugin` call
        JUCE_USE_CURL=0     # If you remove this, add `NEEDS_CURL TRUE` to the `juce_add_plugin` call
        JUCE_VST3_CAN_REPLACE_VST2=0)

# If your target needs extra binary assets, you can add them here. The first argument is the name of
# a new static library target that will include all the binary resources. There is an optional
# `NAMESPACE` argument that can specify the namespace of the generated binary data class. Finally,
# the SOURCES argument should be followed by a list of source files that should be built into the
# static library. These source files can be of any kind (wav data, images, fonts, icons etc.).
# Conversion to binary-data will happen when your target is built.

# juce_add_binary_data(AudioPluginData SOURCES ...)

target_link_libraries(AudioPluginExample
        PRIVATE
        # AudioPluginData           # If we'd created a binary data target, we'd link to it here
        juce::juce_audio_utils
        PUBLIC
        juce::juce_recommended_config_flags
        juce::juce_recommended_lto_flags
        juce::juce_recommended_warning_flags)
