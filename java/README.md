# Java Oracle

This Dockerfile, prepares Ubuntu docker image to run Java 8 by Oracle.
By using this image, you acknowledge that you have read and accepted the terms of the [end user license agreement](http://www.oracle.com/technetwork/java/javase/terms/license/)

## How to use this image

### Using a Dockrfile

In your `Dockerfile`, you can easily compile and run your project:

```
FROM alisonalonso/java
copy . /src
RUN javac MyApp.java
CMD ["java", "MyApp"]
```

### Compile your app in a container

To compile, but not run your app inside a Docker instance, you can use this:

```shell
$ docker run --rm -v $(pwd):/src alisonalonso/java javac MyApp.java
```

