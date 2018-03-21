# Creating Tasks

Three steps are required in order to create a new task in UCSD.

 1. Create a config Class that defines the task form format and stores the structure within a database table.
 2. Create the task itself, which uses the config Class created in step 1.
 3. Register the task at UCSD services startup within the main module class.

In this simple example, we will create a task that mimics the populate/retrieve/delete operations as described in the db_access_with_jdo section of this documentation. So let's start with the retrieve.

Firstly, we need to create a config Class that will allow the end user to specify search criteria for one of the 4 database columns used in the jdo example. Names:

 * id
 * accountName
 * volume_name
 * volume_size

Here's an example config Class that will allow any of the above to be entered as a simple text field. We will make the accountName entry mandatory. All other fields are optional.

The config Class should look something like this:

``` java
 package com.cisco.feature.acmestorage.tasks;

import javax.jdo.annotations.PersistenceCapable;
import javax.jdo.annotations.Persistent;

import com.cloupia.service.cIM.inframgr.TaskConfigIf;
import com.cloupia.service.cIM.inframgr.customactions.UserInputField;
import com.cloupia.service.cIM.inframgr.forms.wizard.FormField;

@PersistenceCapable(detachable = "true", table = "acmestorage_retrieve_dummy_data_table")
public class DummyDataRetrieveConfig implements TaskConfigIf {

	@Persistent
	public static final String displayLabel = "Dummy Table Retrieve Data";

	@Persistent
	private long configEntryId;
	@Persistent
	private long actionId;

	@FormField(label = "Enter search text for DB row retrieval:", help = "Search Criteria", mandatory = false, editable = false)
	private String workflowLabel;

	@FormField(label = "ID", mandatory = false)
	@UserInputField(type = "gen_text_input")
    @Persistent
    private String id;

	@FormField(label = "Account Name", mandatory = true)
	@UserInputField(type = "gen_text_input")
    @Persistent
    private String accountName;

	@FormField(label = "Volume Name", mandatory = false)
	@UserInputField(type = "gen_text_input")
    @Persistent
    private String volume_name;

	@FormField(label = "Volume Size", mandatory = false)
	@UserInputField(type = "gen_text_input")
    @Persistent
    private String volume_size;



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

	public String getVolume_size() {
		return volume_size;
	}

	public void setVolume_size(String volume_size) {
		this.volume_size = volume_size;
	}

	@Override
	public String getDisplayLabel() {
		return displayLabel;
	}

	@Override
	public long getActionId() {
		return actionId;
	}

	@Override
	public void setActionId(long actionId) {
		this.actionId = actionId;
	}

	@Override
	public long getConfigEntryId() {
		return configEntryId;
	}

	@Override
	public void setConfigEntryId(long configEntryId) {
		this.configEntryId = configEntryId;
	}

}
```

**IMPORTANT:** Be sure to create a _jdo.files_ file within the package directory and add the entry:

```+DummyDataRetrieveConfig```

Next, we need to create the task class. Next...
