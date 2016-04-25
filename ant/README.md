# Apache Ant 1.9.7 with JDK 8

This image provides Apache Ant 1.9.7 with Java Development Kit 8 (jdk8u92).

![Apache Ant](http://ant.apache.org/images/project-logo.gif)

## How to use

### Run directly

You can run a Ant by using the Ant Docker image directly:

```
$ docker run -it --rm -v $(pwd):/src -w /src alisonalonso/ant ant
```