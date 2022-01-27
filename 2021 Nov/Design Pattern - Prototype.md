# Design Pattern - Prototype

Created: October 25, 2021
Created by: Lee Anne
Tags: Design_Pattern

# Concept

- The pattern that one object can clone new object to create
- One of creational design pattern

![img](https://user-images.githubusercontent.com/15176192/140093898-cb6236f8-3e74-46f4-a9aa-bf880b493121.gif)


- This could be used when the resources can be overloaded while generating new instance every time

# Code

```java
package test;

import java.util.Objects;

/* you should implement Cloanable interface if you want to make a copy
 with clone() method. */
public class GithubIssue implements Cloneable {

    private String url;

    public String getUrl() {
        return url;
    }

    public void setUrl(String url) {
        this.url = url;
    }

    @Override
    protected Object clone() throws CloneNotSupportedException {
        return super.clone();
    }

    @Override
    public boolean equals(Object o) {
        if (this == o) return true;
        if (o == null || getClass() != o.getClass()) return false;
        GithubIssue that = (GithubIssue) o;
        return Objects.equals(url, that.url);
    }

    @Override
    public int hashCode() {
        return Objects.hash(url);
    }
}
```

```java
package test;

public class PrototypeTest {

    public static void main(String...args) throws CloneNotSupportedException {
        GithubIssue issue = new GithubIssue();
        issue.setUrl("https://helloIntelliJ.com");

        GithubIssue issue1 = (GithubIssue) issue.clone();
        issue1.setUrl("https://helloIntelliJ.com");

        System.out.println(issue == issue1);
        System.out.println(issue.equals(issue1));
        System.out.println(issue.getClass() == issue1.getClass());
        System.out.println(issue.hashCode() == issue1.hashCode());

    }
}

/* result:
	 false
	 true
	 true
	 true */
```

---

clone(): this method supports `shallow` copy. If you want a `deep` copy, you should customize parent clone() method.

I have attached the concept of [shallow and deep copy reference](https://www.geeksforgeeks.org/difference-between-shallow-and-deep-copy-of-a-class/) for you.

# Pros & Cons

- Pros
    - Reduce boilerplate codes
    - Save resources to make replica
    - Return abstract type
    - Can create an object at runtime
- Cons
    - Might be complicated to generate clone Object in terms of [circular reference](https://ko.wikipedia.org/wiki/%EC%88%9C%ED%99%98_%EC%B0%B8%EC%A1%B0)

# In Real World...

- In practical field, we used not to use clone() to make a Collection copy(e.g. ArrayList, LinkedList...)

```java
// This is the normal way to make a shallow copy.
List<GithubRepository> list = new ArrayList<>();
list.add(repo);
List<GithubRepository> clone = new ArrayList<>(list);
```

- We usually use [ModelMapper](http://modelmapper.org/getting-started/) library.
- This pattern can be used with `Factory Method` Pattern.

# Reference

[GoF Design Pattern lecture by Keesun Baek](https://www.inflearn.com/course/%EB%94%94%EC%9E%90%EC%9D%B8-%ED%8C%A8%ED%84%B4/lecture/94126?tab=note&speed=1.5)

[Gof Design Pattern](http://www.kyobobook.co.kr/product/detailViewKor.laf?ejkGb=KOR&mallGb=KOR&barcode=9788945072146)
