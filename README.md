# Springboot Template

Springboot template running with [Shared Jenkins Pipelines](https://github.com/redhat-mobile-consulting/shared-jenkins-pipelines)

## Environment vars
None

## Pre-requisites
- Maven [Maven](https://maven.apache.org/)


## Getting started
- Clone the repository
```
git clone  <github template url> <project_name>
```
- Install dependencies
```
cd <project_name>
mvn install
```
- Run the servie
```
mvn spring-boot:run
```

## Custom setup

### Update pom.xml
```
<scm>
        <url>https://github.com/redhat-mobile-consulting/springboot-template.git</url>
        <connection>scm:git:https://github.com/redhat-mobile-consulting/springboot-template.git</connection>
        <developerConnection>scm:git:https://github.com/redhat-mobile-consulting/springboot-template.git</developerConnection>
        <tag></tag>
    </scm>
    
    <distributionManagement>
        <snapshotRepository>
            <id>nexus-snapshots</id>
            <url>http://nexus3-misanche-nexus.apps.na39.openshift.opentlc.com/repository/maven-snapshots</url>
        </snapshotRepository>
        <repository>
            <id>nexus-releases</id>
            <url>http://nexus3-misanche-nexus.apps.na39.openshift.opentlc.com/repository/maven-releases</url>
        </repository>
    </distributionManagement>
```
# Create new pipeline in Openshift




