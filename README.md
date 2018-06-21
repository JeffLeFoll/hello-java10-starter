[![Build Status](https://travis-ci.org/jooby-project/hello-java10-starter.svg?branch=master)](https://travis-ci.org/jooby-project/hello-java10-starter)
# hello starter

Hello world starter project for Java 9/10/11+.

## goal

This project shows how to run [Jooby](http://jooby.org) in Java 10. To run Java 9/10/11 etc all you have to do is to set the `java.source.version` in your `pom.xml` file:

```xml
<!-- jdk 10 -->
<java.source.version>10</java.source.version>
```

## quick preview

This project contains a simple application that:

* Accept an optional `name` HTTP parameter
* Creates a POJO and send the response back as JSON

[App.java](https://github.com/jooby-project/hello-java10-starter/blob/master/src/main/java/starter/hello/App.java):

```java
public class App extends Jooby {

  {

    /** Render JSON: */
    use(new Jackson());

    use(new Whoops());

    /**
     * Say hello:
     */
    get(req -> {
      var name = req.param("name").value("Jooby");
      return new Message("Hello " + name + "!");
    });
  }

  public static void main(final String[] args) {
    run(App::new, args);
  }
}

```

## run

    mvn jooby:run

## help

* Read the [jooby documentation](http://jooby.org/doc)
* Join the [channel](https://gitter.im/jooby-project/jooby)
* Join the [group](https://groups.google.com/forum/#!forum/jooby-project)
