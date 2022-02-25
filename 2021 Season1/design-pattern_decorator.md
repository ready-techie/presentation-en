# Design Pattern - Decorator

Created: Oct 29, 2020 7:59 PM (GMT)
Created by: Lee Anne
Tags: Design_Pattern

## Purpose

The design pattern comes from the problem on "Inheritance". The more we generate many subclasses to add new functions by using "Inheritance", the more hard it is to maintain the programs. Let's suppose the below example.

![IMG_0028](https://user-images.githubusercontent.com/15176192/115132486-b7acc580-a03b-11eb-9115-b8abc1128315.jpg)

What could we do for organizing those classes for the maintenance...?

It allows a behavior to be added to an individual object, without affecting the behavior of other objects from the same class.

Decorator could resolve two things:

1. Flexible to change while in run-time(In case of extensions, it only allows to be changed while in compile-time)

2. Follow OO design(Open for extensions, closed for modification)

- Object-Oriented 5 Principles

    Please, refer [SOLID principles](https://www.digitalocean.com/community/conceptual_articles/s-o-l-i-d-the-first-five-principles-of-object-oriented-design)

## Example Case

Here is the concept of using Decorator Design Pattern

![IMG_0029](https://user-images.githubusercontent.com/15176192/115132512-fb073400-a03b-11eb-8961-a2af242be5d1.jpg)

**Decorator adds its own behavior either before and/or after delegating to the object it decorates to do the rest of the job**

## How to design

Decorator uses "Composition"  rather than "Inheritance"

![IMG_0030](https://user-images.githubusercontent.com/15176192/115132520-08242300-a03c-11eb-999c-1612faff91f0.jpg)

In case of "double mocha soy latte with whip" beverage order

![IMG_0031](https://user-images.githubusercontent.com/15176192/115132527-13774e80-a03c-11eb-9f65-55d8a3bcdcbd.jpg)

## Code

Super class: Beverage , Child: Espresso

<img width="335" alt="Screen_Shot_2021-04-17_at_7 43 39_PM" src="https://user-images.githubusercontent.com/15176192/115132548-3efa3900-a03c-11eb-90e0-bc63363c4415.png">

<img width="419" alt="Screen_Shot_2021-04-17_at_7 44 12_PM" src="https://user-images.githubusercontent.com/15176192/115132565-65b86f80-a03c-11eb-9ca2-55920a99b2e8.png">

Decorator class: CondimentDecorator, Child: Mocha

<img width="498" alt="Screen_Shot_2021-04-17_at_7 43 56_PM" src="https://user-images.githubusercontent.com/15176192/115132551-4de0eb80-a03c-11eb-8bc0-66f74b9c2a98.png">

<img width="455" alt="Screen_Shot_2021-04-17_at_7 44 36_PM" src="https://user-images.githubusercontent.com/15176192/115132572-736df500-a03c-11eb-80a3-eef00edeeb11.png">

Test Result

<img width="658" alt="Screen_Shot_2021-04-17_at_8 18 31_PM" src="https://user-images.githubusercontent.com/15176192/115132590-884a8880-a03c-11eb-9753-cd9f54d94f02.png">

<img width="290" alt="Screen_Shot_2021-04-17_at_8 18 41_PM" src="https://user-images.githubusercontent.com/15176192/115132599-94364a80-a03c-11eb-8a2c-0d55ffa00eda.png">

You can check the example [Source code](https://www.wickedlysmart.com/head-first-design-patterns/) in here.

## Etc...

- Practical Usage: Java IO

![IMG_0032](https://user-images.githubusercontent.com/15176192/115132539-2b4ed280-a03c-11eb-8790-8fef2409853a.jpg)

- Weakness
    - Increase complexity when the developers add more Decorators
    - Try not to use Decorator but to use Factory or Adaptor design pattern as there should be multiple interface layers

## References

- [Head First Design Patterns: A Brain-Friendly Guide](https://www.notion.so/Design-Pattern-Decorator-db084d4e62c04faab02c25323ea63e26#14c67411c1bb4d018302c9425795d77b) by Eric Freeman
- [Wikipedia](https://en.wikipedia.org/wiki/Decorator_pattern)
