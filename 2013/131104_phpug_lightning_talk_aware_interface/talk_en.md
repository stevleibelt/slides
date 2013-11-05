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

---

## AwareInterface, For What?

* dependency injection (also known as "interface injection" [0])
* declare dependencies via interfaces to easy up reading classes
* count dependencies of "MyClass" via "grep -r 'MyClassAwareInterface' source/"

---

## Dependency Injection? But There Are Other Types Also! [1]

### Constructor Injection 

* + object is in a ready state
* + object declares complexity up front
* +/- dependencies can not be swapped after instantiation 
* - can lead to cyclical dependencies 
* - dependencies are not polymorphic
* - there is a parameter per dependency
* - constructors are not part of the liskov substitutaion principle [5]

---

### Setter Injection

* + one injection point per dependency
* +/- its hard to distinguish between mandatory and optional dependencies
* - consumer has to be very honest to inject all dependencies

---

### Interface Injection

* + increase readability of class structure
* + one injection point per dependency
* + interface injection class to lead to a rule to distinguish between mandatory and optiona dependencies
* + could only consist of a "injectMyClass" method
* - could lead to a lot of consumed interfaces
* - consumer has to be very honest to inject all dependencies

---

### 


## Source

[0](http://avalanche123.com/blog/2010/10/01/interface-injection-and-symfony2-dic/)
[1](http://www.slideshare.net/ralphschindler/zend-di-in-zf-20)
[2](http://martinfowler.com/articles/injection.html#InterfaceInjection)
[3](http://ieeexplore.ieee.org/xpl/login.jsp?tp=&arnumber=1636252&url=http://ieeexplore.ieee.org/iel5/10902/34302/01636252.pdf?arnumber=1636252)
[4](http://de.wikipedia.org/wiki/Dependency_Injection)
[5](http://en.wikipedia.org/wiki/Liskov_substitution_principle)
[7](http://api.symfony.com/2.0/Symfony/Component/DependencyInjection/ContainerAwareInterface.html)
[8](http://stackoverflow.com/questions/6188466/what-is-aware-when-should-i-include-in-my-class-name)

## Was Ist Ein AwareInterface Und Wofür Brauch Ich Es?

## Wann Benutzte Ich eIn Aware Interface?

https://github.com/php-loep/di/issues/3

## Vorteile

## Nachteile

## Eure Meinung
