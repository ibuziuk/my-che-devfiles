[![Contribute](https://www.eclipse.org/che/contribute.svg)](https://che.prod-preview.openshift.io/f?url=https://raw.githubusercontent.com/ibuziuk/my-che-devfiles/master/spring-rest-guide/devfile.yaml)

# Known issues

## Not possible to override `JAVA_OPTS or MAVEN_OPTS` in the devfile

Even though MAVEN_OPTS are defined in the devfile, env var is not set correctly in the maven container:

```
-XX:MaxRAM=150m -XX:MaxRAMFraction=2 -XX:+UseParallelGC -XX:MinHeapFreeRatio=10 -XX:MaxHeapFreeRatio=20 -XX:GCTimeRatio=4 -XX:AdaptiveSizePolicyWeight=90 -Dsun.zip.disableMemoryMapping=true -Xms20m -Djava.security.egd=file:/dev/./urandom
```

As the result `-Duser.home=/home/user` is not set which makes `mvn` commands not working:

```
[ERROR] Could not create local repository at /?/.m2/repository -> [Help 1]
[ERROR] 
[ERROR] To see the full stack trace of the errors, re-run Maven with the -e switch.
[ERROR] Re-run Maven using the -X switch to enable full debug logging.
[ERROR] 
[ERROR] For more information about the errors and possible solutions, please read the following articles:
[ERROR] [Help 1] http://cwiki.apache.org/confluence/display/MAVEN/LocalRepositoryNotAccessibleException
```

Related issue [#12679](https://github.com/eclipse/che/issues/12679) / [#13340](https://github.com/eclipse/che/issues/13340)

## The gradle version used in that project does not work on Java 11

- https://github.com/spring-guides/gs-rest-service - contains both gradle and maven conig
- gradle integration does not work with java 11:

````
Could not create an instance of Tooling API implementation using the specified Gradle distribution 'https://services.gradle.org/distributions/gradle-4.6-bin.zip'.
Could not create service of type FileMetadataAccessor using NativeServices.createFileMetadataAccessor().
Could not determine java version from '11.0.4'.
````

Related issue [#13547](https://github.com/eclipse/che/issues/13547)
