# Deleting DB Table Rows


```java
package com.cisco.feature.acmestorage.inventory.dummy;

import org.apache.log4j.Logger;

import com.cloupia.fw.objstore.ObjStore;
import com.cloupia.fw.objstore.ObjStoreHelper;

public class DummyTableDeleteData {

	/*
	 * Enable logging so that we can write output to the UCSD inframgr logfile.
	 */
	static Logger logger = Logger.getLogger(DummyTableDeleteData.class);


	/**
	 * Method to delete data from the DB previously stored using the DummyTablePopulate Class.
	 *
	 * @throws Exception
	 */

	public void delete() throws Exception {

		/*
		 * Prepare an object store object to
		 */
		ObjStore<DummyTableConfig> store = ObjStoreHelper.getStore(DummyTableConfig.class);

		/*
		 * accountName here syntactically matches that in DummyTableConfig.
		 */
		String query = "accountName == 'UKTME@RUSS'";

		logger.info("Deleting all rows containing UKTME@RUSS in DummyTableConfig");

		store.delete(query);

	}

}
```


inframgr log after UCSD services restart:

```
2018-03-19 13:45:13,251 [main] INFO  initFeatures(FeatureContainer.java:253) - Initializing feature acmestorage
2018-03-19 13:45:13,251 [main] INFO  initFeature(CustomModule.java:123) - ooooooooooooooooooo
ucsdVersion=6.5.0.0
name=ACME Storage
category=/AcmeStorage
accountType=Storage Account
moduleID=acmestorage
contact=rwhitear@cisco.com
version=0.0.5
format=1.0
description=UCSD Open Automation Module for ACME Storage
ooooooooooooooooooo
2018-03-19 13:45:13,252 [main] INFO  initFeature(CustomModule.java:129) - Initializing the feature: acmestorage
2018-03-19 13:45:13,367 [main] INFO  getCloupiaBuildInfoFromFile(CloupiaProductInfoUtil.java:255) - resource:file:/opt/infra/inframgr/MANIFEST.MF
2018-03-19 13:45:13,368 [main] INFO  registerComponents(AbstractCloupiaModule.java:65) - AbsractCloupiaModule:: registerComponents() java.net.URLClassLoader@2d2757ab
2018-03-19 13:45:13,368 [main] INFO  registerPodDefinition(CustomFeatureRegistry.java:297) - CustomFeatureRegistry:: registerPodDefinition() Class Loadersun.misc.Launcher$AppClassLoader@15db9742
2018-03-19 13:45:13,428 [main] INFO  populate(DummyTablePopulate.java:42) - Trying to write the following to the DB:
2018-03-19 13:45:13,438 [main] INFO  populate(DummyTablePopulate.java:43) - ID: one
2018-03-19 13:45:13,438 [main] INFO  populate(DummyTablePopulate.java:44) - Account Name: UKTME@RUSS
2018-03-19 13:45:13,438 [main] INFO  populate(DummyTablePopulate.java:45) - Volume Name: Vol01
2018-03-19 13:45:13,439 [main] INFO  populate(DummyTablePopulate.java:46) - Volume Size: 10000
2018-03-19 13:45:19,876 [main] INFO  query(DummyTableRetrieveData.java:37) - Trying to retrieve table rows from the DB:
2018-03-19 13:45:19,876 [main] INFO  query(DummyTableRetrieveData.java:39) - Number of rows in the DB: 3
2018-03-19 13:45:19,876 [main] INFO  query(DummyTableRetrieveData.java:46) - ID: one
2018-03-19 13:45:19,876 [main] INFO  query(DummyTableRetrieveData.java:47) - Account Name: UKTME@RUSS
2018-03-19 13:45:19,876 [main] INFO  query(DummyTableRetrieveData.java:48) - Volume Name: Vol01
2018-03-19 13:45:19,876 [main] INFO  query(DummyTableRetrieveData.java:49) - Volume Size: 10000
2018-03-19 13:45:19,877 [main] INFO  query(DummyTableRetrieveData.java:46) - ID: one
2018-03-19 13:45:19,877 [main] INFO  query(DummyTableRetrieveData.java:47) - Account Name: UKTME@RUSS
2018-03-19 13:45:19,877 [main] INFO  query(DummyTableRetrieveData.java:48) - Volume Name: Vol01
2018-03-19 13:45:19,877 [main] INFO  query(DummyTableRetrieveData.java:49) - Volume Size: 10000
2018-03-19 13:45:19,877 [main] INFO  query(DummyTableRetrieveData.java:46) - ID: one
2018-03-19 13:45:19,877 [main] INFO  query(DummyTableRetrieveData.java:47) - Account Name: UKTME@RUSS
2018-03-19 13:45:19,877 [main] INFO  query(DummyTableRetrieveData.java:48) - Volume Name: Vol01
2018-03-19 13:45:19,877 [main] INFO  query(DummyTableRetrieveData.java:49) - Volume Size: 10000
2018-03-19 13:45:19,878 [main] INFO  delete(DummyTableDeleteData.java:34) - Deleting all rows containing UKTME@RUSS in DummyTableConfig
2018-03-19 13:45:19,880 [main] WARN  registerTasks(AbstractCloupiaModule.java:98) - No Tasks to register for module = acmestorage
2018-03-19 13:45:19,880 [main] WARN  registerReports(AbstractCloupiaModule.java:219) - No Reports to register for module = acmestorage
```


