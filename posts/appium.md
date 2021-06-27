---
title: appium
description: appium
date: 2021-06-24
tags:
  - appium
layout: layouts/post.njk
image: https://cdn.pixabay.com/photo/2020/08/30/20/54/rice-field-5530707_1280.jpg
---
## Setup
* Appium
  * ```$ brew install appium --cask```
  * ```$ npm i -g appium```
* Java
  1. 安裝openjdk 
      ```$ brew install java```
  2. 增加以下兩項至 ~/.config/fish/conf.d/baymo.fish (筆者慣用fish shell)
      * 新增PATH
      ```fish_add_path /opt/homebrew/opt/openjdk/bin```
      * 新增環境變數 
      ```set -x JAVA_HOME "/opt/homebrew/opt/openjdk/libexec/openjdk.jdk/Contents/Home"```
* Android Studio
  1. 安裝
      * ```$ brew install android-studio --cask```
      * for Mac M1
          ```$ brew install android-studio-preview-canary --cask```
  1. 新增環境變數
      ```set -x ANDROID_HOME "/Users/baymo/Library/Android/sdk"```
  1. 安裝模擬器
        * Open the AVD manager
            ![open avd](/img/android-emulator/open-avd.png "open the AVD manager")
        * Create virtual device
            ![create](/img/android-emulator/create.png "create")
        * 選一個有Play Store的 (其它為root，會導致App無法正常使用)
            ![choose](/img/android-emulator/choose.png "choose one with Play Store")
        * Download R， (S會導致Appium的inspector無法正常顯示)
            Mac M1，ABI需為arm64-v8a
            ![download](/img/android-emulator/download.png "R download")
        * 慢慢等
            ![downloading](/img/android-emulator/downloading.png "downloading")
        * 載完後選R
            ![image](/img/android-emulator/choose-image.png "image")
        * 都不用改，直接Finish
            ![finish](/img/android-emulator/finish.png "finish")

## Get Started
### Inspect layout hierarchy
1. Launch appium server
  ```$ appium```
1. Launch appium GUI client
    ![appium app](/img/appium/appium-app.png "appium app")
1. New Session Window
    剛剛的1.已用command line啟動server，這裡不用再Start Server，只要建client session就好
    ![new session](/img/appium/launch.png "new session")
1. 填好config，Start Session
    ![config](/img/appium/config.png "config")
  * appPackage: play store url的id
       ![scb play store](/img/appium/scb-play-store.png "scb play store")
  * automationName: UiAutomator2
  * platformName: Android
  * deviceName: 
        ```$ adb devices```
       ![adb devices](/img/appium/adb-devices.png "adb devices")
  * app: apk在電腦的路徑
      可透過[https://apps.evozi.com/apk-downloader/](https://apps.evozi.com/apk-downloader/)將apk載到電腦裡
      
