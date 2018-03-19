# Retrieving Data from the DB



```java
package com.cisco.feature.acmestorage.inventory.dummy;

import java.util.List;

import org.apache.log4j.Logger;

import com.cloupia.fw.objstore.ObjStore;
import com.cloupia.fw.objstore.ObjStoreHelper;

public class DummyTableRetrieveData {

	/*
	 * Enable logging so that we can write output to the UCSD inframgr logfile.
	 */
	static Logger logger = Logger.getLogger(DummyTableRetrieveData.class);


	/**
	 * Method to retrieve data from the DB previously stored using the DummyTablePopulate Class.
	 *
	 * @throws Exception
	 */

	public void query() throws Exception {

		/*
		 * Prepare an object store object to
		 */
		ObjStore<DummyTableConfig> store = ObjStoreHelper.getStore(DummyTableConfig.class);

		/*
		 * Using JDO to retrieve every row from the database table. Results are returned as a list of
		 * objects.
		 */
		List<DummyTableConfig> dummyTableList = store.queryAll();

		logger.info("Trying to retrieve table rows from the DB:");

		for( DummyTableConfig entryItem : dummyTableList ) {

			/*
			 * Retrieving objects from the DB and writing their values to the inframgr log.
			 */
			logger.info("ID: " + entryItem.getId());
			logger.info("Account Name: " + entryItem.getAccountName());
			logger.info("Volume Name: " + entryItem.getVolume_name());
			logger.info("Volume Size: " + entryItem.getVolume_size());			

		}

	}

}
```

Here is the output from the inframgr log after the next UCSD services restart:

```
2018-03-19 12:10:40,608 [main] INFO  initFeatures(FeatureContainer.java:253) - Initializing feature acmestorage
2018-03-19 12:10:40,609 [main] INFO  initFeature(CustomModule.java:123) - ooooooooooooooooooo
ucsdVersion=6.5.0.0
name=ACME Storage
category=/AcmeStorage
accountType=Storage Account
moduleID=acmestorage
contact=rwhitear@cisco.com
version=0.0.4
format=1.0
description=UCSD Open Automation Module for ACME Storage
ooooooooooooooooooo
2018-03-19 12:10:40,609 [main] INFO  initFeature(CustomModule.java:129) - Initializing the feature: acmestorage
2018-03-19 12:10:41,137 [main] INFO  getCloupiaBuildInfoFromFile(CloupiaProductInfoUtil.java:255) - resource:file:/opt/infra/inframgr/MANIFEST.MF
2018-03-19 12:10:41,137 [main] INFO  registerComponents(AbstractCloupiaModule.java:65) - AbsractCloupiaModule:: registerComponents() java.net.URLClassLoader@2d2757ab
2018-03-19 12:10:41,137 [main] INFO  registerPodDefinition(CustomFeatureRegistry.java:297) - CustomFeatureRegistry:: registerPodDefinition() Class Loadersun.misc.Launcher$AppClassLoader@15db9742
2018-03-19 12:10:41,155 [main] INFO  populate(DummyTablePopulate.java:42) - Trying to write the following to the DB:
2018-03-19 12:10:41,156 [main] INFO  populate(DummyTablePopulate.java:43) - ID: one
2018-03-19 12:10:41,156 [main] INFO  populate(DummyTablePopulate.java:44) - Account Name: UKTME@RUSS
2018-03-19 12:10:41,156 [main] INFO  populate(DummyTablePopulate.java:45) - Volume Name: Vol01
2018-03-19 12:10:41,156 [main] INFO  populate(DummyTablePopulate.java:46) - Volume Size: 10000
2018-03-19 12:10:45,957 [main] INFO  query(DummyTableRetrieveData.java:37) - Trying to retrieve table rows from the DB:
2018-03-19 12:10:45,957 [main] INFO  query(DummyTableRetrieveData.java:44) - ID: one
2018-03-19 12:10:45,957 [main] INFO  query(DummyTableRetrieveData.java:45) - Account Name: UKTME@RUSS
2018-03-19 12:10:45,957 [main] INFO  query(DummyTableRetrieveData.java:46) - Volume Name: Vol01
2018-03-19 12:10:45,957 [main] INFO  query(DummyTableRetrieveData.java:47) - Volume Size: 10000
2018-03-19 12:10:45,957 [main] INFO  query(DummyTableRetrieveData.java:44) - ID: one
2018-03-19 12:10:45,957 [main] INFO  query(DummyTableRetrieveData.java:45) - Account Name: UKTME@RUSS
2018-03-19 12:10:45,957 [main] INFO  query(DummyTableRetrieveData.java:46) - Volume Name: Vol01
2018-03-19 12:10:45,957 [main] INFO  query(DummyTableRetrieveData.java:47) - Volume Size: 10000
2018-03-19 12:10:45,958 [main] WARN  registerTasks(AbstractCloupiaModule.java:98) - No Tasks to register for module = acmestorage
2018-03-19 12:10:45,958 [main] WARN  registerReports(AbstractCloupiaModule.java:219) - No Reports to register for module = acmestorage
```

Notice how there are two identical entries retrieved from the DB. This is due to the fact that DummyTablePopulate is running at every service restart and is therefore adding a row into the DB everytime UCSD services are restarted.

Next, we will create a Class to delete entries from the database.
