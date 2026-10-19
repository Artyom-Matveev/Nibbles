### ThumbPad

An ergonomic, grid-based input framework optimized for small screens and one-handed typing. 

### Overview

ThumbPad is a lightweight 3x4 / T9-style keypad layout engine designed for micro-displays and legacy-constrained environments. It provides a structured interface for text input using a limited physical or digital grid, mimicking the deterministic behavior of classic mobile phone keypads. 

### Technical Stack

The core engine and its components are built and compiled using the following environment: 

* **Java 8** (Core application logic and Input Method Editor binding)
* **GCC 14.2.0** (Native JNI components / C backend integration)

### Compatibility & Environment Notice

* **Primary Target:** Developed specifically for **Android 7.1.2** (API Level 25).
* **Testing Status:** Fully tested and verified to be functional on Android 7.1.2.
* **Other Versions:** Compatibility with lower or higher versions of Android (or other GCC/Java toolchains) is **untested and not guaranteed** by the author. Use at your own risk or feel free to submit compatibility reports via Issues.

### Features

* **3x4 Grid Mapping:** Deterministic character cycling based on standard T9 layouts.
* **Low Overhead:** Minimal memory footprint, optimized for constrained devices.
* **Strict Architecture:** Decoupled input logic from the rendering pipeline.

### Repository Structure

├── AndroidManifest.xml   # Android app manifest and IME service declaration
├── src/
│   └── Ime.java          # Core Java implementation of the Input Method Service
├── jni/
│   └── native.c          # Native C backend compiled with GCC
└── res/
    ├── xml/
    │   └── method.xml    # Input method subtype definitions
    └── drawable/
        └── icon.xml      # Keyboard status/launcher icon


### Getting Started

### Prerequisites

* JDK 8
* GCC 14.2.0 (configured within the Android NDK toolchain)
* Android SDK / NDK configured for API Level 25

### Build and Compilation

To compile the native JNI modules using GCC 14.2.0: 

gcc -O2 -shared -fPIC -I${ANDROID_NDK}/sysroot/usr/include jni/native.c -o libthumbpad.so

To compile the Java 8 components and Android IME service: 

javac -source 1.8 -target 1.8 -bootclasspath ${ANDROID_HOME}/platforms/android-25/android.jar -d bin src/Ime.java


### License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file in the repository root for details. 

Copyright (c) 2026 Artyom-Matveev
