## Setting up Development Environment

This document describes how a developer's workstation can be setup.

### Software Requirements

* Linux or Windows
* Java 7
* Tomcat 6 or 7 or 8
* Maven 3.x

### Getting the code

There are several of ways to get code, e.g. download it as a [zip](https://github.com/nordic-institute/x-road-test-service/archive/master.zip) file or clone the git repository.

```
git clone https://github.com/nordic-institute/x-road-test-service.git
```

The code is located in the ```src``` folder.

### Building the code

Example Adapter uses Maven as the build management tool. In order to build the whole project and generate the war  file (test-service-x.x.x-SNAPSHOT.war), you must run the maven command below from the ```src``` directory.

```
mvn clean install
```

Running the above maven command generates the war file under the directory presented below:

```
src/target/test-service-x.x.x-SNAPSHOT.war
```
#### Error on building the code

If running ```mvn clean install``` generates the error presented below, there are two possible solutions.

```
[ERROR] Failed to execute goal on project test-service: Could not resolve dependencies for project com.pkrete.xrd4j.tools:example-adapter:war:0.0.1-SNAPSHOT: Failed to collect dependencies at com.pkrete.xrd4j:common:jar:0.0.6: Failed to read artifact descriptor for com.pkrete.xrd4j:common:jar:0.0.6: Could not transfer artifact com.pkrete.xrd4j:common:pom:0.0.6 from/to csc-repo (https://maven.csc.fi/repository/internal/): sun.security.validator.ValidatorException: PKIX path building failed: sun.security.provider.certpath.SunCertPathBuilderException: unable to find valid certification path to requested target -> [Help 1]
```

##### Solution 1

Skip certificate validation:

```
mvn install -Dmaven.wagon.http.ssl.insecure=true -Dmaven.wagon.http.ssl.allowall=true
```

##### Solution 2

Import CSC's Maven repository's certificate as a trusted certificate into ```cacerts``` keystore. See full [instructions](../documentation/Import-a-Certificate-as-a-Trusted-Certificate.md). CSC's Maven repository's URL is ```https://maven.csc.fi```.

### IDE Setup

The project can be imported into different IDEs, but currently this section covers only Netbeans. However, some modifications are required regardless of the IDE that's being used.

#### Netbeans

Opening the project in Netbeans.

* File -> Open Project -> path of the src folder -> Click Open Project button

Adding a new Tomcat server.

* Tools -> Servers -> Add Server

### Running the application

Below there's the default URL of the application. 

[http://localhost:8080/test-service-x.x.x-SNAPSHOT/Endpoint](http://localhost:8080/test-service-x.x.x-SNAPSHOT/Endpoint)

**N.B.!** If ```example-adapter-x.x.x-SNAPSHOT.war``` file is manually copied in Tomcat's webapp folder, then the application can be accessed at:

[http://localhost:8080/test-service-x.x.x-SNAPSHOT/Endpoint](http://localhost:8080/test-service-x.x.x-SNAPSHOT/Endpoint)
