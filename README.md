# Any23-server-docker: extend Apache any23-server to use more shell scripts as handy tools around.

# Build (locally first!)
* Due Docker Hub not allowing free Container images hosting anymore, please build your local images first.
```
./build.sh
or
make build
```

# Run (recommended for easy-start)
```
./run.sh
```
The tomcat port is http://<host_name>:18880/ and you can change it by modifying, '.env' file:
Please note the specially syntax "#" (only 1 at the beginning of the file is needed, only change the port number
18880 to say, 188888. And, make sure you don't change other characters to break the 'run.sh' special parser.
```
#PORTS_LIST="18880:8080"
```
# Quick commands
* build.sh - build local image
* logs.sh - see logs of container
* run.sh - run the container
* shell.sh - shell into the container
* stop.sh - stop the container

################################### Inherited from parent GIT ###################################
# Any23 Web Server

This is the root dir of the Any23 Web-Server module.

Apache Any23 provides a Web-Service that can be used to extract RDF from Web documents.

## Generate Web-Server Packaging

Execute 'mvn package' from this directory.

```
$ mvn package
```
From this directory it generates roughly the following...
```
.
├── pom.xml
├── README.txt
├── src
│   ├── main
│   │   ├── assembly
│   │   ├── bin
│   │   ├── java
│   │   ├── resources
│   │   └── webapp
│   └── test
│       ├── java
│       └── resources
└── target
    ├── any23-service-${version}.war
    ├── any23-service-${version}-without-deps.war
    ├── apache-any23-service-${version}-bin-server-embedded.tar.gz <<<
    ├── apache-any23-service-${version}-bin-server-embedded.zip <<<
    ├── apache-any23-service-${version}-bin.tar.gz <<<
    ├── apache-any23-service-${version}-bin-without-deps.tar.gz <<<
    ├── apache-any23-service-${version}-bin-without-deps.zip <<<
    ├── apache-any23-service-${version}-bin.zip <<<
    ├── archive-tmp
    ├── classes
    ├── generated-sources
    ├── maven-archiver
    ├── maven-shared-archive-resources
    ├── surefire
    ├── surefire-reports
    └── test-classes
```

Specific README's for each of the artifacts can be found in either ./target/*.tar.gz || ./target/*.zip (annotated above with '<<<'), where much more detailed information sources can be located.

# Docker
It may be more convenient if you use [Docker](https://www.docker.com/) for packaging and running the Any23 server.

## Build the image
```
$ docker build -t tomcat .
```

## Run the image
```
$ docker run -d -p 8080:8080 --name tomcat tomcat
```

## Hot deploy Any23 webapp (war)
```
$ docker cp target/apache-any23-service-2.4-SNAPSHOT.war tomcat:/usr/local/tomcat/webapps/apache-any23-service-2.4-SNAPSHOT.war
```
