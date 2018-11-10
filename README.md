# Compile android common branch with clang
RecenRecently I need to use clang to compile android kernel, it takes time to figure out the compiable one. Here's the step of my first success.

Step 1: Download ndk from the follwoing link and unzip it(Platform: ubuntu 18.04.1 LTS):
```
https://developer.android.com/ndk/downloads/
```
Step 2: Download android kernel source code from Google repo, this is the one I used:
```
git clone https://android.googlesource.com/kernel/common
```

Step 3:Pick a branch, I compile this one:
```
git checkout android-4.9
```
Step 4: Set up the environment variable, those are what I use:
```
export ARCH=arm64
export CROSS_COMPILE=/dir/to/ndk/toolchains/aarch64-linux-android-4.9/prebuilt/linux-x86_64/bin/aarch64-linux-android-
```
Step 5: Begin to compile:
```
make ranchu64_defconfig
make -j$(nproc --all) CC=dir/to/ndk/toolchains/llvm/prebuilt/linux-x86_64/bin/clang \
                      CLANG_TRIPLE=aarch64-linux-gnu-
```
