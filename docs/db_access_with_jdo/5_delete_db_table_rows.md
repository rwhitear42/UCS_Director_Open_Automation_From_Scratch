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
