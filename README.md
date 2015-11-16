# Introduction

Dockerfile to build a JBoss Fuse Service Works container image.  This sits upon EAP with Java EE container deployment support.

FSW uses JBoss Fuse Enterprise Message Bus (ESB).  The underlying technology to Fuse is JBoss A-MQ, which has integrated Apache Qpid (for AMQP) and Apache Camel inside the Message Broker (for flexible messaging), and thus gives multi-protocol, multi-language support out of the box.  



Currently this image acts as a stand-alone container in single-node availability.

## Building a new Version

* Download JBoss A-MQ from http://www.jboss.org/products/amq/download/
* Put the file in the "install_files" directory
* Update the VERSION file
* run `build.sh`

## Downloading from a Docker Registry

These builds are not performed by the **Docker Trusted Build** service because it contains JBoss proprietary code, but this method can be used if using a [Private Docker Registry](https://docs.docker.com/registry/deploying/).

```bash
docker pull jlgrock/activemq:$VERSION
```

# Examples of Running a Container

The following will map all exposed ports
```bash
docker run -it --rm -p 8101:8101 -p 8181:8181 -p 44444:44444 -p 1099:1099 -p 61616:61616 jlgrock/jboss-amq:6.2.0
```
