Today's topic is from the keywords I learned while working. These are related with clean code and coding pattern for better understanding and meaningful code.

## Access modifier (or access specifiers)

- keywords in object-oriented languages that set the accessibility of classes, methods, and other members
- specific part of programming language syntax used to facilitate the encapsulation of components
- `Assembly`: Assemblies form the fundamental units of deployment, version control, reuse, activation scoping, and security permissions for *.NET-based* applications. An assembly is a **collection of types and resources that are built to work together and form a logical unit of functionality**. Assemblies take the form of executable (.exe) or dynamic link library (.dll) files, and are the building blocks of .NET applications. They provide the common language runtime with the information it needs to be aware of type implementations.
```
These are keywords in oo langs that set the accessibility between classes, methods..and so on. Withe proper access modifier, the code gets properly encapsulated.  
~  
So these are formed as exe or dll files and can be referenced by other projects 
```
### **Public**

Can be accessed by any other code in the same assembly or another assembly that references it.

![https://camo.githubusercontent.com/999e6cab5460a6907ee14c7b32064d995e6ecbb39505fdf57b2cb7720f8a0cd4/68747470733a2f2f692e737461636b2e696d6775722e636f6d2f5647676a682e706e67](https://camo.githubusercontent.com/999e6cab5460a6907ee14c7b32064d995e6ecbb39505fdf57b2cb7720f8a0cd4/68747470733a2f2f692e737461636b2e696d6775722e636f6d2f5647676a682e706e67)

### **Private**

Can only be accessed by code in the **same class or struct**.

![https://camo.githubusercontent.com/3a66dadd4d00743045953c7d9aafebb4968d29327402bec2bb0bb9011db315c0/68747470733a2f2f692e737461636b2e696d6775722e636f6d2f5364654d392e706e67](https://camo.githubusercontent.com/3a66dadd4d00743045953c7d9aafebb4968d29327402bec2bb0bb9011db315c0/68747470733a2f2f692e737461636b2e696d6775722e636f6d2f5364654d392e706e67)

### **Protected**

Can only be accessed by code in the **same class or struct**, or in a **derived class**.

![https://camo.githubusercontent.com/108026b1bf6df973e051f88581a4c616b9068acd91fcbd44dffb919eac724741/68747470733a2f2f692e737461636b2e696d6775722e636f6d2f756e694f752e706e67](https://camo.githubusercontent.com/108026b1bf6df973e051f88581a4c616b9068acd91fcbd44dffb919eac724741/68747470733a2f2f692e737461636b2e696d6775722e636f6d2f756e694f752e706e67)

**Internal**

Can be accessed by any code in the **same assembly**, but *not* from another assembly.

![https://camo.githubusercontent.com/44f408fd8f4938df848ffce23155764ec8a18f690a24caf595862898d087444a/68747470733a2f2f692e737461636b2e696d6775722e636f6d2f386f37446d2e706e67](https://camo.githubusercontent.com/44f408fd8f4938df848ffce23155764ec8a18f690a24caf595862898d087444a/68747470733a2f2f692e737461636b2e696d6775722e636f6d2f386f37446d2e706e67)

### **Protected internal**

Can be accessed by any code in the **same assembly**, or by any **derived class in another assembly**. `protected` outside (the same assembly) `internal` inside (same assembly)

![https://camo.githubusercontent.com/50bfb6dd5a179fa1d96fb82c3fea1f397c75d8b96ebcdf4d52a821a19c2d0276/68747470733a2f2f692e737461636b2e696d6775722e636f6d2f56615151392e706e67](https://camo.githubusercontent.com/50bfb6dd5a179fa1d96fb82c3fea1f397c75d8b96ebcdf4d52a821a19c2d0276/68747470733a2f2f692e737461636b2e696d6775722e636f6d2f56615151392e706e67)

## **Static method vs Instance method**

```jsx
const v = new Point(0,0);
const u = new Point(4,5);
```

**Static method**

- defined on an object, but it doesn't change properties of the object
- returns value
- ex. `Math.sum(2, 5)`

```jsx
Point.add = function(v1, v2) {
  return new Point(v1.x + v2.x, v1.y + v2.y);
};

const result = Point.add(v, u);
```

**Instance method**

- instantiation of a class
- Object is changed

```jsx
Point.prototype.add = function(v) {
    this.x += v.x;
    this.y += v.y;
 };

v.add(u);
```

*..an instance is an individual instantiation of a class and is fundamentally different from a class. In JavaScript, "instance" does not have this technical meaning because JavaScript does not have this difference between classes and instances.*

```
instantiate means the class is implemented when creating it, by constructor

so usually we say class and instance is different but in js, they don't have this kind of meaning... so the sample codes looks like a mock..
```
## Singleton pattern vs Single Instance

Singleton restricts the instantiation of a class to one "single" instance.

It just specifies that wherever you’re normally using singleton objects, you should consider just having a single instance

- A `singleton` is a class that enforces the rule that there can only be a single object of it and most often that object can be accessed throughout the program.
- A `single instance` on the other hand means that the class itself is not a singleton, but (on a higher level), you just make sure there is only one instance.

### Difference between

- Using singleton pattern is more explicit way to use as a single object
- Singleton is hard to use in TDD since every test runs in isolation and the environment is reset between them.

```
And I came up with another q, about singleton pattern and single instance.

you can make many instances from a class, 
```

## Reference

- [http://devmonologue.com/design-patterns/singleton-vs-single-instance](http://devmonologue.com/design-patterns/singleton-vs-single-instance)
- [https://www.khanacademy.org/computing/computer-programming/programming-natural-simulations/programming-vectors/a/static-functions-vs-instance-methods](https://www.khanacademy.org/computing/computer-programming/programming-natural-simulations/programming-vectors/a/static-functions-vs-instance-methods)
- [https://developer.mozilla.org/en-US/docs/Web/JavaScript/Guide/Details_of_the_Object_Model](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Guide/Details_of_the_Object_Model)
- [https://docs.microsoft.com/en-us/dotnet/standard/assembly/](https://docs.microsoft.com/en-us/dotnet/standard/assembly/)