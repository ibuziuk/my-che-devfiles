[![Contribute](https://che.openshift.io/factory/resources/factory-contribute.svg)](https://che.openshift.io/f?url=https://raw.githubusercontent.com/ibuziuk/my-che-devfiles/master/spring-rest-guide/devfile.yaml)

== Known issues

- https://github.com/spring-guides/gs-rest-service - contains both gradle and maven conig
- gradle integration does not work with java 11:

````
Could not create an instance of Tooling API implementation using the specified Gradle distribution 'https://services.gradle.org/distributions/gradle-4.6-bin.zip'.
Could not create service of type FileMetadataAccessor using NativeServices.createFileMetadataAccessor().
Could not determine java version from '11.0.4'.
````
