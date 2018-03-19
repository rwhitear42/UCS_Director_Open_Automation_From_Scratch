# Procedure to Create a DB Table in UCSD

In order to demonstrate database table creation in UCSD, we will do the following:

 1. Create a new package called _com.cisco.feature.acmestorage.inventory.dummy_.
 2. Create a new Class within this package called _DummyTableConfig.java_.
 3. Create a text file called jdo.files within the package directory.
 4. Add _DummyTableConfig_ Class to the jdo.files file.
 5. Run an ANT build in order to ensure that the JDO enhancement occurs for our new Class.


**Step 1**

Create a new package within Eclipse called _com.cisco.feature.acmestorage.inventory.dummy_.



**Step 2**

In this step, we need to create a Class that will employ JDO annotation in order to create and define our new dummy table. The new database table will be called _acmestorage_dummy_table_ and will have the following table columns:

 * id (String)
 * account_name (String)
 * volume_name (String)
 * volume_size (long)

We will also implement log4j logging in our Class so that we can write to the UCS Director inframgr log.

The final Java Class should look something like this:

```java
package com.cisco.feature.acmestorage.inventory.dummy;

import javax.jdo.annotations.PersistenceCapable;
import javax.jdo.annotations.Persistent;

import org.apache.log4j.Logger;

@PersistenceCapable(detachable = "true", table = "acmestorage_dummy_table")
public class DummyTableConfig {

	/*
	 * Enable logging so that we can write output to the UCSD inframgr logfile.
	 */
	static Logger logger = Logger.getLogger(DummyTableConfig.class);

    @Persistent
    private String id;

    @Persistent
    private String accountName;

    @Persistent
    private String volume_name;

    @Persistent
    private long volume_size;

  	public String getId() {
  		return id;
  	}

  	public void setId(String id) {
  		this.id = id;
  	}

  	public String getAccountName() {
  		return accountName;
  	}

  	public void setAccountName(String accountName) {
  		this.accountName = accountName;
  	}

  	public String getVolume_name() {
  		return volume_name;
  	}

  	public void setVolume_name(String volume_name) {
  		this.volume_name = volume_name;
  	}

  	public long getVolume_size() {
  		return volume_size;
  	}

  	public void setVolume_size(long volume_size) {
  		this.volume_size = volume_size;
  	}

}
```

**Steps 3 and 4**

Create a text file called _jdo.files_ within the package directory and add an entry for our newly created Class.


**Step 5**

Finally, run an ANT build and check the console output for confirmation that our new class has been enhanced.

```
jdoEnhance:
     [java] Adding class to enhancer: com.cisco.feature.acmestorage.inventory.dummy.DummyTableConfig    xxxxxxxxxxxxxxxxxxxxxxxxxxxxxx
```

Now that we have created our new database table, let's explore how to populate it with some simulated content using Java Data Objects. Next...
