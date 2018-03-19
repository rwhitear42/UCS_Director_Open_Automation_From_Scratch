# Populate DB Table with Simulated Data

Now that we have defined our DB structure with the _DummyTableConfig_ Class, we can go ahead and create objects of this type and insert them into the DB table. Here is an example of how this can be achieved.

```java
package com.cisco.feature.acmestorage.inventory.dummy;

import org.apache.log4j.Logger;

import com.cloupia.fw.objstore.ObjStore;
import com.cloupia.fw.objstore.ObjStoreHelper;

public class DummyTablePopulate {

	/*
	 * Enable logging so that we can write output to the UCSD inframgr logfile.
	 */
	static Logger logger = Logger.getLogger(DummyTablePopulate.class);


	/**
	 * Method to populate DB DummyTablePopulate table.
	 *
	 * @throws Exception
	 */

	public void populate() throws Exception {

		/*
		 * Prepare an object store object to
		 */
		ObjStore<DummyTableConfig> store = ObjStoreHelper.getStore(DummyTableConfig.class);

		/*
		 * Create a new DummyTableConfig object and populate it with some simulated data.
		 */
		DummyTableConfig simData1 = new DummyTableConfig();

		simData1.setId("one");
		simData1.setAccountName("UKTME@RUSS");
		simData1.setVolume_name("Vol01");
		simData1.setVolume_size(10000);

		/*
		 * Let the inframgr log know what we are trying to do...
		 */
		logger.info("Trying to write the following to the DB:");
		logger.info("ID: " + simData1.getId());
		logger.info("Account Name: " + simData1.getAccountName());
		logger.info("Volume Name: " + simData1.getVolume_name());
		logger.info("Volume Size: " + simData1.getVolume_size());

		/*
		 * Write the object to the DB
		 */
		store.insert(simData1);

	}

}
```

It's that easy. Now let's create a Class that will retrieve our DB data and write it to the inframgr log.

Now when we recompile the plugin and upload it to UCS Director and restart the services, the inframgr logs should reflect the above like so:

```
2018-03-19 11:17:10,842 [main] INFO  initFeatures(FeatureContainer.java:253) - Initializing feature acmestorage
2018-03-19 11:17:10,842 [main] INFO  initFeature(CustomModule.java:123) - ooooooooooooooooooo
ucsdVersion=6.5.0.0
name=ACME Storage
category=/AcmeStorage
accountType=Storage Account
moduleID=acmestorage
contact=rwhitear@cisco.com
version=0.0.3
format=1.0
description=UCSD Open Automation Module for ACME Storage
ooooooooooooooooooo
2018-03-19 11:17:10,842 [main] INFO  initFeature(CustomModule.java:129) - Initializing the feature: acmestorage
2018-03-19 11:17:10,872 [main] INFO  getCloupiaBuildInfoFromFile(CloupiaProductInfoUtil.java:255) - resource:file:/opt/infra/inframgr/MANIFEST.MF
2018-03-19 11:17:10,872 [main] INFO  registerComponents(AbstractCloupiaModule.java:65) - AbsractCloupiaModule:: registerComponents() java.net.URLClassLoader@6d2bda08
2018-03-19 11:17:10,872 [main] INFO  registerPodDefinition(CustomFeatureRegistry.java:297) - CustomFeatureRegistry:: registerPodDefinition() Class Loadersun.misc.Launcher$AppClassLoader@15db9742
2018-03-19 11:17:10,894 [main] INFO  populate(DummyTablePopulate.java:42) - Trying to write the following to the DB:
2018-03-19 11:17:10,894 [main] INFO  populate(DummyTablePopulate.java:43) - ID: one
2018-03-19 11:17:10,894 [main] INFO  populate(DummyTablePopulate.java:44) - Account Name: UKTME@RUSS
2018-03-19 11:17:10,894 [main] INFO  populate(DummyTablePopulate.java:45) - Volume Name: Vol01
2018-03-19 11:17:10,894 [main] INFO  populate(DummyTablePopulate.java:46) - Volume Size: 10000
2018-03-19 11:17:10,983 [main] WARN  registerTasks(AbstractCloupiaModule.java:98) - No Tasks to register for module = acmestorage
2018-03-19 11:17:10,983 [main] WARN  registerReports(AbstractCloupiaModule.java:219) - No Reports to register for module = acmestorage
```

Next, we will create a Class that retrieves data from the database.

Next...
