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

Logging?
========

What Does It Mean?
------------------

Differences To Metrics
----------------------

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
