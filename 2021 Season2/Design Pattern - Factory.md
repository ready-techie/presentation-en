# Design Pattern - Factory

Created: July 21, 2021
Created by: Lee Anne
Tags: Design_Pattern

## Purpose

- Factory Pattern can be used to instantiate diverse Object instances. Factories handle the details of object creation.
- Advantages: By encapsulating the object creating in one class, developers do not have to make modifications in every implementation. We can make changes just in one factory class.
- Static factory is a general usage as Factory Design Pattern.
- It follows OO Principles(Open for extensions, closed for modification).

## Example

- Before using Factory Pattern

![IMG_579478EAADB1-1](https://user-images.githubusercontent.com/15176192/126521043-d67a023e-a86a-40f8-8a1e-08350aadc9c8.jpeg)

- After using Factory Pattern

![IMG_CD19CE41028D-1](https://user-images.githubusercontent.com/15176192/126521144-bac460f8-7a07-4604-9fd3-4c4b31415afe.jpeg)

## Design

In terms of the above case, it has a coupling architecture with other classes. Thus, on behalf of it, I am going to use 'Factory Method' pattern by implementing abstract methods.

![IMG_1D7CBE1476DD-1](https://user-images.githubusercontent.com/15176192/126521251-dc6d8739-0ec2-4186-8276-4cc10d01a043.jpeg)

## Code

- Pizza.java

```java
package test;

import java.util.ArrayList;

public abstract class Pizza {
	String name;
	String dough;
	String sauce;
	
	ArrayList<String> toppings = new ArrayList<>();
	
	public void prepare() {
		System.out.println("Preparing " + name + " pizza...");
		System.out.println("Adding toppings: ");
		
		for(int i = 0; i < toppings.size(); i++) {
			System.out.print(toppings.get(i));
		}
		System.out.println();
	}
	
	public void bake() {
		System.out.println("This pizza should be baked at least 25 min");
	}
	
	public void cut() {
		System.out.println("Cutting the pizza half");
	}
	
	public void box() {
		System.out.println("Wrap the pizza with a pizza box");
	}	
}
```

- PizzaStore.java

```java
package test;

public abstract class PizzaStore {
	
	public Pizza orderPizza(String type) {
		
		Pizza pizza;
		
		pizza = createPizza(type);
		
		pizza.prepare();
		pizza.bake();
		pizza.cut();
		pizza.box();
		
		return pizza;
	}
	
	protected abstract Pizza createPizza(String type);
}
```

- Concrete Class 1(NYStylePizza.java)

```java
package test;

public class NYStyleCheesePizza extends Pizza {
	public NYStyleCheesePizza() {
		name = "NY Cheese Pizza";
		dough = "Thin crust";
		sauce = "Salsa Sauce";
		
		toppings.add("Tomatoes");
	}
}
```

- Concrete Class 2(ChicagoStylePizza.java)

```java
package test;

public class ChicagoStyleCheesePizza extends Pizza {
	public ChicagoStyleCheesePizza() {
		name = "Chicago Cheese Pizza";
		dough = "Thick crust";
		sauce = "Tomato Sauce";
		
		toppings.add("Bacons");
	}
}
```

- Concrete Factory Class1(NYStylePizzaStore.java)

```java
package test;

public class NYStylePizzaStore extends PizzaStore {
	
	public Pizza createPizza(String item) {
		if(item.equals("cheese")) {
			return new NYStyleCheesePizza();
		}
		return null;
	}
}
```

- Concrete Factory Class2(ChicagoPizzaStore.java)

```java
package test;

public class ChicagoStylePizzaStore extends PizzaStore {

	public Pizza createPizza(String item) {
		if(item.equals("cheese")) {
			return new ChicagoStyleCheesePizza();
		}
		return null;
	}
}
```

## Conclusion

![IMG_002A5FA4E974-1](https://user-images.githubusercontent.com/15176192/126521318-bb1d2d1c-c7d5-4f18-9e79-4a520b030d39.jpeg)