After a further restart, rows reverts to one as the delete does its job:

```
2018-03-19 14:59:21,648 [main] INFO  initFeatures(FeatureContainer.java:253) - Initializing feature acmestorage
2018-03-19 14:59:21,648 [main] INFO  initFeature(CustomModule.java:123) - ooooooooooooooooooo
ucsdVersion=6.5.0.0
name=ACME Storage
category=/AcmeStorage
accountType=Storage Account
moduleID=acmestorage
contact=rwhitear@cisco.com
version=0.0.5
format=1.0
description=UCSD Open Automation Module for ACME Storage
ooooooooooooooooooo
2018-03-19 14:59:21,648 [main] INFO  initFeature(CustomModule.java:129) - Initializing the feature: acmestorage
2018-03-19 14:59:21,675 [main] INFO  getCloupiaBuildInfoFromFile(CloupiaProductInfoUtil.java:255) - resource:file:/opt/infra/inframgr/MANIFEST.MF
2018-03-19 14:59:21,676 [main] INFO  registerComponents(AbstractCloupiaModule.java:65) - AbsractCloupiaModule:: registerComponents() java.net.URLClassLoader@c845c13
2018-03-19 14:59:21,676 [main] INFO  registerPodDefinition(CustomFeatureRegistry.java:297) - CustomFeatureRegistry:: registerPodDefinition() Class Loadersun.misc.Launcher$AppClassLoader@15db9742
2018-03-19 14:59:21,726 [main] INFO  populate(DummyTablePopulate.java:42) - Trying to write the following to the DB:
2018-03-19 14:59:21,735 [main] INFO  populate(DummyTablePopulate.java:43) - ID: one
2018-03-19 14:59:21,735 [main] INFO  populate(DummyTablePopulate.java:44) - Account Name: UKTME@RUSS
2018-03-19 14:59:21,735 [main] INFO  populate(DummyTablePopulate.java:45) - Volume Name: Vol01
2018-03-19 14:59:21,735 [main] INFO  populate(DummyTablePopulate.java:46) - Volume Size: 10000
2018-03-19 14:59:25,321 [main] INFO  query(DummyTableRetrieveData.java:37) - Trying to retrieve table rows from the DB:
2018-03-19 14:59:25,321 [main] INFO  query(DummyTableRetrieveData.java:39) - Number of rows in the DB: 1
2018-03-19 14:59:25,321 [main] INFO  query(DummyTableRetrieveData.java:46) - ID: one
2018-03-19 14:59:25,321 [main] INFO  query(DummyTableRetrieveData.java:47) - Account Name: UKTME@RUSS
2018-03-19 14:59:25,321 [main] INFO  query(DummyTableRetrieveData.java:48) - Volume Name: Vol01
2018-03-19 14:59:25,321 [main] INFO  query(DummyTableRetrieveData.java:49) - Volume Size: 10000
2018-03-19 14:59:25,322 [main] INFO  delete(DummyTableDeleteData.java:34) - Deleting all rows containing UKTME@RUSS in DummyTableConfig
2018-03-19 14:59:25,324 [main] WARN  registerTasks(AbstractCloupiaModule.java:98) - No Tasks to register for module = acmestorage
2018-03-19 14:59:25,325 [main] WARN  registerReports(AbstractCloupiaModule.java:219) - No Reports to register for module = acmestorage
```
