---
title: "Constructors in Scala"
slug: "constructors-in-scala"
tags: ["scala", "constructors", "auxiliary-constructors", "Apprenticeship"]
date: 2018-04-12
---

As I continue to learn `Scala` by the help of `Scala for the Impatient` book, I gain more insight about the language. First of all, Scala tries to minimize number of keystrokes required to achieve some functionality. Unlike Java, a class can be defiend as `class Name(val someVal: String)` or in a standart form like `class Name {}`, and almost every specialized format of defining things, has their own unique behaviours. I guess this yields confusion for the newcomers.

Return to the subject, constructors. Unlike Java, constructors don't have to have the same name with the class itself in Scala. I will start with, `auxiliary constructors`. Besides the fancy name, this type of constructors achieves same functionality with the constructor overloading. Auxiliary constructors can be chained with the other auxiliary constructor. If an auxiliary constructor is not chained with another one, it must be chained with the primary constructor. For example;

```scala
class Cat {
  private var name = ""
  private var age = 0

  // Auxiliary constructor for one param
  def this(name: String) {
    this() // Chained with the primary constructor
    this.name = name
  }

  // Auxiliary constructor for two params
  def this (name: String, age: Int) {
    this(name) // Chained with the one parameter auxiliary constructor
    this.age = age
  }
}

val strayCat = new Cat
val kavun = new Cat("Kavun")
val beyazPeynir = new Cat("Beyaz Peynir", 1)
```

There is also a `primary constructor`, which treats the class as a function and defines fields in the parameters. This would make you feel odd after Java, but I am living in the wondrous world of Javascript for four years now, I can get used to anything. For example, following is a primary constructor;

```scala
class Cat(val name: String, val age: Int) {
  println("Purr!")
  def describe = s"$name is $age years old"
}
```

At a first glance, code above seemed extremely odd to me. Scala merged primary constructor with the class definition itself. With this definition, when an instance instantiates from `Cat` class, `name` and `age`properties assigns immediately. In Javascript class syntax, we need to assign given name and age to the constructor `this.name = name`. Scala removed the `constructor` method and assignments with this handy syntax. It's not just that, the primary constructor executes all statements inside of the class, hence every created instance of `Cat` will `Purr!` in the example above.

In the example above, age is a `val` which we can't change, but it should be able to change each year. So, constructor could be rephrased like;

```scala
class Cat(val name: String, private var age: Int) {
  println("Purr!")
}
```

Yes, we can even decide if the field is private or not. Scala doesn't push developers to use this syntax, so if you don't like the syntax, you are still be able to build your constructors with auxiliary constructors. Does the merging constructor with the definition of class violates separation of concerns? I don't know, but I like this syntax. Besides, React also violates separation of concerns to a certain degree by combining HTML and Javascript.
