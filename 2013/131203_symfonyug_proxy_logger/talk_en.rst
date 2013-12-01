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

What Is This Talk About?
========================

* distinction between logging, metrics and writing of history
* present you a way of logging
* present you a logging component

----

Why At A Symfony UserGroup?
===========================

.. code:: php

    "symfony/event-dispatcher": "v2.3.5"    //since version 1.2.0 :-)

----

Logging, Metrics Or Writing Of History?
=======================================

I gain the feeling that things where mixing up.

----

What Does It All Mean?
----------------------

* analyse internal data
* archive internal data
* collect internal data
* meter internal data
* record internal data

----

Logging?
--------

    In computing, a logfile or simply log is a file that records events taking place in the execution of a system in order to provide an audit trail that can be used to understand the activity of the system and to diagnose problems. The act of keeping a logfile is called logging. (`[0]`)

.. _[0]: http://en.wikipedia.org/wiki/Logfile

----

Metrics?
--------

    A software metric is a measure of some property of a piece of software or its specifications [...] 
    The goal is obtaining objective, reproducible and quantifiable measurements, which may have numerous valuable applications in schedule and budget planning, cost estimation, quality assurance testing, software debugging, software performance optimization, and optimal personnel task assignments. (`[1]`)

.. _[1]: http://en.wikipedia.org/wiki/Software_metric

Writing Of History?
-------------------

* recoding of events like:
    * user (id 3) had registerd with link "http://www.foo.bar/my-add-uuid-123"
    * user (id 3) purchased contract (id 9) 
    * archive user interactions for the reason of law
* preserve status of a bunch of data
    * create graph of data transformation
    * record when happen what on which set of data

----

And Graylog2 (As An Example) Is?
--------------------------------

    Graylog2 is for data analysis (`[2]`)

So graylog is pure `web analytics` (doing all at once if you ask me).

.. _[2]: http://www.graylog2.org/
.. _web analytics: http://en.wikipedia.org/wiki/Web_analytics

----

What Do I Mean With Logging?
----------------------------

* record of workflow
* record of processed data
* dump of processed data if something went wrong
* the more it went wrong, the more i want to get dumped
* logging per instance (webserver)
* dumping process data? secure your logfiles!
* not meaning webserver log but web application log
* delete old log files or log entries without fear
* change log behaviour without fear
* split your logs into logical units (import/export/registration)

----

Confused?
---------

* figure out what your customer want
* your customer should know what to measure
    * avoid measure everything
    * do not interpret data by adding wished cross connections
* try to define common terms for your team and your customer
* separate you data
* create logger, history and metric writer (even if they are all simple file writer)

----

All I Want To Do Is To Do Logging
=================================

What I Struggled With
---------------------

* never found the right balance between logging enough to debug and do not glut the logfiles
* set loglevel to warning and you are loosing notice, info or debug
* set loglevel to info and your log file will be flooded with messages

What I Need
-----------

* if something goes wrong, "i want it all" (`[3]`)

.. [3]: http://en.wikipedia.org/wiki/I_Want_It_All

----

How To Solve This Problem?
==========================

Log all process data but only when something goes wrong.

----

Meaning?
--------

* buffer log entries
* clean or flush the buffer under well defined circumstances
* deal with (a collection of) psr3 loggers
* one log target (file/database column/whatever) per logical log unit (like import/purchase/migration)

----

History Of Development
----------------------

