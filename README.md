# mvn-dependency-log4j
This is an example of simple Springboot microservice using maven-dependency-plugin 
which shows log4j 1.2.12 dependency.

### Preconditions
* Operating System: Ubuntu 20.04 LTS or Windows 10 or Windows 10 / WSL2
* Install [Java 17](https://adoptium.net/releases.html?variant=openjdk17&jvmVariant=hotspot)
* Install [Maven 3.8.4](https://maven.apache.org/download.cgi)

### Problem statement
``org.apache.maven.plugins:maven-dependency-plugin:3.2.0`` downloads ``log4j:log4j:1.2.12`` during maven build.
This obsolete version of log4j is not part of runtime, but is found by security scan tools in the local maven cache. 

### Reproduce the problem
* compile the project with clean maven cache.
```
rm -rf ~/.m2/repository/*
git clone https://github.com/jveverka/mvn-dependency-log4j.git
cd mvn-dependency-log4j
mvn clean install
ls -la ~/.m2/repository/log4j/log4j/
# log4j 1.2.12 is downloaded by maven dependency plugin
```
* remove maven maven-dependency-plugin from [pom.xml](pom.xml) and compile the project with clean maven cache. 
```
rm -rf ~/.m2/repository/*
mvn clean install
ls -la ~/.m2/repository/log4j/log4j/
# log4j 1.2.12 is NOT downloaded by maven dependency plugin
```

### Expected behaviour
``mvn clean install`` does not cause download of ``log4j:log4j:1.2.12`` into local ``~/.m2/repository`` maven cache.
