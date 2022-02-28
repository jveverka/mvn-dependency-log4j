# mvn-dependency-log4j
This is an example of simple Springboot microservice using maven-dependency-plugin 
which shows log4j 1.2.12 dependency.

### Preconditions
* Operating System: Ubuntu 20.04 LTS or Windows 10 or Windows 10 / WSL2
* Install [Java 17](https://adoptium.net/releases.html?variant=openjdk17&jvmVariant=hotspot)
* Install [Maven 3.8.4](https://maven.apache.org/download.cgi)

### Reproduce problem
```
rm -rf ~/.m2/repository/*
git clone https://github.com/jveverka/mvn-dependency-log4j.git
cd mvn-dependency-log4j
mvn clean install
ls -la ~/.m2/repository/log4j/log4j/
# log4j 1.2.12 is downloaded by maven dependency plugin
```