* so i searched and found nothing good for php
* started developing and released `version 0.9.0`
* it was working but, it looks like a `first draft` ;-)
* later on i stumbled over `monolog` and its `FingersCrossedHandler` (so i'm not alone with that concept of logging :-))
* monolog looks like a big, monolithic logging component (sorry if i'm wrong)
* big refactoring and implementation of event driven design leads to `version 1.2.0`
* story continues :-)

.. _version 0.9.0: https://github.com/stevleibelt/php_component_proxy_logger/tree/0.9.0
.. _version 1.2.0: https://github.com/stevleibelt/php_component_proxy_logger/tree/1.2.0
.. _monolog: https://github.com/Seldaek/monolog
.. _FingersCrossedHandler: https://github.com/Seldaek/monolog/tree/master/src/Monolog/Handler/FingersCrossed
.. _first draft: https://github.com/stevleibelt/php_component_proxy_logger/blob/master/documentation/VersionHistory.md

----

What It Is
==========

* defines a `log request` as a php object
* wraps your existing logger or loggers
* create a logger collection by using the `proxy logger`
* collect a bunch of log entries by using the `buffer logger`
* controll the buffer behaviour by using the `buffer manipulators`
* influence the process flow by using the build in `event system`
* be lazy, use the `factories`
* use the `IsValidLogLevel`
* follows `unix philosophy` (do one thing and do it well)
* you can enrich you existing logger component

.. _log request: https://github.com/stevleibelt/php_component_proxy_logger/blob/master/source/Net/Bazzline/Component/ProxyLogger/LogRequest/LogRequestInterface.php
.. _proxy logger: https://github.com/stevleibelt/php_component_proxy_logger/blob/master/source/Net/Bazzline/Component/ProxyLogger/Logger/ProxyLoggerInterface.php
.. _buffer logger: https://github.com/stevleibelt/php_component_proxy_logger/blob/master/source/Net/Bazzline/Component/ProxyLogger/Logger/BufferLoggerInterface.php
.. _buffer manipulators: https://github.com/stevleibelt/php_component_proxy_logger/tree/master/source/Net/Bazzline/Component/ProxyLogger/BufferManipulator
.. _event system: https://github.com/stevleibelt/php_component_proxy_logger/tree/master/source/Net/Bazzline/Component/ProxyLogger/Event
.. _factories: https://github.com/stevleibelt/php_component_proxy_logger/tree/master/source/Net/Bazzline/Component/ProxyLogger/Factory
.. _IsValidLogLevel: https://github.com/stevleibelt/php_component_proxy_logger/blob/master/source/Net/Bazzline/Component/ProxyLogger/Validator/IsValidLogLevel.php
.. _unix philosophy: http://en.wikipedia.org/wiki/Unix_philosophy

----

Showtime
========

Time for some `demo implementation`!

.. _demo implementation: https://github.com/stevleibelt/php_component_proxy_logger/blob/master/examples/Example/ManipulateBufferLogger/ExampleWithUpwardFlushBufferTriggerVersusNormalLogger.php

----

What It Is Not
==============

* it simple deals with log entries
* it does not care how to store
* it does not care where to store
* is not *the* logger component, just a part of it

----

Common Terms
============

* RealLogger represents a psr-3 logger
* LogRequest represents a log request (log level, message and context)
* LogRequestBuffer represents a collection of log requests that are not pushed to the real loggers
* ProxyLogger represents a collection of real loggers
* BufferLogger represents as a log request keeper that pass each log request to a buffer
* BypassBufferInterface represents a buffer manipulation to bypass a certain log level to all added real loggers
* FlushBufferTriggerInterface represents a buffer manipulation to trigger a buffer flush based on a log level

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

instead of
----------

.. code:: php

    class MyLoggerFactory
    {
        public function createMyProcessLogger()
        {
            return new Logger();
        }
    }

----

use this
--------

.. code:: php

    class MyLoggerFactory
    {
        public function createMyProcessLogger()
        {
            $realLogger = new Logger();

            //of course this should not be done on each create call
            $proxyLoggerFactory = new ProxyLoggerFactory();
            $proxyLogger = $proxyLoggerFactory->create($realLogger);

            return $proxyLogger;
        }
    }

.. https://github.com/stevleibelt/php_component_proxy_logger/blob/master/documentation/MigrationTutorial.md

----

What Else?
==========

If you have to deal with `log4php` loggers, use an `adapter`.

And the adapter works vica versa (super cool, put in a psr3 logger in an log4php environment).

.. _adapter: https://github.com/stevleibelt/php_component_psr_and_log4php_adapter
.. _log4php: https://logging.apache.org/log4php/

----

Crux?
=====

* do not log all
* structure your log
* explain your customer that they want metric or history
* add bugs or remarks to the `component`
* joind the development `team`

.. _component: https://github.com/stevleibelt/php_component_proxy_logger
.. _team: https://github.com/bazzline

----

Questions?
==========

* who is using monolog?
    * what are your experience?
    * positives
    * negatives?
* what loggers are you using?
* do you use your log files to create metrics?

----

Your Opinion?
=============

* how do you like the main idea of the component?

----

Thanks!
=======

