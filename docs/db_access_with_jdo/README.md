# Creating and Accessing Database Tables in UCSD

UCS Director uses JDO by Datanucleus in order to abstract the creation and accessing of database tables. The name of each new DB table created within UCSD by the plugin must start with the name of the plugin itself. This ensures uniqueness among all plugins and ensures that system tables are not corrupted. Also, the name of any Class that requires persistence within the database needs to declare itself for JDO enhancement at plugin build time. This is achieved by creating a text file called ```jdo.files``` in each package directory that requires JDO enhancement and then adding the Class name (Preceded by +) to that file.

Plugins created and use database tables within UCSD for a variety of reasons. Most common use will be for the storage of form structure for orchestrator tasks and report tabs. It will also be likely though, that new tables will also be needed for device inventory too. In order to show how this works, we will create a dummy table in our new plugin and will populate it with some simulated data. We will then examine the contents of the new table at startup and will output it to the system log.

So, let's get started.
