# About this Fork
I used Jucer version 8.0.10 with Visual Studio Community Edition 2022 version 17.14.17 on Windows 11 Home. I tried to prepare a project to support more plugin formats and audio drivers on Windows, to update the code for use with the latest versions (as of October 2025) of Juce and Visual Studio and to do some small code optimization to reduce the warnings: i didn't complete the optimization work however i reduced the warnings from over 200 to about 31 at least on my system. The modified code is in the files in the Source folder and in the "Files-To-Replace" folder whose files will replace the files of the same name in the various directories (see the "Read-this.txt" file). Jucer is ready to build plugins in VST2, VST3, LV2, AAX, and standalone formats with ASIO and Jack4Win support (the fork is for Windows). Remember to check the directories in the Jucer project file, especially those in the global path relating to the AAX, VST-2.4, Asio and Jack SDKs (the latter must be installed on your system). Please note that VST2 plugins require the Steinberg license. The AAX plugin cannot be used unless it is first activated/authorized following a specific procedure established by Avid, which requires - among other things - Avid and PACE/iLok accounts and the use of tools such as AAX Validator, Pro Tools Developer Bundle, PACE Eden Signing Tools, etc. 

# Original Readme:

# Curvessor 2

![Curvessor GUI](Images/screenshot.jpg?raw=true 'screenshot')

[Curvessor](https://www.unevens.net/curvessor.html) is an audio plug-in that implements a dynamic range processor in which **the response curve of each channel is an automatable spline**.

Curvessor can be used as a classic compressor/expander, enjoying the freedom and precision that comes with spline editing.

But more specifically, as it allows the authoring of response curves _that are not increasing_, Curvessor can be used for creative dynamic range processing in sound design.

## Features

- The response curves are smoothly automatable splines.
- Optional Mid/Side Stereo processing.
- Forward, Feedback and Sidechain topologies. 
- The amount of feedback can be smoothly changed, going from pure forward topology to pure feedback topology and everything in between. _(NEW in verison 2)_
- Optional RMS and high-pass filtering on the level detector _(NEW in verison 2)_
- All parameters, and all splines, can have different values on the Left channel and on the Right channel - or on the Mid channel and on the Side channel, when in Mid/Side Stero Mode.
- Dry-Wet.
- Up to 32x Oversampling with either Minimum Phase or Linear Phase Antialiasing.
- VU meter showing the difference between the input level and the output level.
- Customizable smoothing time, used to avoid zips when automating the knots of the splines, the stereo link percentage, the wet amount, or the input and output gains.

## Build

Clone with

`git clone --recursive https://github.com/unevens/Curvessor`

Curvessor uses the [JUCE](https://github.com/WeAreROLI/JUCE) cross-platform C++ framework.

You'll need [Projucer](https://shop.juce.com/get-juce) to open the file `Curvessor.jucer` and generate the platform specific builds.

## Supported platforms

Curvessor is developed and tested on Windows and Linux. It may also work on macOS, but I can neither confirm nor deny.

VST and VST3 binaries are available at https://www.unevens.net/curvessor.html.

## Submodules, libraries, credits

- The [oversimple](https://github.com/unevens/oversimple) submodule is a wrapper around two resampling libraries:
    - [HIIR](https://github.com/unevens/hiir) by Laurent de Soras, *"a 2x Upsampler/Downsampler with two-path polyphase IIR anti-aliasing filtering"*.
    - [r8brain-free-src](https://github.com/avaneev/r8brain-free-src), *"an high-quality pro audio sample rate converter / resampler C++ library"* by Aleksey Vaneev.
- [audio-dsp](https://github.com/unevens/audio-dsp), my toolbox for audio dsp and SIMD instructions, which uses Agner Fog's [vectorclass](https://github.com/vectorclass/version2) and [Boost.Align](https://www.boost.org/doc/libs/1_71_0/doc/html/align.html).
- [gamma-env](https://github.com/avaneev/gammaenv): *"DSP S-curve envelope signal generator"*, by Aleksey Vaneev. Curvessor uses a SIMD optimized version of gammaenv that I wrote specifically for it. See the files `audio-dsp/adsp/GammaEnv.hpp` and `audio-dsp/adsp/GammaEnvMacro.hpp`.

Curvessor is released under the GNU GPLv3 license.

VST is a trademark of Steinberg Media Technologies GmbH, registered in Europe and other countries.


## Version 1

For version 1, see the branch `version-1`.
