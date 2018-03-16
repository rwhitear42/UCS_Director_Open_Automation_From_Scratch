# Create Feature file

The feature file resides in the project root directory and must be named <FEATURE_NAME>.feature. So for example, taking our new ACME Storage plugin, the feature file needs to be named:

```acme-storage.feature```

The contents of the feature file detail the name of the final feature output prefixed by 'features/'. If the new module contains any Java libraries that need to be packaged along with it, then these Jars should also be listed here. Finally, there should be an entry detailing the entry Class into the project. This Class must extend _AbstractCloupiaModule_, but more on that shortly.

Here is an example of how our ACME Storage feature file could look:

```
{
      jars:  [ "features/feature-acme-storage.jar", "features/acme-storage/lib/jsch/jsch-0.1.45.jar" ],
      features: [ "com.cisco.feature.acme-storage.AcmeStorageModule" ]
}
```

The example above shows how the packaged module will be named within UCSD (/opt/infra/inframgr/features/feature-acme-storage.jar).

It also details that jsch-0.1.45.jar needs to be packaged along too (**Don't forget to modify the build.xml file when adding new libraries to be used**)

Finally, it details the entry point into the main Java Class (AcmeStorageModule.java). This class will be discussed in detail later on.

Next, we need to [create a module.properties file](https://github.com/rwhitear42/UCS_Director_Open_Automation_From_Scratch/blob/master/docs/initial_framework/5_module_properties.md).
