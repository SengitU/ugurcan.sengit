---
title: "Case Classes in Scala"
slug: "case-classes-in-scala"
tags: ["scala", "Apprenticeship"]
date: 2018-04-17
---

In my professional working life, I've mostly used Javascript, and some Java as flavor on the plate. Maybe because of my lack of experience or Scala's more detailed specifications, some features of the language confuses me until I understand why do we need them. After that, I question how did we handle business without that features.

Case classes in conjunction with pattern matching is one of the shiny features. Let me define them first;

```scala
trait Flight

case class OneWayFlight(from: String, to: String, departureTime: LocalDateTime) extends Flight
case class RoundTripFlight(from: String, to: String, departureTime: LocalDateTime,
                         returnTime: LocalDateTime) extends Flight
case class TransitFlight(from: String, through: String, to: String, departureTime: LocalDateTime,
                         returnTime: LocalDateTime) extends Flight
```

With my limited Scala knowledge, I pretend `trait`s as `interface`s in Java. Of course, traits are more than that, but it's a subject for another post. So, we have defined different types of flights by extending `Flight` trait. Each case class has different construction parameters, so we will need to handle these classes according to their properties.

Assume that, we would like to group vacations by their duration, which is `returnTime - depatureTime` is not applicable for OneWayFlight, but the Objects we accept are Flight types. How can we implement this? If it was Java, I would write a pseudo control statement as follows;

```java
method calculateDuration(flights) {
  for(flight in Flights) {
    if(flight instanceof OneWayFlight) {
      ...
    } else if(flight instanceof RoundTripFlight || flight instanceof TransitFlight) {
      ...
    }
  }
}
```

Of course there might be better ways to handle this problem, but in Java, if I add another type of flight, **compiler will not remind me to add new type** to this code snippet. In Scala, we would write the following;

```scala
def aggregateFlights(flights: Seq[Flight]): Seq[Flight] = {
  flights.groupBy {
    case OneWayFlight => None
    case RoundTripFlight => ...
    case TransitFlight => ...
  }
}
```

So, Scala compiler is aware of the implementations of Flight trait, and by this way, we are able to use pattern matching with our case classes. This might seem like just a syntactic sugar, but it's way more than that. First of all, a colleague might add a new type of flight without knowing this method. But, in such case, scala compiler raises a warning during compile time, pointing out the unmatched case classes. This is called `exhaustiveness check` and could really prevent you from bugs.

Another thing to point out, in Scala traits, you have an option to `seal` trait's scope to that file. If I change `trait Fligth` to `sealed trait Flight` it will not be able to reach outside of the file. But, how could it help me? It keeps your types together and most importantly, it increases the compiler performance. Compiler will check for implementations of the trait, if you seal it, compiler will only check that file, otherwise I assume it will check every tree, but I am not sure about this part.
