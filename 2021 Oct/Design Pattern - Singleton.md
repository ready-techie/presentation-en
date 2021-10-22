# Design Pattern - Singleton

Created: October 14, 2021
Created by: Anonymous
Tags: Design_Pattern

# Concept

- restricts the class instances into only 'one' single instance

# Code

```java
package test;

public class SingletonPractice {
    private static SingletonPractice instance;

    public static SingletonPractice getInstance() {
        if(instance == null) {
            instance = new SingletonPractice();
        }

        return instance;
    }
}
```

However, in this case, you `cannot` authorize that this code is `thread-safe`.

Let's look at the below picture.

![multi_thread](https://user-images.githubusercontent.com/15176192/138225635-e9a34f3b-a236-4805-a95a-624b3bcf8f7f.jpeg)

If you generate multiple threads in one program, you should make them share some codes or data if it needs to be.

# Idiom

1. Lazy initialization

```java
package test;

public class SingletonPractice {
    private static SingletonPractice instance;

		private SingletonPractice(){};

    public static synchronized SingletonPractice getInstance() {
        if (instance == null) {
                if (instance == null) {
                    instance = new SingletonPractice();
                }
        }
        return instance;
    }

}
```

1. Lazy initialization(Double-checked locking)

```java
**public** **final** **class** **Singleton** {
    **private** **static** **volatile** Singleton instance = **null**;
    **private** Singleton() {}
    **public** **static** Singleton getInstance() {
        **if** (instance == **null**) {
            **synchronized**(Singleton.class) {
                **if** (instance == **null**) {
                    instance = **new** Singleton();
                }
            }
        }
        **return** instance;
    }
}
```

1. Eager initialization

```java
package test;

public class SingletonPractice {
// It might result in memory overhead(what if creating a instance needs big resources?!)
    private static final SingletonPractice INSTANCE= new SingletonPractice();

		private SingletonPractice(){};

    public static SingletonPractice getInstance() {
        return INSTANCE;
    }
}
```

1. [initialization-on-demand holder idiom](https://en.wikipedia.org/wiki/Initialization-on-demand_holder_idiom) (`Recommended`)

A singleton implementation may use [lazy initialization](https://en.wikipedia.org/wiki/Lazy_initialization), where the instance is created when the static method is first invoked. If the static method might be called from multiple [threads](https://en.wikipedia.org/wiki/Thread_(computing)) simultaneously, measures may need to be taken to prevent [race conditions](https://en.wikipedia.org/wiki/Race_condition) that could result in the creation of multiple instances. The following is a [thread-safe](https://en.wikipedia.org/wiki/Thread_safety) implementation, using lazy initialization with [double-checked locking](https://en.wikipedia.org/wiki/Double-checked_locking), written in Java. In order to avoid the synchronization overhead while keeping lazy initialization with thread safety, the preferred approach in Java is to use the [initialization-on-demand holder idiom](https://en.wikipedia.org/wiki/Initialization-on-demand_holder_idiom). 

```java
package test;

public class SingletonPractice {

    private SingletonPractice(){};

    private static class LazyHolder {
        private static final SingletonPractice INSTANCE = new SingletonPractice();
    }

    public static synchronized SingletonPractice getInstance() {
        return LazyHolder.INSTANCE;
    }

}
```

# In Real World...

There are a bunch of use cases as Singleton Design Pattern.

- Java Runtime Library
- Spring framework

```java
package com.kakaopay.kakaopay_assignment.config;

import org.springframework.context.ApplicationContext;
import org.springframework.context.annotation.AnnotationConfigApplicationContext;

public class SpringSingletonTest {

    public static void main(String...args) {
        ApplicationContext applicationContext = new AnnotationConfigApplicationContext(SpringConfig.class);

        String test1 = applicationContext.getBean("hello", String.class);
        String test2 = applicationContext.getBean("hello", String.class);
				// result: true
        System.out.println(test1 == test2);
    }

}
```

- Any other design patterns such as Facade, Builder
- *TBD: I was told that there is another way to handle this singleton case...(Figuring out)*
- **Cons:**
    - **Violates SRP Object Oriented principle**
    - **Difficult to write unit test because unit testing requires loosely coupled classes in order to isolate what's being tested**

# Reference

- [Singleton Design Pattern - Wiki](https://en.wikipedia.org/wiki/Singleton_pattern)
- [GoF Design Pattern Lecture](https://www.youtube.com/watch?v=bHRETd1rFfc)
