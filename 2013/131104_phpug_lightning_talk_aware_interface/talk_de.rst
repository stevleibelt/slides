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

Wer bin Ich?
============

* `Stev Leibelt`_
* PHP developer
* Großer Freund von `open source`_
* Mag Wörter wie:
    * "Linux"
    * "[L]GPL"
    * "ZFS"
    * "Gang Of Four"
    * "`free as in freedom, not as in beer`_."
* Wurde im schönsten `Freistaat`_ geboren :-)
* Arbeitet für eine Firma mit einem Hauptprodukt (und ja, es gibt noch alten Quelltext ;-))

.. _Stev Leibelt: http://stev.leibelt.de
.. _open source: http://opensource.org/licenses
.. _free as in freedom, not as in beer: http://theopensourceschool.blogspot.de/2010/01/free-as-in-freedom-not-as-in-free-beer.html
.. _Freistaat: http://de.wikipedia.org/wiki/Sachsen

----

Um was geht es in diesem Vortrag?
=================================

* Kurze Auffrischung was Dependency Injection ist
* Anmerkung wie man lesbaren Quelltext schreiben kann
* Philosophieren und Interpretieren von Wörtern ;-)
* Daran zu erinnern, dass es noch immer eine Welt ohne "DIC" [5] gibt

----

:data-x: r0
:data-y: r500
:data-scale: 0.1

AwareInterface?
===============

* Sie vereinfachen Dependency Injection
* Sind ebenfalls als "Interface Injection" [0], [2] bekannt
* Abhängigkeiten durch Interfaces zu deklarieren, vereinfacht das Lesen der Klasse
* Definiert den Weg, wie ein Objekt injiziert wird
* Benennt alle "beweglichen Teile"
* Vereinfacht das Zählen der Abhängigkeiten durch "grep -r 'MyClassAwareInteface' source/"

----

:data-rotate: 90

Dependency Injection?
=====================

Aber es gibt noch mehrere Wege! [1]

----

Constructor Injection 
---------------------

* \+ Objekt ist in einem benutzbaren Stadium
* \+ Objekt deklariert die Komplexität im Voraus
* +/- Abhängigkeiten können nicht nachträglich geändert werden
* \- Kann zu zyklischen Abhängigkeiten führen
* \- Ein Parameter pro Abhängigkeit
* \- Konstruktoren sind nicht Teil des Liskov Substitutaion Principle [4] (Totschlagkriterium!)

----

Setter Injection
----------------

* \+ Ein Weg zur Injizierung pro Abhängigkeit
* \- Kein definierter Weg wie eine Abhängigkeit injiziert wird
* \- Es ist schwer zwischen optionalen und zwingenden Abhängigkeiten zu unterscheiden
* \- Verbraucher muss sich sicher sein alle Abhängigkeiten injiziert zu haben

----

Interface Injection (Ein spezieller Setter Injection)
-----------------------------------------------------

* \+ Erhöht die Lesbarkeit der Klasse
* \+ Eine definierte Art wie man eine Abhängigkeit injiziert
* \+ Interface Injection kann zu einer projektweiten Regel führen wie man optionale und zwingende Abhängigkeiten bezeichnet
* \+ Vereinfacht das Einbauen von "DI" [3] in alten Quelltext (durch hart verdrahten einer Prüfungen wie "instanceof MyClassAwareInterface" [9])
* \- Kann zu vielen Interface Definitionen führen
* \- Verbraucher muss sich sicher sein alle Abhängigkeiten injiziert zu haben

----

:data-x: r-800
:data-scale: 1
   
AwareInterface Das Gleiche Wie InjectionInterface?
==================================================

* Nein (zumindest nicht für mich)
* Injection Interface definiert den Weg wie ein Typ/Objekt als Abhängigkeit injizieren wird
* Ein Aware Interface sollte mehr sein

----

:data-y: r1000

Was meinst du mit "mehr"?
=========================

* "Bewusstsein impliziert das Wissen gesammelt durch die eigene Erkenntnisse oder mittels erhaltener Informationen" [8]
* Es sollte wenigst die ersten zwei Methoden beinhalten [7]:
    * "setMyClass(MyClassInterface $myClass)"
    * "getMyClass()"
    * "hasMyClass()" (optional)
* Falls "hasMyClass()" definiert ist, sollte die Abhängigkeit optional sein
* Falls die Abhängigkeit zwingend ist, könnte der Name des Interfaces auf "InjectInterface" oder "DependendInterface" enden

----

Optionale Abhängigkeiten?
=========================

* Beispielsweise wird kein Logger injiziert gibt es kein Logging, aber der Code funktioniert weiterhin
    * Vereinfacht das Unittesten (wie "DI" im Allgemeinen)
* Implementierung von neuen, optionalen Funktionalitäten und einfaches Ausprobieren (ohne großem Aufwand)
    * Einfaches entfernen von unpraktischen Funktionalitäten

----

:data-x: r-800
:data-scale: 1
:data-rotate: -90

Fragen?
=======

Ich hab welche :-)
------------------

* Nutzt ihr AwareInterfaces oder InjectionInterfaces (warum, warum nicht?)
* Wie verdeutlicht ihr optionale und zwingende Abhängigkeiten?

----

:data-rotate: -90

Eure Meinung?
=============

----

:data-rotate: 270

Dankeschön!
===========

----

:data-y: 1000

Quellen
=======

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
