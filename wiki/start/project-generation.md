---
title: "创建第一个项目"
description: "libGDX Project Setup Tool 负责 libGDX Gradle 项目设置所涉及的所有步骤"
redirect_from:
  - /dev/project_generation/
  - /dev/project-generation/
---

要设置您的第一个项目并下载必要的依赖项，libGDX 提供了一个设置工具。

{% include setup_flowchart.html current='1' %}

1. 下载 libGDX Project Setup Tool (gdx-setup):

    <a href="/assets/downloads/legacy_setup/gdx-setup_latest.jar" class="btn btn--success" style="margin-right: 10px">Stable Release</a>
    <a href="https://libgdx-nightlies.s3.eu-central-1.amazonaws.com/libgdx-runnables/gdx-setup.jar" class="btn btn--success">Nightly Version</a>

2. 双击下载文件，如果启动失败，打开文件所在文件夹的控制台，运行 <br>`java -jar ./gdx-setup_latest.jar`

这将打开以下设置，允许您生成项目：

![Setup UI](https://tvax3.sinaimg.cn/large/7fee3e64ly1gzoftfa5lkj20xe10un2g.jpg){: style="width: 601px;" }

**注意：** 除了安装工具的用户界面之外，您还可以使用命令行 [command-line](/wiki/start/project-setup-via-command-line) 来创建项目。
{: .notice--primary}

系统会要求您提供以下参数：
* **Name**: 应用程序的名称；带减号的小写通常是一个好主意，例如 `my-game`
* **Package**: 代码将驻留在其中的 Java 包, 例如 `com.badlogic.mygame`
* **Game Class**: 应用的主游戏 Java 类的名称 例如 `MyGame`
* **Destination**: 将在其中创建应用的文件夹
* **Android SDK**: 您的 Android SDK 的位置。使用　Android Studio，要了解它的位置，请启动　Android Studio　并单击"Configure" -> "SDK Manager"。默认情况下，它位于 `/Users/username/Library/Android/sdk` <br>

![Android Studio welcome screen](/assets/wiki/images/project-generation2.png){: style="width: 873px;" }
![Android Studio SDK manager](/assets/wiki/images/project-generation3.png){: style="width: 1159px;" }

* **Sub Projects**: libGDX is cross-platform. By default, all the target platforms are included (Desktop; Android; iOS; HTML). There is no need to change the default value unless you are sure you will never compile for a specific target.

**Note:** iOS projects can only be compiled on macOS.
{: .notice--info}

* **extensions**: the extensions offered are:<br>
  * **[Bullet](/wiki/extensions/physics/bullet/bullet-physics)**: 3D Collision Detection and Rigid Body Dynamics Library.<br>
  * **[FreeType](/wiki/extensions/gdx-freetype)**: Scalable font. Great to manipulate font size dynamically. However be aware that it does not work with HTML target if you cross compile for that target.<br>
  * **Tools**: Set of tools including: particle editor (2d/3d), bitmap font and image texture packers.<br>
  * **[Controllers](https://github.com/libgdx/gdx-controllers)**: Library to handle controllers (e.g. Xbox 360 controller).<br>
  * **[Box2d](/wiki/extensions/physics/box2d)**: Box2D is a 2D physics library.<br>
  * **[Box2dlights](https://github.com/libgdx/box2dlights)**: 2D lighting framework that uses box2d for raycasting and OpenGL ES 2.0 for rendering.<br>
  * **[Ashley](https://github.com/libgdx/ashley)**: A tiny entity framework.<br>
  * **[Ai](https://github.com/libgdx/gdx-ai)**: An artificial intelligence framework.<br>

By clicking "Show Third Party Extensions" you can access a list of community-made libGDX extensions. If you want to add extensions later on, please take a look at [this](/wiki/articles/dependency-management-with-gradle#libgdx-extensions) wiki page.

When ready, click "Generate".

**Note:** You may get a message indicating that you have a more recent version of Android build tools or Android API than the recommended. This is not a blocking message and you may continue.
{: .notice--info}

## Project Layout
This will create a directory called `mygame` with the following layout:

```
settings.gradle            <- definition of sub-modules. By default core, desktop, android, html, ios
build.gradle               <- main Gradle build file, defines dependencies and plugins
gradlew                    <- local Gradle wrapper
gradlew.bat                <- script that will run Gradle on Windows
gradle                     <- script that will run Gradle on Unix systems
local.properties           <- IntelliJ only file, defines Android SDK location

core/
    build.gradle           <- Gradle build file for core project*
    src/                   <- Source folder for all your game's code

desktop/
    build.gradle           <- Gradle build file for desktop project*
    src/                   <- Source folder for your desktop project, contains LWJGL launcher class

android/
    build.gradle           <- Gradle build file for android project*
    AndroidManifest.xml    <- Android specific config
    assets/                <- contains for your graphics, audio, etc.  Shared with other projects.
    res/                   <- contains icons for your app and other resources
    src/                   <- Source folder for your Android project, contains android launcher class

html/
    build.gradle           <- Gradle build file for the html project*
    src/                   <- Source folder for your html project, contains launcher and html definition
    webapp/                <- War template, on generation the contents are copied to war. Contains startup url index page and web.xml

ios/
    build.gradle           <- Gradle build file for the iOS project*
    src/                   <- Source folder for your iOS project, contains launcher
```

## What is Gradle?
libGDX projects are [Gradle](https://gradle.org/) projects, which makes managing dependencies and building considerably easier.

Gradle is a **dependency management** system and thus provides an easy way to pull in third-party libraries into your project, without having to manually download them. Instead, Gradle just needs you to provide it with the names and versions of the libraries you want to include in your application. This is all done in the Gradle configuration files. Adding, removing and changing the version of a third-party library is as easy as changing a few lines in that configuration file. The dependency management system will pull in the libraries you specified from a central repository (in our case [Maven Central](http://search.maven.org/)) and store them in a directory outside of your project. Find out more in our [wiki](/wiki/articles/dependency-management-with-gradle).
{: .notice--info}

In addition, Gradle is also a **build system** helping with building and packaging your application, without being tied to a specific IDE. This is especially useful if you use a build or continuous integration server, where IDEs aren't readily available. Instead, the build server can call the build system, providing it with a build configuration so it knows how to build your application for different platforms. If you want to know more about deploying your application, take a look [here](/wiki/deployment/deploying-your-application).
{: .notice--info}

**Now you are ready to [import the project into your IDE and run it](/wiki/start/import-and-running).**
