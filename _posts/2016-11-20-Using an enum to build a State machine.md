---
layout: default
title:  "Using an enum to build a State machine"
date: 2016-11-20 07:30:26 +0800
categories: java
---
#### Overview

The enum is Java is more powerful than many other languages which can lead to surprising uses.

In this article, I outline some the individual features of enum in Java, and put them together to form a state machine.

#### Enum for Singleton and Utility class

You can use an enum as a Singleton or Utility very simply.

```
enum Singleton {
    INSTANCE;
}
enum Utility {
    ; // no instances
}
```
<!--description-->

#### Enum to implement an interface

You can also implement an interface in an enum.

```
interface Named {
    public String name();
    public int order();
}

enum Planets implements Named {
    Mercury, Venus, Earth, Mars, Jupiter, Saturn, Uranus, Neptune;
    // name() is implemented automagically.
    public int order() { return ordinal()+1; }
}

```

#### Each Enum Instance a different sub-class

You can override the behaviour of an instance. This effectively give the instance a different sub-class of the enum with its own implementation.

```
// from http://download.oracle.com/javase/1,5.0/docs/guide/language/enums.html
public enum Operation {
  PLUS   { double eval(double x, double y) { return x + y; } },
  MINUS  { double eval(double x, double y) { return x - y; } },
  TIMES  { double eval(double x, double y) { return x * y; } },
  DIVIDE { double eval(double x, double y) { return x / y; } };

  // Do arithmetic op represented by this constant
  abstract double eval(double x, double y);
}

```

#### Using an enum as a state machine

[![img](http://t2.gstatic.com/images?q=tbn:ANd9GcQuPJJYVwYKMdS-oKpV0eumb8e3B140f1flSOnxQeeD37nxuIDu)](http://t2.gstatic.com/images?q=tbn:ANd9GcQuPJJYVwYKMdS-oKpV0eumb8e3B140f1flSOnxQeeD37nxuIDu)

What you can do with all these techniques is to create a enum based statement.

In this short example, a parser state machine processes raw XML from a ByteBuffer. Each state has its own process method and if there is not enough data available, the state machine can return to retrieve more data. Each transition between states is well defined and the code for all states is together in one enum.

```
interface Context {
    ByteBuffer buffer();
    State state();
    void state(State state);
}
interface State {
    /**
       * @return true to keep processing, false to read more data.
     */
    boolean process(Context context);
}
enum States implements State {
    XML {
        public boolean process(Context context) {
            if (context.buffer().remaining() < 16) return false;
            // read header
            if(headerComplete)
                context.state(States.ROOT);
            return true;
        }
    }, ROOT {
        public boolean process(Context context) {
            if (context.buffer().remaining() < 8) return false;
            // read root tag
            if(rootComplete)
                context.state(States.IN_ROOT);
            return true;
        }
    }
}

public void process(Context context) {
    socket.read(context.buffer());
    while(context.state().process(context));
}
```

Using this approach it is possible to write an XML parser which can process packets in sub 10 micro-seconds. It is as efficient as you would need for most cases.

**Reference: **[Java Secret: Using an enum to build a State machine](http://vanillajava.blogspot.com/2011/06/java-secret-using-enum-as-state-machine.html) from our [JCG partner](http://www.javacodegeeks.com/p/jcg.html) [Peter Lawrey](http://www.blogger.com/profile/17982030676088168612) at the [Vanilla Java](http://vanillajava.blogspot.com/).
