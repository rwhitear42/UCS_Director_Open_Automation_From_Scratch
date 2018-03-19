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
