Project creation
==================

Cocoon cloud compiler is a remote service to create and customize executable applications for your desired mobile OS (currently, iOS and Android). It allows you to setup a project, upload your source code and generate the final .APK for Android and a XCode project for iOS that you can upload yourself to the Google Play Store, Amazon App Store and the Apple App Store respectively.

You must first be registered in Cocoon. If you haven't registered yet, you can do it in just a few seconds [here](http://cocoon.io/). Once you have logged in, you can start creating projects.

If you know nothing about Cocoon, we recommend you to read our [getting started guide](/user-guide/) before using the cloud compiler.

## Create a project

A project is the base of a compilation. It contains the configuration and resources needed to generate the final binary files for Android and iOS, including the source code.

This is an empty project card. This is the first element you will notice once you are logged in the cloud by the first time. And, as you can see, there are four main ways of creating a new project: [from an external url](/user-guide/project-creation#from-web-to-app), dragging and dropping a [zip file](/user-guide/project-creation#from-zip), using a [github repository](/user-guide/project-creation#from-github) or selecting the [guided creation](/user-guide/project-creation#guided-creation).  

![[class='center'] Create project](img/create-project.png "Create project")

### From Web to App

If you have a website and it is adapted for mobile devices, you can introduce here the url and you will see how it would look like as an app.

### From GitHub

A GitHub project that has a Cordova structure (detailed [below](/user-guide/project-creation#from-zip)) will be valid for a compilation at the cloud. It is compulsory to have at least the **www** folder and the **config.xml** file. In order to have access to this option, it is mandatory that the code you want to upload is available from a public repository.

### From ZIP

It is possible to upload to the cloud compiler the content of the **www** folder, the **full project** or a single **config.xml file**, always compressed on a zip file. At least, it is compulsory to have the *www* folder or the *config.xml file*.

* If it is just included the www folder, the config.xml file will be generated by default at the cloud.

* If it is provided just a config.xml file, take into account that every file referred on it will be searched in the zip file (icons, content, index,...). If those referred files are not found, the zip will be rejected. In addition, take into account that, even if the project is created, there won't be any source code apart from the config.xml file.

![[class='left'] Recommended content](img/project-content.png "Recommended content")

This is the structure a project must have. Unlikely a normal project for Cordova, the folders **platforms**, **hooks** and **plugins** are not necessary but it is recommendable to add the **res** folder containing all the icons and splashes the project requires. We don't use the **platforms** folder so don't add it to the zip file as it will only waste your bandwidth when uploading. If you have a plugins folder we install the plugins inside it. Uploading a config.xml file to the cloud will update the project's configuration with the config.xml configuration.

To create the project, just drag and drop the compressed file on an empty project card and it will be created automatically.

**Important**: Remember that when uploading a config.xml file to the cloud we will update the project's configuration with the config.xml configuration. You may want to do that the first time you create the project so we read your configuration from there but once your project has been created, we recommend to upload just the source code (**www** and **res** optionally) and use the project configuration UI to configure the project.

### Guided creation

This is the project creation wizard. It will assist you to create your project in 3 easy steps.

![[class='center'] Project creation wizard](img/creation-wizard.png "Project creation wizard")

**Provide HTM5 Code**

The first step is to decide the origin of your source code. There are 4 different possibilities:

![[class='center'] Available code origins](img/wizard-source.png "Available code origins")

As you can see, there is one new option:

**From template**

This is the fastest way to have a Cocoon project compiled and configured in order to test how different game engines and frameworks run inside our webview engines. Each demo will be customized with the data provided in next steps of the wizard.

In most of the cases, unless otherwise stated, we don't belong the code. The author of each demo is referred in the project configuration, and so does the repository where it is the original source code.

Feel free to test them as many times as you want. We have different templates (Phaser, AngularJS and Polymer among others) and we expect to keep adding more in the short term.

**Choose webview**

Once you have decided the origin of the source code, it is time to decide the [webview engine](/webview-engines/).

![[class='center'] Available webview engines](img/wizard-webview.png "Available webview engines")

If you have any doubt about which webview engine is the best for your project, you will find more information in each [webview engine](/webview-engines/) section. If you have selected a template, the best webview engine has been already set, and you can skip this step.

**Fill project data**

Introduce a project name and a package name (bundle id) for your project. For example:

![[class='center'] Project creation data](img/wizard-data.png "Project creation data")

This information can be edited later from the [project configuration](/user-guide/project-configuration) once the creation is complete.

## Modify a project

You can download the source code of your project to work locally and update it at the cloud as many times as you need. The last source code updated will be stored in the cloud compiler until the next update or the elimination of the project.

If your project is created through a github url, you will be able to synchronize all the changes from the repository linked to the project.

In addition, from the [project configuration](/user-guide/project-configuration), it is possible to edit the confi.xml file, add [plugins](/plugins), select a different [webview engine](/webview-engines), compile a [developer app](/user-guide/developer-app), choose a signing key for the different platforms or delete the project.

Remember that if the new zip file contains a config.xml, the previous configuration will be deleted.

## Compile a project

To trigger a compilation it is necessary to click the "build" button. If there is a black icon on a project card, it means that project has never been compiled. In case of doubt, a tooltip will appear hovering each platform icon.

If a compilation is in course, the icons of the platforms will flicker from grey to light blue.

To prevent accidental builds, if the "build" button is clicked during a compilation, you will be prompted with a dialog to confirm the new compilation, as the current one will be cancelled. The new compilation must wait again its turn in the compilation queue. Make sure that all the changes are up to date in your project before compiling to avoid waiting unnecessarily.

Each time a compilation finishes, the user will be notified by email. If a project is compiled more than once, the latest compilation will prevail. It is up to the user to keep the previous compilations.

If a compilation fails, the icon will appear in orange and, instead of the compiled files, it will be possible to see the full error log clicking each platform icon.

## Signing

It is possible to include personal signing keys in order to get your final apps  signed and ready for uploading them to the stores. This feature is completely optional. You can always decide not to add a signing key to a project. If there is not a signing key, you will get a project ready for being signed locally.

You can add signing keys on a [project configuration](/user-guide/project-configuration) or in the [user profile](/user-guide/user-profile).

The information required for adding a signing key is different for each platform. If you need more information, you can have a look at the [user profile](/user-guide/user-profile) documentation.

If a project is compiled with or without a signing key, the compiled files obtained from the compilation will vary.

**Android with signing key:**

* Signed *release APK*

**Android without signing key:**

* Signed *debug APK*
* Unsigned *release APK*

**iOS with signing key:**

* *IPA* file

**iOS without signing key:**

* *XCArchive* file

## Delete a project

If a project is deleted, all the data will be removed from the database and it can't be recovered. Ensure that you have a copy of the source code in case you want to keep it. Otherwise, it will be lost.

If there was a signing key linked to that project, it will be possible to assign it to other projects as it will be kept in the user profile.
