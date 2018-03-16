# Install and Link Open Automation libraries

The UCS Director Open Automation libraries, the log4j logging library and the Datanucleus JDO enhancement libraries must be installed into your Eclipse project and the Jars externally referenced.

Start by copying the following directories from the _repository/ucsd<VERSION>/lib_ directory to the _lib_ folder within your Eclipse project:

 * ucsd-oa-sdk
 * logging
 * jdo

Once complete, your Eclipse project should look something like this:

![alt text](https://github.com/rwhitear42/UCS_Director_Open_Automation_From_Scratch/blob/master/docs/initial_framework/images/oa_libraries_installation.png "OA libraries")

Once copied, select each Jar file and add it to the build path like so:

![alt text](https://github.com/rwhitear42/UCS_Director_Open_Automation_From_Scratch/blob/master/docs/initial_framework/images/reference_jars.png "Build Path")

Continue until all libraries have been added to the build path.

Finally, we need to create our entry point Java Class as declared in the acme-storage.feature file.

This procedure can be found [here](https://github.com/rwhitear42/UCS_Director_Open_Automation_From_Scratch/blob/master/docs/initial_framework/7_module_entry_point_java_class.md).
