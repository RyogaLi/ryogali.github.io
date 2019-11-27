---
layout: post
title:  "Python Logging with the logging module"
tags: [Coding, Bioinformatics]
---

Updated: for python 3.7

For python 2.7, with file configuration 

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

[logger_testlog]
level=DEBUG
handlers=fHandler
qualname=testlog
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

[handler_fHandler]
class=FileHandler
level=DEBUG
formatter=simpleFormatter
args=("./main.log","a")
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

{% highlight python %}
# main.py
import logging
import logging.config

# load the root logger
# load the config file
# always use the absolute path, the error msgs of loggin are not very helpful
logging.config.fileConfig("path_to/logging.conf", disable_existing_loggers=False)
# get proper logger
log = logging.getLogger("root")

# if we change dir (change working directory) and create new logger, the 
# main.log will be created under that dir
# For example
# in module.py
from main import *
import logging
import logging.config
logging.config.fileConfig("path_to/logging.conf")

# get proper logger
log = logging.getLogger("testlog")

{% endhighlight %}



