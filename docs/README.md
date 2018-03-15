# Getting Started

The core purpose of this journey is to lead to a fully functioning (At least from a GUI perspective) and attractive plugin for UCS Director (Hereafter called UCSD). It will look and feel like support for an actual new device has been built into the UCSD framework. However, all displayed data will be simulated.

Don't worry though. This doesn't mean that it won't be fully functional. It's just that I don't want to tie the installation of this actual plugin to an actual technology for use in your own UCSD environment. Had I done so, then this would mean that you would require an instance of that technology in your environment in order for you to be able to display the various report screens and orchestration tasks.

That said, we will be creating database tables within UCSD (Via JDO enhancement) and will be populating those tables with our simulated data. It is a very small step to then employ a REST client in order to actually replace the simulated data with real content. Techniques such as JSON parsing and REST will be included along the way in these pages.

So. **Where do we start?**

Firstly, we need to create the most basic of plugin frameworks. This will include some mandatory subdirectories, a feature file (More on that later), a ```build.xml``` file for the ANT build within the Eclipse IDE and some reference libraries. Most importantly, we need to declare and create the entry class into our plugin.

[Create Initial Framework](https://github.com/rwhitear42/UCS_Director_Open_Automation_From_Scratch/tree/master/docs/initial_framework) 
