# Main Module Class Modification

Finally, we need to modify com.cisco.feature.acmestorage.AcmeStorageModule.java in order to register our new task. This is done like so:

``` java
@Override
public AbstractTask[] getTasks() {
  return new AbstractTask[] {
      new DummyDataRetrieveTask(),
    };
}
```

Once done, perform an ANT build on the build.xml file, checking in the Eclipse console that the config class got enhanced by JDO:

```
jdoEnhance:
     [java] Adding class to enhancer: com.cisco.feature.acmestorage.tasks.DummyDataRetrieveConfig    xxxxxxxxxxxxxxxxxxxxxxxxxxxxxx
```

Upload the new plugin to UCSD and restart services. Upon restart, the new task should show up within the UCSD orchestrator
