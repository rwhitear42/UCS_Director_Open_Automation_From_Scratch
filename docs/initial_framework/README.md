# Initial Framework Creation

**NOTE** The Eclipse IDE is used throughout, and UCSD requires Java SE 8 to be configured

Here are the steps required in order to create the bare bones of a new UCSD plugin module:

 1. Create a new Java project
 2. Create the mandatory folders
 3. Create a ```build.xml``` file
 4. Create a feature file
 5. Copy and link the required Open Automation Java libraries to your project
 6. Create the entry Class for your module


#STEP 1 -  Create a new Java Project in Eclipse

Think of a name for you project and then create it within Eclipse:

![alt text](https://github.com/rwhitear42/UCS_Director_Open_Automation_From_Scratch/blob/master/docs/initial_framework/images/new_java_project.png "Creating a new project")

The simulated new technology for which we are creating this new plugin will be a storage device, manufactured by the renowned ACME Corp. Using the example below, create the plugin as named below, being sure to select JavaSE 1.8 as the execution environment.

![alt text](https://github.com/rwhitear42/UCS_Director_Open_Automation_From_Scratch/blob/master/docs/initial_framework/images/name_new_java_project.png "Name the new project")

Click ```Finish``` in order to create the new module.

Once done, you should have a new project, containing no more than the JRE System Library and a source folder ```src```:

![alt text](https://github.com/rwhitear42/UCS_Director_Open_Automation_From_Scratch/blob/master/docs/initial_framework/images/project_explorer_pane.png "Project explorer pane")

Next we need to [Create the mandatory folders](https://github.com/rwhitear42/UCS_Director_Open_Automation_From_Scratch/blob/master/docs/initial_framework/2_mandatory_folder_creation.md)
