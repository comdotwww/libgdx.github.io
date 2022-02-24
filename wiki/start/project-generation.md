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

* **Sub Projects**: libGDX 是跨平台的. 默认状态下, 所有平台都包含的 (Desktop; Android; iOS; HTML)，除非您确定永远不会针对特定目标进行编译，否则没有必要去更改默认值。

**Note:** iOS 项目只能在 macOS 系统环境下编译.
{: .notice--info}

* **扩展**: 提供的扩展有：<br>
  * **[Bullet](/wiki/extensions/physics/bullet/bullet-physics)**: 3D 碰撞检测和刚体动力学库.<br>
  * **[FreeType](/wiki/extensions/gdx-freetype)**: 可扩展字体。非常适合动态操作字体大小。但是请注意，如果您为该目标进行交叉编译，则它不适用于 HTML 目标。<br>
  * **Tools**: 工具集，包括：粒子编辑器（2d/3d）、位图字体和图像纹理打包器。<br>
  * **[Controllers](https://github.com/libgdx/gdx-controllers)**: 用于处理控制器的库（例如 Xbox 360 控制器）。<br>
  * **[Box2d](/wiki/extensions/physics/box2d)**: 一个2D物理库。<br>
  * **[Box2dlights](https://github.com/libgdx/box2dlights)**: 2D光照框架，使用box2d进行光线投射，使用OpenGL ES 2.0进行渲染。<br>
  * **[Ashley](https://github.com/libgdx/ashley)**: 一个很小的实体类框架。<br>
  * **[Ai](https://github.com/libgdx/gdx-ai)**: 一个人工智能框架。<br>

通过单击"显示第三方扩展"，您可以访问社区制作的 libGDX 扩展列表。如果您想稍后添加扩展，请查看 [此wiki页面](/wiki/articles/dependency-management-with-gradle#libgdx-extensions) 。

准备就绪后，单击"生成"。

**注意：** 您可能会收到一条消息，指示您使用的 Android 构建工具或 Android API 版本比建议的版本更新。这不是阻止消息，您可以继续。
{: .notice--info}

## 项目布局
这将创建一个使用以下布局调用的目录：`mygame`

```
settings.gradle            <- 子模块的定义。By default core, desktop, android, html, ios
build.gradle               <- 主 Gradle 构建文件，定义依赖项和插件
gradlew                    <- local Gradle wrapper
gradlew.bat                <- 将在 Windows 上运行 Gradle 的脚本
gradle                     <- 在 Unix 系统上运行 Gradle 的脚本
local.properties           <- 仅限 IntelliJ 文件，定义 Android SDK 位置

core/
    build.gradle           <- Gradle build file for core project*
    src/                   <- Source folder for all your game's code

desktop/
    build.gradle           <- Gradle build file for desktop project*
    src/                   <- Source folder for your desktop project, contains LWJGL launcher class

android/
    build.gradle           <- Gradle build file for android project*
    AndroidManifest.xml    <- Android specific config
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

## 什么是 Gradle？
libGDX 项目是 [Gradle](https://gradle.org/) 项目, 这使得管理依赖关系和构建变得相当容易。

Gradle 是一个 **依赖关系管理系统** ，因此提供了一种将第三方库拉入项目的简单方法，而无需手动下载它们。相反，Gradle 只需要您向它提供要包含在应用程序中的库的名称和版本。这一切都是在 Gradle 配置文件中完成的。添加、删除和更改第三方库的版本就像更改该配置文件中的几行一样简单。 依赖关系管理系统将从中央存储库（在本例中为 [Maven Central](http://search.maven.org/)）中提取您指定的库，并将它们存储在项目外部的目录中。在我们的 [wiki](/wiki/articles/dependency-management-with-gradle) 中了解更多信息。
{: .notice--info}

此外，Gradle还是一个 **构建系统** ，可帮助构建和打包应用程序，而无需绑定到特定的 IDE 。如果您使用 IDE 不易获得的生成或持续集成服务器，则此功能特别有用。相反，生成服务器可以调用生成系统，为其提供生成配置，以便它知道如何为不同的平台生成应用程序。如果您想了解有关部署应用程序的更多信息，请查看 [此处](/wiki/deployment/deploying-your-application)。
{: .notice--info}

**现在，您已准备好 [将项目导入 IDE 并运行它](/wiki/start/import-and-running)。**
