# Oracle Java 8 - JDK

## Using a Dockerfile

In your `Dockerfile`, you can easily compile and run your project:

```
FROM alisonalonso/java:jdk8
copy . /src
RUN javac MyApp.java
CMD ["java", "MyApp"]
```

## Compile your app in a container

To compile, but not run your app inside a Docker instance, you can use this:

```shell
$ docker run --rm -v $(pwd):/src alisonalonso/java:jdk8 javac MyApp.java
```

