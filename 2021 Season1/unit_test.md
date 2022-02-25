# Unit Test

Created: May 2, 2021
Created by: Lee Anne
Tags: TDD

# The concept

Unit Test comes from [TDD](https://en.wikipedia.org/wiki/Test-driven_development) software development process. In TDD process developer should generate all test cases for each module before developing.

![TDD](https://user-images.githubusercontent.com/15176192/117570669-1c70b280-b106-11eb-947c-06c7cf8079e1.png)

Unit Testing: Software test method of which individual units of source code(module) are tested to determine whether they are fit for use. Each module(source code) should be tested **independently(1:1 law)**.

![unit_test](https://user-images.githubusercontent.com/15176192/117570659-0fec5a00-b106-11eb-9f78-4e60f44f1b2f.png)

The process of Testing(Bottom: Low level, Top: High level)

As part of White-box testing, in order to save expense of managing software application Unit testing should be performed before. Had better use in conjunction with other testing activities.

# Advantages

1. Unit tests help to fix bugs early in the development cycle and save costs.
2. It helps the developers to understand the testing code base and enables them to make changes quickly
3. Good unit tests serve as project documentation
4. Unit tests help with code re-use. Migrate both your code **and** your tests to your new project. Tweak the code until the tests run again.

# Tools

JUnit: Unit Test Framework for Java(Latest Release: [JUnit 5](https://junit.org/junit5/))

[Mockito](https://github.com/mockito/mockito): Unit Test Framework for Java. Allows Mock Object

[LDRA](https://ldra.com/company-overview/): Provides Static/Dynamic code analysis report and unit test framework. This is used in Software Verification

# Examples

With JUnit

[Generating String Calculator](https://www.youtube.com/watch?v=rEkPAfZw41o)

```java
package util;

import org.junit.Assert;
import org.junit.jupiter.api.BeforeAll;
import org.junit.jupiter.api.Test;

public class StringCalculatorTest {
	
	static StringCalculator stc;
	
	@BeforeAll
	static void setUp() throws Exception {
		stc = new StringCalculator();
	}
	
	@Test
	public void testSplit() throws Exception {
		String result[] = stc.split("1");
		Assert.assertArrayEquals(new String[] {"1"}, result);
		result = stc.split("");
		Assert.assertArrayEquals(new String[] {""}, result);
		result = stc.split(null);
		Assert.assertArrayEquals(new String[] {}, result);
	}
	
	@Test
	public void testSplitWhenComma() throws Exception {
		String result[] = stc.split("1,2,3");
		Assert.assertArrayEquals(new String[] {"1", "2", "3"}, result);
	}

	@Test
	public void testSplitWhenNewLine() throws Exception {
		String result[] = stc.split("1\n2\n3");
		Assert.assertArrayEquals(new String[] {"1", "2", "3"}, result);
	}
	
	@Test
	public void testSplitWhenNewLineAndComma() throws Exception {
		String result[] = stc.split("1\n2\n3");
		Assert.assertArrayEquals(new String[] {"1", "2", "3"}, result);
	}
	
	@Test
	public void testConvertToInt() throws Exception {
		int result[] = stc.convertToInt(new String []{"1", "2", "3"});
		Assert.assertArrayEquals(new int[] {1,2,3}, result);
		
		result = stc.convertToInt(new String[] {});
		Assert.assertArrayEquals(new int[] {}, result);
		
		result = stc.convertToInt(null);
		Assert.assertArrayEquals(new int[] {}, result);
	}
	
	public void testSum() throws Exception {
		int result = stc.sum(new String[] {"1", "2", "3"});
		Assert.assertEquals(6, result);
		
		result = stc.sum(new String[] {});
		Assert.assertEquals(0, result);
		
		result = stc.sum(null);
		Assert.assertEquals(0, result);
	}

}
```

```java
package util;

public class StringCalculator {

	public String[] split(String text) {
		
		if(text == null) return new String[] {};
		
		return text.split(",|\n");
	}

	public int[] convertToInt(String[] text) {
		
		if(text  == null) {
			return new int[] {};
		}
		
		int result[] = new int[text.length];
		for(int i = 0; i < text.length; i++) {
			int num = Integer.parseInt(text[i]);
			result[i] = num;
		}
 		
		return result;
	}

	public int sum(String[] text) {
		int result = 0;
		for(String tx : text) {
			result += Integer.parseInt(tx);
		}
		return result;
	}
	
	
	
}
```

Test Result

<img width="445" alt="Screen_Shot_2021-05-02_at_3 20 27_PM" src="https://user-images.githubusercontent.com/15176192/117570616-cf8cdc00-b105-11eb-8c7e-8d26e2963aac.png">

With JUnit and Mockito

Toy project(TBD)

# Etc...

[EMMA](http://emma.sourceforge.net/): Open Source Toolkit for Java Code Coverage(No external library dependencies. Only Java base)

ATDD: a development methodology based on communication between the business customers, the developers, and the testers

![ATDD](https://user-images.githubusercontent.com/15176192/117570585-ae2bf000-b105-11eb-9a31-07bb8e677a15.png)

It differs from developer-tester-business customer collaboration. ATDD encompasses acceptance testing, but highlights writing acceptance tests before developers begin coding.

# Reference

- [Wikipedia](https://www.wikiwand.com/en/Test-driven_development)
- [Unit Test Tutorial](https://www.guru99.com/unit-testing-guide.html#2)
- [The most famous unit testing tools 20 in 2021](https://ko.myservername.com/20-most-popular-unit-testing-tools-2021#2_JMockit)
- [ATDD](https://velog.io/@windtrip/ATDDAcceptance-Test-Driven-Development)
