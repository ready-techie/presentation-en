## Atomic Design

- Methodology, similar to nature🍃, for creating design systems

## 5 Distinct Levels

![five distinct levels in atomic design](https://bradfrost.com/wp-content/uploads/2013/06/atomic-design.png)

five distinct levels in atomic design

### 1. Atoms

- basic building block
- HTML tags, such as a form label, an input, or a button.
- abstract and often not useful on their own
- Atoms should not have margin or position value

### 2. Molecules

- groups of atoms bonded together and are the smallest fundamental units of a compound
- have their own properties

![http://bradfrost.com/wp-content/uploads/2013/06/molecule.jpg](https://bradfrost.com/wp-content/uploads/2013/06/atoms.jpg)

- molecules can be complex, as a rule of thumb they are relatively simple combinations of atoms built for **reuse**.

### 3. Organisms

- groups of molecules joined together to form a relatively complex, distinct section of an interface

![Organism](https://bradfrost.com/wp-content/uploads/2013/06/organism-examples.jpg)

- Building up from molecules to organisms encourages creating standalone, portable, **reusable** components

### 4. Templates

- consist mostly of groups of organisms stitched together to form pages

![http://bradfrost.com/wp-content/uploads/2013/06/template1.jpg](https://bradfrost.com/wp-content/uploads/2013/06/template1.jpg)

- very concrete and **provide context** to all these relatively abstract molecules and organisms.
- where clients start seeing the final design in place
- templates begin their life as HTML **wireframe**s, but over time increase fidelity to ultimately become the final deliverable.

### 5. Pages

- specific instances of templates.
- real representative content to give an accurate depiction of what a user will ultimately see.

![http://bradfrost.com/wp-content/uploads/2013/06/page1.jpg](https://bradfrost.com/wp-content/uploads/2013/06/page1.jpg)

- the highest level of fidelity and because they’re the most tangible

## Reference

- [https://bradfrost.com/blog/post/atomic-web-design/](https://bradfrost.com/blog/post/atomic-web-design/)
- [https://zoomkoding.github.io/디자인패턴/우아한테크캠프/2020/07/09/atomic-design-pattern.html](https://zoomkoding.github.io/%EB%94%94%EC%9E%90%EC%9D%B8%ED%8C%A8%ED%84%B4/%EC%9A%B0%EC%95%84%ED%95%9C%ED%85%8C%ED%81%AC%EC%BA%A0%ED%94%84/2020/07/09/atomic-design-pattern.html)
