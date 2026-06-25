# Keystone and Capstone Libraries for Android

This package contains pre-built static libraries of Keystone and Capstone for Android.

## Architectures

- armeabi-v7a
- arm64-v8a
- x86
- x86_64

## Usage

### In Android Studio / Gradle

1. Copy the `include` and `lib` directories to your project's `app/src/main/cpp/` directory.

2. Update your `app/build.gradle` file to include the architectures:

```gradle
android {
    // ...
    defaultConfig {
        // ...
        ndk {
            abiFilters 'armeabi-v7a', 'arm64-v8a', 'x86', 'x86_64'
        }
    }
}
```

3. Update your `CMakeLists.txt` file:

```cmake
# Add include directories
include_directories(${CMAKE_SOURCE_DIR}/include)

# For Keystone
add_library(keystone STATIC IMPORTED)
set_target_properties(keystone PROPERTIES IMPORTED_LOCATION
    ${CMAKE_SOURCE_DIR}/lib/${ANDROID_ABI}/libkeystone.a)

# For Capstone
add_library(capstone STATIC IMPORTED)
set_target_properties(capstone PROPERTIES IMPORTED_LOCATION
    ${CMAKE_SOURCE_DIR}/lib/${ANDROID_ABI}/libcapstone.a)

# Link your library with Keystone and Capstone
target_link_libraries(your_library keystone capstone)
```

## Credits

by Rodroid Mods by tojik_proof_93

## License

- Keystone: dual license (GPL v2 & commercial license)
- Capstone: BSD license
