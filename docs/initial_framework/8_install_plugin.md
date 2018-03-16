# Install Plugin and Restart UCSD Services

Here are the steps required in order to install and enable your newly created plugin.

Firstly, login to UCSD as admin and select Administration -> Open automation

Click the Add button:

![alt text](https://github.com/rwhitear42/UCS_Director_Open_Automation_From_Scratch/blob/master/docs/initial_framework/images/add_plugin.png "Add Plugin")

Next, click _Select a File_...

![alt text](https://github.com/rwhitear42/UCS_Director_Open_Automation_From_Scratch/blob/master/docs/initial_framework/images/select_plugin_file.png "Select Plugin")

...and browse to the directory that contains the _feature-acme-storage.zip_ file.

![alt text](https://github.com/rwhitear42/UCS_Director_Open_Automation_From_Scratch/blob/master/docs/initial_framework/images/select_plugin_file2.png "Select Plugin")

Click Submit to commit plugin

**NOTE** With 6.5.0.0 (Unpatched), the Submit button appears to do nothing even though the plugin installs correctly. Follow the next steps to confirm successful installation of the plugin.

1. SSH into the UCS Director appliance and login as user _shelladmin_.
2. Select option 3 to stop services.
3. Select option 4 to start services.

Wait for the services to come back up and login via the GUI as admin once more.

The plugin should now show under Administration -> Open Automation with a status of _Enabled/Active_

![alt text](https://github.com/rwhitear42/UCS_Director_Open_Automation_From_Scratch/blob/master/docs/initial_framework/images/installed_plugin.png "Installed Plugin")

**Congratulations!** You have successfully created your first UCS Director plugin.

You can now proceed to [Creating an Account Type](https://github.com/rwhitear42/UCS_Director_Open_Automation_From_Scratch/blob/master/docs/creating_an_account_type/README.md).
