# AcmeStorageModule.java Class

The module entry Class name and package location must match the entry in the module features file. It must also extend _AbstractCloupiaModule_ and implement the mandatory methods.

For our AcmeStorage module, the entry Class will look something like so:

``` java
package com.cisco.feature.acmestorage;

import com.cloupia.service.cIM.inframgr.AbstractCloupiaModule;
import com.cloupia.service.cIM.inframgr.AbstractTask;
import com.cloupia.service.cIM.inframgr.CustomFeatureRegistry;
import com.cloupia.service.cIM.inframgr.collector.controller.CollectorFactory;
import com.cloupia.service.cIM.inframgr.reports.simplified.CloupiaReport;

public class AcmeStorageModule extends AbstractCloupiaModule {

	@Override
	public CollectorFactory[] getCollectors() {
		return null;
	}

	@Override
	public CloupiaReport[] getReports() {
		return null;
	}

	@Override
	public AbstractTask[] getTasks() {
		return null;
	}

	@Override
	public void onStart(CustomFeatureRegistry cfr) {
	}

}
```

Once created, the module framework should now be in a state that can be installed and enabled within UCS Director (Although it will do nothing!).

First of all, an ANT build is required in order to build our first plugin. To do this, right click the build.xml file within the AcmeStorage Eclipse project followed by Run As -> ANT Build.

If successful, then the Eclipse console will show something like this:

```
Buildfile: /Users/rwhitear/Documents/Cisco/Eclipse_Oxygen/eclipse-workspace/AcmeStorage/build.xml
clean:
   [delete] Deleting directory /Users/rwhitear/Documents/Cisco/Eclipse_Oxygen/eclipse-workspace/AcmeStorage/build
jdoEnhance:
     [java] Found no jdo.files in the source directory. Nothing to enhance
build:
    [mkdir] Created dir: /Users/rwhitear/Documents/Cisco/Eclipse_Oxygen/eclipse-workspace/AcmeStorage/build
      [jar] Building jar: /Users/rwhitear/Documents/Cisco/Eclipse_Oxygen/eclipse-workspace/AcmeStorage/build/feature-acme-storage.jar
     [copy] Copying 1 file to /Users/rwhitear/Documents/Cisco/Eclipse_Oxygen/eclipse-workspace/AcmeStorage/build
    [mkdir] Created dir: /Users/rwhitear/Documents/Cisco/Eclipse_Oxygen/eclipse-workspace/AcmeStorage/build/resources
    [mkdir] Created dir: /Users/rwhitear/Documents/Cisco/Eclipse_Oxygen/eclipse-workspace/AcmeStorage/build/poddefinition
    [mkdir] Created dir: /Users/rwhitear/Documents/Cisco/Eclipse_Oxygen/eclipse-workspace/AcmeStorage/build/acme-storage/lib
      [zip] Building zip: /Users/rwhitear/Documents/Cisco/Eclipse_Oxygen/eclipse-workspace/AcmeStorage/feature-acme-storage.zip
     [echo] acme-storage feature is located at /Users/rwhitear/Documents/Cisco/Eclipse_Oxygen/eclipse-workspace/AcmeStorage/feature-acme-storage.zip
BUILD SUCCESSFUL
Total time: 890 milliseconds
```

The important part here is the feature-acme-storage.zip file. This is the file that gets imported into UCS Director via its GUI, as we will show [next]().
