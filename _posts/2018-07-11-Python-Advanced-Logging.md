---
layout: post
title:  "Python Advanced Logging"
tags: [Coding, Bioinformatics]
---

For python 2.7

0. Create the most basic configuration file for logging ( `logging.conf` )

```
[loggers]
keys=root,simpleExample

[handlers]
keys=consoleHandler

[formatters]
keys=simpleFormatter
```

* Create keys 

```
[logger_root]
level=DEBUG
handlers=consoleHandler

[logger_simpleExample]
level=DEBUG
handlers=consoleHandler
qualname=simpleExample
propagate=0
```

* Level:The logging functions are named after 
the level or severiy of the events they are 
used to track. The default level is WARNING, 
which means that only events of this level 
and above will be tracked
    * DEBUG - INFO - WARNING - ERROR - CRITICAL
    * 10 - 20 - 30 - 40 - 50
* handlers: which handler to use
* qualname: name of this logger, will be showing in the logging 
information if formatted
* propagate: 


```
[handler_consoleHandler]
class=StreamHandler
level=DEBUG
formatter=simpleFormatter
args=(sys.stdout,)
```

* Settings for the handler
* Class: read more about different types of [handlers](https://docs.python.org/2/howto/logging.html#useful-handlers)
    * StreamHandler: sends logging output to streams 
    such as sys.stdout, sys.stderr or any file-like object
* Formatter: the format of output string

```
[formatter_simpleFormatter]
format=%(asctime)s - %(name)s - %(levelname)s - %(message)s
```
* Format of the logger
* sample: 
``2005-03-19 15:38:55,977 - simpleExample - DEBUG - debug message``

2. Inside python script
# main.py
{% highlight python %}
import logging
import logging.config

# load the root logger
# load the config file
logging.config.fileConfig("./logging.conf")
# get proper logger
log = logging.getLogger("root")

# if we change dir (change working directory) and create new logger, the 

{% endhighlight %}

