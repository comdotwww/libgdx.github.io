---
title: "设置开发环境"
description: "在启动并运行第一个libGDX项目之前，需要设置开发环境。这样的话，第一步就是选择一个 IDE 。"
redirect_from:
  - /dev/setup/
---

如果这是您第一次使用 libGDX ，那么您来对地方了。以下步骤详细介绍了如何启动并运行您的第一个 libGDX 项目。

{% include setup_flowchart.html current='0' %}

在开始使用 libGDX 之前，您需要设置一个 IDE（集成开发环境）。 基本上它们都是 Java 文件的编辑器，这使得以各种方式开发 Java 应用程序变得更加方便。**如果您已安装 IDE ，则可以跳到 [下一步](/wiki/start/project-generation).**

Java 提供了许多不同的 IDE 。他们都会有小的优点和缺点，但最终他们都做好了自己的工作，所以可以随意选择你最喜欢的任何一个。

## (1.) Android Studio
对于不仅希望面向桌面设备，还希望面向移动平台的新手，**我们推荐 Android Studio **.
{: .notice--info}

- JDK：由Android Studio提供
- IDE 自身: [Android Studio](https://developer.android.com/studio)
- Android: 开箱即用
- 对于iOS: [RoboVM OSS IntelliJ 插件](http://robovm.mobidevelop.com)

## (2.) IDEA
- JDK 8+: 有不同的发行版，但 [Adoptium](https://adoptium.net/) 应该能满足您的需求

   目前，libGDX项目 <u>不适用于</u> JDK 16，因为Gretty还不支持Gradle 7。因此，建议您使用 **JDK 8-15**!
   {: .notice--warning}
- IDE 自身: [IntelliJ IDEA](https://www.jetbrains.com/idea/download/) ("社区"版就足够了)
- 对于 Android: [Android SDK](https://developer.android.com/studio/releases/platform-tools)
- 对于 iOS: [RoboVM OSS IntelliJ 插件](http://robovm.mobidevelop.com)

## (3.) Eclipse
- JDK 8+: 有不同的发行版，但 [Adoptium](https://adoptium.net/) 应该能满足您的需求

   目前，libGDX项目 <u>不适用于</u> JDK 16，因为Gretty还不支持Gradle 7。因此，建议您使用 **JDK 8-15**!
   {: .notice--warning}
- IDE 自身: [Eclipse](https://www.eclipse.org/downloads/)
- Android: 未得到官方支持，但您可使用 [Andmore](https://projects.eclipse.org/projects/tools.andmore) 或 修改的旧版本 [ADT](https://marketplace.eclipse.org/content/android-development-tools-eclipse)
- 对于 iOS: [RoboVM OSS Eclipse 插件](http://robovm.mobidevelop.com)

## (4.) NetBeans
由于 NetBeans 在 libGDX 社区中并不常用，因此如果出现特定于 IDE 的问题，可能很难获得任何帮助。
{: .notice--info}

- JDK 8+: 有不同的发行版，但 [Adoptium](https://adoptium.net/) 应该能满足您的需求

    目前，libGDX项目 <u>不适用于</u> JDK 16，因为Gretty还不支持Gradle 7。因此，建议您使用 **JDK 8-15**!
   {: .notice--warning}
- IDE 自身: [NetBeans](https://netbeans.apache.org/download/index.html) & the NetBeans Gradle 插件
- Android: 官方未支持
- iOS: 官方未支持

## (5.) No IDE
也可以完全在没有任何 IDE 的情况下开发 libGDX 应用程序，只需使用记事本或 [Vim](https://www.vim.org).  **不推荐** 这么做, 因为 IDE 提供了一些非常方便的功能，例如代码完成和错误检查。但是，如果您坚持这样做： libGDX 是 Gradle 应用程序，因此可以通过命令行构建和执行它们。
{: .notice--info}

- JDK 8+: 有不同的发行版，但 [Adoptium](https://adoptium.net/) 应该能满足您的需求

   目前，libGDX项目 <u>不适用于</u> JDK 16，因为Gretty还不支持Gradle 7。因此，建议您使用 **JDK 8-15**!
   {: .notice--warning}
- 对于 Android: [Android SDK](https://developer.android.com/studio/releases/platform-tools)
- 设置 ANDROID_HOME 环境变量, 或者使用配置文件 gradle.properties

<br/>

**现在您已经有了一个开发环境，您可以创建您的第一个 libGDX 项目。libGDX为此提供了一个设置工具，可以生成所有必要的文件。要开始使用它，请查看 [此处](/wiki/start/project-generation).**
