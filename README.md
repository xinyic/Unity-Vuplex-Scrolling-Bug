# Ready Player Me Unity Vuplex Example

![image](https://user-images.githubusercontent.com/7085672/182814867-a729f782-d158-43e4-9e8f-9f332c356259.png)

This repository contains a Unity project that uses the paid Vuplex Web Browser plugin to run the Ready Player Me Avatar creator and load the Ready Player Me Avatar into the application at runtime. This can be used as a reference for anybody wanting to add Ready Player Me Avatars and embed the Ready Player Me avatar creator directly into their Unity application.

***NOTE: Vuplex plugins are not required for Android and iOS applications as the Ready Player Me Unity SDK comes with a free WebView module included in the Unity Package but you are free to use Vuplex WebView if you prefer.***

## What is Vuplex?

![image](https://user-images.githubusercontent.com/7085672/182815068-61c4b242-731f-4dfe-8af6-a216f7f5350a.png)

Vuplex is actually the name of a publisher on the Unity Asset store with a number of different paid "3D WebView" plugins separated for different platforms. Note that when we say Vuplex throughout this document we are referring to their Unity Plugins. As all of their plugins are architected in a similar way the general approach and logic is quite the same for each one.  

## Which Vuplex Plugin Do I Need?

### Windows, Mac + VR (PC)

**3D WebView for Windows and macOS (Web Browser)**

This version of Vuplex Web View can be used for applications targeting Windows and Mac PC (Desktop) applications. It can also be used for VR applications you just need to use a world space UI canvas.

**System requirements**

- Unity 2017.3 or above (except 2017.3 - 2018.1 are unsupported on Windows due to a Unity bug)
- Supports both Mono and IL2CPP
- Windows 8+ (x64) with D3D11 graphics
- macOS 10.10+ (x64, arm64) with Metal graphics

[Click this link for more information.](https://assetstore.unity.com/packages/tools/gui/3d-webview-for-windows-and-macos-web-browser-154144)

### Android, iOS and Mobile VR

**3D WebView for Android and iOS (Web Browser)**

This version of Vuplex Web View can be used for applications targeting both Android and iOS applications. It also works on Mobile VR applications like for Oculus Quest however it is recommended by the Vuplex developer that you instead use the 3D WebView for Android with Gecko Engine instead. You can check their [comparison page](https://support.vuplex.com/articles/android-comparison) to see the differences.

***NOTE: This version of the plugins does NOT support Vulkan graphics API***

**System requirements**

- Unity 2017.3 or above
- Supports both Mono and IL2CPP
- Android 5.0+ (armv7, arm64, x86) with OpenGL graphics
- iOS 10+, supports both Metal and OpenGL

[Click the this link for more information.](https://assetstore.unity.com/packages/tools/gui/3d-webview-for-android-and-ios-web-browser-135383)

### Android VR (Oculus Quest)

**3D WebView for Android with Gecko Engine (Web Browser)**

For mobile VR applications like those that run on devices like the Oculus quest (targeting Android) it is recommended that you use this plugin instead as it has a number of benefits included better stability. You can check their [comparison page](https://support.vuplex.com/articles/android-comparison) to see the differences.

[Click the this link for more information.](https://assetstore.unity.com/packages/tools/gui/3d-webview-for-android-and-ios-web-browser-135383)

**System requirements**

- Unity 2018.3 or above
- Supports both Mono and IL2CPP
- Android 5+ (armv7, arm64, x86, x64) with OpenGL or Vulkan

## Project Requirements

Because the Vuplex plugins are not free we have not included it in the repository. To fully run and test the project you need to have purchased one of the [Vuplex 3 WebView plugins](https://assetstore.unity.com/publishers/40309). If you haven't purchased one already you can use the `ReadyPlayerMe` discount code with [this link here](https://store.vuplex.com/cart/?coupon=ReadyPlayerMe). You can use the guide in the section above to help you understand which plugin you need. For any questions specifically about the Vuplex plugins please contact the developer.

For the Vuplex VR Test Scene you also need to import the [XR Interaction Toolkit](https://docs.unity3d.com/Packages/com.unity.xr.interaction.toolkit@2.0/manual/index.html) plugin from the package manager. This is because the scene uses the XR Origin prefab and some scripts provided with the plugin that help with UI interaction in VR.

# Desktop
## Quick Start

Open up the `VuplexDesktopScene` found in `Assets/Vuplex/Ready Player Me` folder.

To test in the editor you can just hit the Play button and the Vuplex browser should display automatically and load the demo.readyplayer.me website.

After you complete the avatar creation process the WebView should hide itself automatically and load the avatar into the scene.

To test on a built application first you need to make sure that you have added the `VuplexDesktopScene` in the build settings and it is set to as the first active scene in the Scenes In Build section. Also make sure you have set the target platform as PC, Mac, Linux as shown below.

![image](https://user-images.githubusercontent.com/7085672/182815463-1f41bd06-270c-45dc-805b-9da20a0915c9.png)

Now just click Build or Build And Run.

# VR
## Quick Start

*To run the VR Test scene you need to install the XR Interaction Toolkit plugin from the Package Manager*

Open up the `Vuplex VR Test Scene` found in `Assets/Vuplex/Ready Player Me` folder.

To test in the editor you can just hit the Play button and the Vuplex browser should display automatically and load the demo.readyplayer.me website.

After you complete the avatar creation process the WebView should hide itself automatically and load the avatar into the scene.

To test on a built application first you need to make sure that you have added the `Vuplex VR Test Scene` in the build settings and it is set to as the first active scene in the Scenes In Build section. If you are building for Oculus Quest or another mobile VR platform make sure the platform is set to Android. For Desktop VR set the target platform as PC, Mac, Linux as shown below.

![image](https://user-images.githubusercontent.com/7085672/182815820-62d73d6f-8866-4f77-ad5e-b23c18bdab12.png)

Now just click Build or Build And Run.

# Using your partner subdomain

You can change the subdomain that loads in the Web View browser by opening our Settings window found in the top toolbar `Ready Player Me/Settings`. This is the partner name you choose when you become a Ready Player Me Partner.

![image](https://user-images.githubusercontent.com/7085672/182823180-d66dc23a-91fc-417a-a4a9-a84e1535d2f8.png)

Once open edit the text field that currently has `demo` in it and enter in your partner subdomain.

***Don't forget to click save before closing the window!***

# How It works

## Common Features

This project includes 2 example scenes **Vuplex Desktop Scene** and **Vuplex VR Test Scene** which both include the use of a `CanvasWebViewPrefab` and and object with the `VuplexWebviewTest.cs` script. See below for more information on these.

![image](https://user-images.githubusercontent.com/7085672/182816604-82c8702e-0641-4813-a448-b75ca4117f08.png)

#### Canvas Web View Prefab

This is a UI prefab we provide that can be used to display the Ready Player Me avatar creator using Unity's default UI Canvas. When using this prefab make sure it is placed into the scene as the child of a Canvas GameObject. If you select the prefab or game object in the scene and look at the inspector you will see it has a `CanvasWebviewPrefab.cs` script attached to it.

![image](https://user-images.githubusercontent.com/7085672/182816886-fe9286b9-ac6d-427e-b600-205a24103286.png)

This is a script provided with the Vuplex plugin and it is important as we use this to interact and configure the browser later when we discuss the VuplexWebViewTest.cs script.

*In the Vuplex VR Test Scene the Canvas root object has the Canvas Render Mode is set to World Space, so it is rendered in 3D space which works better for VR applications*

#### Vuplex WebView Test

In both example scenes you can find an object called **Vuplex WebView Test** and if you select it in the hierarchy you can see in the Inspector that it has a custom script attached to it called VuplexWebViewTest.cs. We provide this custom script as it assists with the setup of the Vuplex Web Browser and can be used as an example for adding the Ready Player Me Avatar Creation process directly into your Unity application. In particular the We
As you can see, this script has some properties that can be assigned in the editor.

![image](https://user-images.githubusercontent.com/7085672/182817216-440e5843-53b6-494b-b0e5-98c27bcfe7a9.png)

The `Loading` property is just a `GameObject` you can assign, that will display while the avatar is loading. The `Base Web View` property needs to be set as this is the instance of the WebView we will be interacting with, it is of type `BaseWebViewPrefab` so that it will work with all the different types of WebView prefabs that Vuplex provides.

Now open up the `VuplexWebViewTest` script

### Vuplex Web View

While this is not visible in the scene the `VuplexWebView.cs` script it is a used in `VuplexWebviewTest.cs` mentioned previously. It adds some additional functionality to the different Vuplex WebView Prefabs. In particular it inserts some custom Javascript that enables us to listen to events that are fired from the `readyplayer.me/avatar` website. Using these event listeners we are able to automatically retrieve the avatar GLB Url after the creation is complete and subsequently load the avatar into the Unity Scene.

# VR Only

If you open up the `Vuplex VR Test Scene` the hierarchy will look something like this.

![image](https://user-images.githubusercontent.com/7085672/182817479-eebbcb2f-26ff-4d5d-aa47-9d5e9c1baf76.png)

Similar to the Desktop Scene, the main things that make this work is the `CanvasWebViewPrefab` and the `Vuplex WebView Test` with the addition of the XR Origin which is part of the XR Interaction Toolkit that you can download from the package manager. As mentioned previously the Canvas in this scene has the Canvas Render Mode set to World Space so that the UI is visible in 3D space, which works better for VR applications.

#### XR Origin

![image](https://user-images.githubusercontent.com/7085672/182818272-e1bdd876-b00f-4fe4-880a-39a4823885c2.png)

This is a prefab that comes with the XR Interaction Toolkit and is used as a VR Controller that handles tracking from VR devices (head and hand movement) as well as input from the controllers. If you would like to more about the XR Origin or the XR Interaction Toolkit please refer to the documentation [here](https://docs.unity3d.com/Packages/com.unity.xr.interaction.toolkit@2.0/manual/index.html).

### Known Issues

- With the older versions of Vuplex, you might experience issues with scrolling in the website. Make sure you are using version 4.1 or later.
- Although the non-Gecko Engine based version of Vuplex Android WebView has a smaller package size, you might experience 3D canvas freezing on the Ready Player Me website after a while in Quest 2. We recommend using the Gecko Engine based version for a better experience.

## Links
**Ready Player Me Unity SDK**
- [Documentation](https://docs.readyplayer.me/ready-player-me/integration-guides/unity)
- [Download](https://docs.readyplayer.me/ready-player-me/integration-guides/unity/unity-sdk-download)
- [Support](https://docs.readyplayer.me/ready-player-me/integration-guides/unity/troubleshooting)

**Resources**
- [Unity WebGL Documentation](https://docs.unity3d.com/Manual/webgl-develop.html)
- [Vuplex](https://developer.vuplex.com/webview/overview)
- [XR Interaction Toolkit](https://docs.unity3d.com/Packages/com.unity.xr.interaction.toolkit@2.0/manual/index.html)
