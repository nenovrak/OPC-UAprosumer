Arrowhead Framework OPC-UA service prosumer:
=======
Prosumer Design Description
=======

Service prosumer version: 0.2 compatible with the Arrowhead Framework 4.x

## Introduction
The Arrowhead Framework OPC-UA service prosumer is a (Java) program that acts as an interface between an OPC-UA enabled device (e.g., a PLC) and an Arrowhead Framework local cloud.
It can be seen as a wrapper that enables the OPC-UA device to offer services within a local cloud.

## Use cases
![Use case](Figures/useCase.png)

## Sequence diagrams
![Sequence diragram](Figures/sequence.png)

## Services
Being an Arrowhead Framework service prosumer, it produces and consumes services of other prosumers within its local cloud.

### Produced services
- [opcVariable](opcVariable.md)

### Consumed services
The prosumer consume the necessary services of the core prosumers within its local cloud, such as:
- Certificate Authority (to obtain public keys of other prosumers, if secure mode is enabled)
- Authorization (to the Service Registry, if used secure mode is enabled)
- Service Registry

## Unresolved issues
- **Configuration file**: in the use case diagram, a technician types in the configuration file which ID number refers to which signal.
- *Disconnecting from the OPC-UA device*: in this version, the connection between the prosumer and the OPC-UA device is persistent. The prosumer needs to be shut down to disconnect it from the device.
- *Shutdown procedure*: the word `stop` has to be typed at the terminal prompt.
- *Safety*: the prosumer does not offer safety services.
- *Reregister*: the prosumer does not offer service re-registration services.

## Basic operations
To **start** the service prosumer, run: `java -jar provider-4.0.jar -auth` after building the Maven module. 
The `-auth` flag is optional and only adds the Consumer found in the "tester" folder to the IntraCloud authorization so that it can consume the service.

To **stop** the prosumer, type `stop` in the Terminal window in which it was started.

___
Last updated: 2019.04.03 by [Jan van Deventer](mailto:jan.van.deventer@ltu.se).