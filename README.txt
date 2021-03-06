Superpowered Audio Engine for Games, Music and Interactive Audio Apps on Android, iOS & OSX.

Low Latency Audio. Cross Platform. Free.
What is it?-----------The Superpowered Audio SDK is a software development kit based on Superpowered Inc�s digital signal processing (DSP) technology. Superpowered technology allows developers to build computationally intensive audio apps and embedded applications that process more quickly and use less power than other comparable solutions. Superpowered DSP is designed and optimized, from scratch, to run on low-power mobile processors. Specifically, any device running ARM with the NEON extension (which covers 99% of all mobile devices manufactured). Intel CPU is supported too.PLEASE NOTE: all example codes working with the Superpowered features are cross-platform, can be used under iOS and Android.
Folders-------
/SuperpoweredThe SDK itself (static library and headers).

docs
The documentation. Start with index.html.


/SuperpoweredCrossExample (iOS)A fully-functional DJ app project example. Shows how to:

- Set up two players.
- Sync them together.
- Apply some effects on the master mix.
- Use Objective-C++.


/SuperpoweredFrequencies (iOS)
Simple 8-band frequency analyzer. Shows how to:

- Mix Swift and Objective-C++ in a project.
- Use the SuperpoweredBandpassFilterbank.


/SuperpoweredFrequencyDomain (iOS)
Simple time domain to frequency domain transformation with buffering and windowing. Shows how to:

- Use the SuperpoweredFrequencyDomain class.
- Process the magnitudes and phases of the audio input./SuperpoweredPerformance (iOS)It compares several Superpowered features to Core Audio.

- Shows the differences between Superpowered and Core Audio.
- Syncs effects to the player�s bpm.
- Shows how to use Objective-C++ in an Objective-C project.

Swift note:
We have also tried creating this project in Swift, but it�s not complete for audio and several features were impossible to implement (such as proper performance measurement). Swift is not designed for real-time audio. Fortunately, Objective-C++ files work great in Swift projects.

/SuperpoweredOfflineProcessingExample
Advanced example. Decodes an audio file, applies time stretching and saves the result in WAV. Shows how to:

- Set up the SuperpoweredDecoder.
- Use the time stretcher with an efficient dynamic memory pool.
- Save the result in WAV.

/Android/CrossExample (Android)
- Android NDK sample project, similar to SuperpoweredCrossExample.
- Also shows how to use SuperpoweredAndroidAudioIO for output only.


/Android/FrequencyDomain
- Android NDK sample project, similar to SuperpoweredFrequencyDomain.
- Shows how to use SuperpoweredAndroidAudioIO for audio input and output.


Android Studio
--------------

NDK integration with static libraries is still incomplete in Android Studio. Before running the example, please set up the following:

- Open local.properties. Set ndk.dir to your ndk folder.
- Open build.gradle under the app folder. Check for ndk-build, and set the appropriate path again.


How to create a Superpowered project with Android Studio
--------------------------------------------------------

Prerequisites: latest Android SDK, Android NDK, Android Studio installed
Steps:
1. create a new project in Android Studio
2. create the jni folder inside the project�s folder: app/src/main/jni
3. open local.properties, set ndk.dir= to your NDK folder (for example: ndk.dir=/android/ndk)
4. open build.gradle (module: app), add sourceSets.main, task ndkBuild and tasks.withType like this:

    defaultConfig {
        applicationId "com.superpowered.crossexample"
        minSdkVersion 11
        targetSdkVersion 21
        versionCode 1
        versionName "1.0"

        sourceSets.main {
            jniLibs.srcDir 'src/main/libs'
            //jni.srcDirs = []
        }
    }

    task ndkBuild(type: Exec) {
        commandLine '/android/ndk/ndk-build', '-B', '-C', file('src/main/jni').absolutePath
    }
    tasks.withType(JavaCompile) {
        compileTask -> compileTask.dependsOn ndkBuild
    }
5. the jni folder appears as �c� under app in Android Studio
6. copy Android.mk, Application.mk and the libSuperpowered.a files into the jni folder you created at step 2, from a similar folder in one of our example projects
7. create your custom .cpp and .h files, then don�t forget to properly set LOCAL_MODULE and LOCAL_SRC_FILES in Android.mk
8. before compiling the project, uncomment the line: jni.srcDirs = []
9. comment the line to make the �c� folder reappear again
The Latest Version 
------------------Details of the latest version can be found at http://superpowered.com/superpowered-audio-sdk/Pricing and licensing
---------
The Superpowered Audio SDK is free for software applications. Please see the file called license.pdf.

Superpowered FFT benefits from ideas in Construction of a High-Performance FFT by Eric Postpischil (http://edp.org/resume.htm).


Contacts
--------

If you want to be informed about new code releases, bug fixes, general news and information about Superpowered, please email hello@superpowered.com.
