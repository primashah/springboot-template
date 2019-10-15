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
For develop
```
oc new-build <repo#develop> --strategy=pipeline --name=springboot-develop --source-secret=<secret> --build-secret=<secret> -n <jenkinsProject>

oc set env bc/springboot-develop APP_NAME=springboot GIT_BRANCH="develop" GIT_CREDENTIALS=<credentials> GIT_URL=<repo> BUILD_PROJECT=<dev-project> BASE_IMAGE=redhat-openjdk8-openshift:1.2 BUILD_TAG='latest' DEPLOY_TAG='dev' STRATEGY='postman' -n <jenkinsProject>
```

For master
```
oc new-build <repo> --strategy=pipeline --name=springboot-master --source-secret=<secret> --build-secret=<secret> -n <jenkinsProject>

oc set env bc/springboot-develop APP_NAME=springboot GIT_BRANCH="master" GIT_CREDENTIALS=<credentials> GIT_URL=<repo> BUILD_PROJECT=<test-project> BASE_IMAGE=redhat-openjdk8-openshift:1.2 BUILD_TAG='latest' UAT_PROJECT=<uat-project> PROD_PROJECT=<prod-project> DEPLOY_TAG='test' STRATEGY='postman' -n <jenkinsProject>
```



