# Create a **module.properties** File

Unlike the build.xml and acme-storage.features files, the module.properties file resides in the <PROJECT_ROOT>/src directory. It is used to declare the following:

 * module ID of the plugin
 * The current plugin version (We will increment this as we make changes to the module code)
 * The minimum UCS Director version that this plugin will work with
 * Category is the orchestration folder within UCSD where the AcmeStorage tasks will resides
 * format is always 1.0
 * The name is shown in some reports
 * The accountType is specific to the physical account type within UCSD. In our case, we are building support for a storage device
 * The description shows up in the Open Automation section of the UCSD GUI
 * The contact also shows up in the Open Automation section of the UCSD GUI

 Below is a example module.properties file and is the one that we will use for our new acme-storage module.

```
#id the unique identifier for the module (recommendation: restrict this to 3-5 lowercase ascii alphabet characters)
moduleID=acme-storage
#version is the current version your module is on
version=0.0.1
#ucsdVersion is the version of UCSD this version of your module will work best with
ucsdVersion=6.5.0.0
#category is the path where all your tasks will be placed in
category=/AcmeStorage
#format is the version this module is formatted in
format=1.0

#name is a user friendly string to identify your module in the open automation reports
name=ACME Storage

#required for account cleanup purpose if you are making any account entry
accountType=Storage Account
description=UCSD Open Automation Module for ACME Storage
contact=rwhitear@cisco.com
```

Next, we need to install and link the Open Automation libraries into our Eclipse project. [Next](https://github.com/rwhitear42/UCS_Director_Open_Automation_From_Scratch/blob/master/docs/initial_framework/6_install_and_link_OA_libraries.md)
