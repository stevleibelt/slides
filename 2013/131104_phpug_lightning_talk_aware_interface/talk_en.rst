:title: Lightningtalk AwareInterface
:data-transition-duration: 1500

Under licence of LGPL-3. You can get the source from: https://github.com/stevleibelt/slides/tree/master/2013/131104_phpug_lightning_talk_aware_interface
Based on the example: https://hovercraft.readthedocs.org/en/1.0/_sources/examples/hovercraft.txt - http://regebro.github.io/hovercraft
Based on the docs:
https://hovercraft.readthedocs.org/en/1.0/
http://docutils.sourceforge.net/docs/user/rst/quickref.html
http://en.wikipedia.org/wiki/ReStructuredText

----

Lightningtalk AwareInterface
============================

12.11.2013   
PHPUserGroup Hamburg   

----

:data-y: r1000

Who I Am?
=========

* `Stev Leibelt`_
* PHP developer
* big fan of `open source`_
* loves words like:
    * "Linux"
    * "[L]GPL"
    * "ZFS"
    * "Gang Of Four"
    * "`free as in freedom, not as in beer`_."
* was born in the moste beautiful `free state`_ :-)
* working for a company with one main product (and yes, old code exists ;-))

.. _Stev Leibelt: http://stev.leibelt.de
.. _open source: http://opensource.org/licenses
.. _free as in freedom, not as in beer: http://theopensourceschool.blogspot.de/2010/01/free-as-in-freedom-not-as-in-free-beer.html
.. _free state: http://en.wikipedia.org/wiki/Saxony

----

What Is This Talk About?
========================

* short reminder of dependency injection (automatically and "by hand")
* add some thoughts about how to write easy to read code
* philosophy and interpretion of words ;-)
* remind you about the fact that there is a world without "DIC" [5] out there

----

:data-x: r0
:data-y: r500
:data-scale: 0.1

AwareInterface?
===============

* they are good for dependency injection
* also known as "interface injection" [0], [2]
* declaring dependency via interface simplifies the reading of a class
* defines the way of injecting an object "MyClass"
* explains what the code expects [6]
* names all the "moving parts"
* easy up counting of dependencies via "grep -r 'MyClassAwareInterface' source/"

----

:data-rotate: 90

Dependency Injection?
=====================

But There Are Other Types Also! [1]

----

Constructor Injection 
---------------------

* \+ object is in a ready state
* \+ object declares complexity up front
* +/- dependencies can not be swapped after instantiation 
* \- can lead to cyclical dependencies 
* \- there is a parameter per dependency
* \- constructors are not part of the liskov substitutaion principle [4] (killer phrase!)

----

Setter Injection
----------------

* \+ one injection point per dependency
* \- no defined way how to inject "MyClass" into the code
* \- its hard to distinguish between mandatory and optional dependencies
* \- consumer has to be very honest to inject all dependencies

----

Interface Injection (A Special Setter Injection)
------------------------------------------------

* \+ increases the readability of a class structure
* \+ is a defined injection point and way per dependency
* \+ interface injection could lead to a project based rule to distinguish between mandatory and optional dependencies
* \+ simplifies way for implementing "DI" [3] in old code (by hard coding some "instanceof MyClassAwareInterface" checks [9])
* \- could lead to a lot of consumed interfaces
* \- consumer has to be very honest to inject all dependencies

----

:data-x: r-800
:data-scale: 1
   
AwareInterface Equals InterfaceInjection?
=========================================

* no (at least not for me)
* injection interface defines a way to inject a typ/object as dependency
* aware interface should do a bit more

----

:data-y: r1000

What Is This "Bit More"?
========================

* "Aware implies knowledge gained through one's own perceptions or by means of information" [8]
* it should contain two or three methods [7]:
    * "setMyClass(MyClassInterface $myClass)"
    * "getMyClass()"
    * "hasMyClass()" (optional)
* if it contains a "hasMyClass()" method, the dependency should be optional
* if dependency is mandatory, the name of the interface could be "InjectInterface" or "DependendInterface"

----

Optional Dependencies?
======================

* for example, no logger injected leads to no logging but still working code
    * speed up and simplifies unittests (as "DI" in general)
* create a new feature and try to test it (without big refactoring)
    * easy up removing of impractical features

----

:data-x: r-800
:data-scale: 1
:data-rotate: -90

Questions?
==========

I Have Some :-)
---------------

* are you using aware/injection interfaces (why/why not)?
* how do you clear up optional and mandatory dependencies?

----

:data-rotate: -90

Your Opinion?
=============

----

:data-rotate: 270

Thanks!
=======

----

:data-y: 1000

Source
======

0) `Interface Injection And Symfony 2 DIC`_   
1) `Zend DI In ZF 2`_
2) `Interface Injection By Uncle Bob`_
3) `Dependency Injection`_
4) `Liskov Substitution Principle`_
5) `Symfony 2 And The Container Aware Interface`_
6) `What Is Aware And When Should I Implement It`_
7) `Thoughts About AwareInterface`_
8) `The Free Dictonary`_
9) `PHP Loep`_

.. _Interface Injection And Symfony 2 DIC: http://avalanche123.com/blog/2010/10/01/interface-injection-and-symfony2-dic/
.. _Zend DI In ZF 2: http://www.slideshare.net/ralphschindler/zend-di-in-zf-20
.. _Interface Injection By Uncle Bob: http://martinfowler.com/articles/injection.html#InterfaceInjection
.. _Dependency Injection: http://en.wikipedia.org/wiki/Dependency_Injection
.. _Liskov Substitution Principle: http://en.wikipedia.org/wiki/Liskov_substitution_principle
.. _Symfony 2 And The Container Aware Interface: http://api.symfony.com/2.0/Symfony/Component/DependencyInjection/ContainerAwareInterface.html
.. _What Is Aware And When Should I Implement It: http://stackoverflow.com/questions/6188466/what-is-aware-when-should-i-include-in-my-class-name
.. _Thoughts About AwareInterface: http://artodeto.bazzline.net/archives/418-some-thoughts-about-AwareInterfaces-and-InjectorInterfaces.html
.. _The Free Dictonary: http://www.thefreedictionary.com/aware
.. _PHP Loep: https://github.com/php-loep/di/issues/3
