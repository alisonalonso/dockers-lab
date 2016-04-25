# Java Oracle

This Dockerfile, prepares a dockers image to run Oracle Java 8 (JRE and JDK).
By using this image, you acknowledge that you have read and accepted the terms of the [end user license agreement](http://www.oracle.com/technetwork/java/javase/terms/license/)

## How to use

### Running Java Apps

```
$ docker run -it --rm -v $(pwd):/app -w /app alisonalonso/java:jre8 java MyApp
```

### Compile your app in a container

To compile, but not run your app inside a Docker instance, you can use this:

```shell
$ docker run --rm -v $(pwd):/src alisonalonso/java javac MyApp.java
```

