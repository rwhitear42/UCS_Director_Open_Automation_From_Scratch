# Create a build.xml file

The UCS Director Open Automation SDK uses ANT in order to build the module file that is to be installed into the UCSD appliance. A build.xml file is used to ensure that everything is packaged up in the right way and that JDO enhancement has occurred on all Classes that require DB access (More on that in later sections).

A functional ```build.xml``` file has been made available in this repo in order to get you started. It can be found at:

**repository/<UCSD_VERSION>/buildfile/build.xml**

Simply download this file can copy it to your Eclipse Java project root directory.

![alt text](https://github.com/rwhitear42/UCS_Director_Open_Automation_From_Scratch/blob/master/docs/initial_framework/images/buildXml_folder.png "build.xml")

**NOTE** The plugin name is hardcoded into the build.xml file and will need to be changed to your actual project name if you are creating something other than 'AcmeStorage'.

```xml
<property name="moduleID" value="acme-storage" />
```
