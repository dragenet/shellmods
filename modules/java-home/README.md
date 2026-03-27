# java-home

Sets the default Java Development Kit for the session.

## What It Does

- Exports `JAVA_HOME` pointing to the Azul Zulu JDK 17 installation.

## Configuration

The current path is hardcoded to:
```
/Library/Java/JavaVirtualMachines/zulu-17.jdk/Contents/Home
```
Update the path in `init` if using a different JDK version or distribution.

## Prerequisites

- Azul Zulu JDK 17 (or the configured JDK) installed at the specified path.
