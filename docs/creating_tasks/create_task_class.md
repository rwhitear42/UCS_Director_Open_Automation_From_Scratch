# Create a Task class

Now that the config Class has been created and an entry inserted into the _jdo.files_ file, we can go ahead and create the accompanying task Class:

Something like this:

``` java
package com.cisco.feature.acmestorage.tasks;

import org.apache.log4j.Logger;

import com.cloupia.service.cIM.inframgr.AbstractTask;
import com.cloupia.service.cIM.inframgr.TaskConfigIf;
import com.cloupia.service.cIM.inframgr.TaskOutputDefinition;
import com.cloupia.service.cIM.inframgr.customactions.CustomActionLogger;
import com.cloupia.service.cIM.inframgr.customactions.CustomActionTriggerContext;

public class DummyDataRetrieveTask extends AbstractTask{

	static Logger logger = Logger.getLogger(DummyDataRetrieveTask.class);


	@Override
	public void executeCustomAction(CustomActionTriggerContext context, CustomActionLogger actionLogger) throws Exception {

		long configEntryId = 0;
		DummyDataRetrieveConfig config = null;

		try {
			configEntryId = context.getConfigEntry().getConfigEntryId();
			config = (DummyDataRetrieveConfig) context.loadConfigObject();
		} catch (Exception e) {
			e.printStackTrace();
		}

		if (config == null) {
			throw new Exception("No configuration found for custom action "
					+ context.getActionDef().getName() + " entryId "
					+ configEntryId);
		}

		/*
		 * Firstly, let's log to the UCSD service request log the values entered by the end user.
		 */
		actionLogger.addInfo("ID: " + config.getId());
		actionLogger.addInfo("Account Name: " + config.getAccountName());
		actionLogger.addInfo("Volume Name: " + config.getVolume_name());
		actionLogger.addInfo("Volume Size: " + config.getVolume_size());

		/*
		 * Now let's build a DB query based upon the inputs.
		 */

		String query = "";

		if( config.getId().length() > 0 )
			query += "id == '" + config.getId() + "'";

		if( config.getAccountName().length() > 0) {
			if( query.length() > 0 ) {
				query += " && accountName == '" + config.getAccountName() + "'";
			} else {
				query += "accountName == '" + config.getAccountName() + "'";
			}
		}

		if( config.getVolume_name().length() > 0) {
			if( query.length() > 0 ) {
				query += " && volume_name == '" + config.getVolume_name() + "'";
			} else {
				query += "volume_name == '" + config.getVolume_name() + "'";
			}
		}

		if( config.getVolume_size().length() > 0) {
			if( query.length() > 0 ) {
				query += " && volume_size == '" + config.getVolume_size() + "'";
			} else {
				query += "volume_size == '" + config.getVolume_size() + "'";
			}
		}

		/*
		 * The final DB query will look like this:
		 */
		actionLogger.addInfo("DB Query: " + query ) ;

	}

	@Override
	public TaskConfigIf getTaskConfigImplementation() {
		return new DummyDataRetrieveConfig();
	}

	@Override
	public String getTaskName() {
		return DummyDataRetrieveConfig.displayLabel;
	}

	@Override
	public TaskOutputDefinition[] getTaskOutputDefinitions() {
		return null;
	}

}
```

Finally, we need to declare the task in the main plugin module Class.

Here...
