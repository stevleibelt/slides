# Lightningtalk The AwareInterface

12.11.2013
PHPUserGroup Hamburg

---

## Who Am I

* [Stev Leibelt](http://stev.leibelt.de/)
* PHP developer
* big fan of [open source](http://opensource.org/licenses)
* loves words like:
    * "Linux"
    * "BSD"
    * "[L]GPL"
    * "ZFS"
    * "Composer"
    * "Gang Of Four"
    * "KISS"
    * "[free as in freedom, not as in beer.](http://theopensourceschool.blogspot.de/2010/01/free-as-in-freedom-not-as-in-free-beer.html)"
* was born in the moste beautiful [free state](http://en.wikipedia.org/wiki/Saxony) :-)
* working for a company with one main product (and yes, old code exists ;-))

---

## What Is This Talk About

* write easy to read code
* dependency injection (automatically and "by hand")
* philosophy and interpretion of words ;-)
* keep in mind, there is a world without "DIC" [5] out there

---

## AwareInterface, For What?

* dependency injection (also known as "interface injection" [0], [2])
* declare dependencies via interfaces to easy up reading classes
* explains what the code expects [6]
* you only have to read the "implements" section to know all the dependencies
* names all the "moving parts"
* easy up counting of dependencies via "grep -r 'MyClassAwareInterface' source/"

---

## Dependency Injection? But There Are Other Types Also! [1]

### Constructor Injection 

* + object is in a ready state
* + object declares complexity up front
* +/- dependencies can not be swapped after instantiation 
* - can lead to cyclical dependencies 
* - dependencies are not polymorphic
* - there is a parameter per dependency
* - constructors are not part of the liskov substitutaion principle [4]

---

### Setter Injection

* + one injection point per dependency
* +/- its hard to distinguish between mandatory and optional dependencies
* - consumer has to be very honest to inject all dependencies

---

### Interface Injection (A Special Setter Injection)

* + increase readability of class structure
* + one injection point per dependency
* + interface injection class to lead to a rule to distinguish between mandatory and optiona dependencies
* + could only consist of a "injectMyClass" method
* + easy way for implementing "DI" [3] in old code (by hard coding some "instanceof MyClassAwareInterface" checks [9])
* - could lead to a lot of consumed interfaces
* - consumer has to be very honest to inject all dependencies

---

## AwareInterface === Interface Injection?

* no (at least not for me)
* injection interface defines a method to inject a typ/object as dependency
* aware interface should do a bit more

---

### My Ideal World

* "Aware implies knowledge gained through one's own perceptions or by means of information" [8]
* should contain two or three methods [7]:
    * "setMyClass(MyClassInterface $myClass)"
    * "getMyClass()"
    * "hasMyClass()" (optional)
* if "hasMyClass()" is defined in the interface, the dependency should be optional
* if dependency is mandatory, the name of the interface should be "InjectInterface" or "DependendInterface"

---

## Optional Dependencies?

* for example, no logger injected leads to no logging but still working code
    * speed and easy up unittests (as "DI" in general)
* create a new feature and try to test it (without big refactoring)
    * easy up removing of impractical features

## Again, AwareInterface For What?

---

## Questions?

## Your Opinion?

* are you using aware/injection interfaces (why/why not)?
* how do you clear up optional and mandatory dependencies?

## Thanks!

---

## Source

[0](http://avalanche123.com/blog/2010/10/01/interface-injection-and-symfony2-dic/)
[1](http://www.slideshare.net/ralphschindler/zend-di-in-zf-20)
[2](http://martinfowler.com/articles/injection.html#InterfaceInjection)
[3](http://de.wikipedia.org/wiki/Dependency_Injection)
[4](http://en.wikipedia.org/wiki/Liskov_substitution_principle)
[5](http://api.symfony.com/2.0/Symfony/Component/DependencyInjection/ContainerAwareInterface.html)
[6](http://stackoverflow.com/questions/6188466/what-is-aware-when-should-i-include-in-my-class-name)
[7](http://artodeto.bazzline.net/archives/418-some-thoughts-about-AwareInterfaces-and-InjectorInterfaces.html)
[8](http://www.thefreedictionary.com/aware)
[9](https://github.com/php-loep/di/issues/3)
