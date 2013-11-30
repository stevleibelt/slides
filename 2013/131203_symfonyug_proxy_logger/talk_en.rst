:title: Proxy Logger Component
:data-transition-duration: 1500

Under licence of LGPL-3. You can get the source from: https://github.com/stevleibelt/slides/tree/master/2013/131203_symfinyug_proxy_logger
Based on the example: https://hovercraft.readthedocs.org/en/1.0/_sources/examples/hovercraft.txt - http://regebro.github.io/hovercraft
Based on the docs:
https://hovercraft.readthedocs.org/en/1.0/
http://docutils.sourceforge.net/docs/user/rst/cheatsheet.txt
http://docutils.sourceforge.net/docs/user/rst/quickref.html
http://en.wikipedia.org/wiki/ReStructuredText

----

Proxy Logger Component
======================

| 03.12.2013  
| `Symfony User Group Hamburg`
| `mindworks GmbH`

.. _mindworks GmbH: http://www.mindworks.de
.. _Symfony User Group Hamburg: http://www.meetup.com/sfughh/events/143293602

:data-y: r1000

----

Logging Or Do You Mean Metrics?
===============================

What Does It Mean?
------------------

* measuring of data
* record of data

----

Logging?
--------

    In computing, a logfile or simply log is a file that records events taking place in the execution of a system in order to provide an audit trail that can be used to understand the activity of the system and to diagnose problems. The act of keeping a logfile is called logging. (`[0]`)

.. _[0]: http://en.wikipedia.org/wiki/Logfile

----

Metrics?
--------

    A software metric is a measure of some property of a piece of software or its specifications [...] 
    The goal is obtaining objective, reproducible and quantifiable measurements, which may have numerous valuable applications in schedule and budget planning, cost estimation, quality assurance testing, software debugging, software performance optimization, and optimal personnel task assignments. (`[0]`)

.. _[0]: http://en.wikipedia.org/wiki/Software_metric

Writing Of History?
-------------------

* recoding of events like:
    * user (id 3) had registerd with link "http://www.foo.bar/my-add-uuid-123"
    * user (id 3) purchased contract (id 9) 

----

And Graylog2 Is (As An Example)?
--------------------------------

    Graylog2 is for data analysis (`[0]`)

.. _[0]: http://www.graylog2.org/

----

So What Do I Mean With Logging?
-------------------------------

* record of workflow
* record of processed data
* dump of processed data if something went wrong
* the more it went wrong, the more i want to get dumped
* logging per instance (webserver)
* dumping process data? secure your logfiles!

----

Why At A Symfony UserGroup?
===========================

.. code:: php

    "symfony/event-dispatcher": "v2.3.5"    //since version 1.2.0 :-)

How I Came To The Idea?
=======================

----

What It Can
===========

.. use Comparison Between Normal Logger And Trigger Flush Buffer Logger

----

What It Can Not
===============

----

Common Terms
============

.. https://github.com/stevleibelt/php_component_proxy_logger/blob/master/documentation/CommonTerms.md

----

Components
==========

.. https://github.com/stevleibelt/php_component_proxy_logger/blob/master/documentation/Components.md

----

Installation
============

Use `composer` and `packagist`.

.. code:: php

    require: "net_bazzline/component_proxy_logger": "dev-master"

.. _composer: http://getcomposer.org
.. _packagist: http://packagist.org

----

How To Use It?
==============

.. https://github.com/stevleibelt/php_component_proxy_logger/blob/master/documentation/MigrationTutorial.md

----

Crux?
=====

* do not log all
* structure your log
* explain your customer that they want metrics or history
* add bugs or remarks to the `component`
* joind the development `team`

.. _component: https://github.com/stevleibelt/php_component_proxy_logger
.. _team: https://github.com/bazzline

----

Questions?
==========

----

Your Opinion?
=============

----

Thanks!
=======

----

Version History?
================

.. https://github.com/stevleibelt/php_component_proxy_logger/blob/master/documentation/VersionHistory.md

----
