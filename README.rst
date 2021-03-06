weather-api
===========

|Build Status| |codecov|

A Python wrapper for the Yahoo Weather API.

With the API, you can get up-to-date weather information for any location, including 5-day forecast, wind, atmosphere, astronomy conditions, and more. You can lookup weather by woeid, city name or lat/long.

For more information, check out the `API documentation`_.

Install
-------

::

    pip install weather-api

Examples
--------

.. code:: python


    from weather import Weather, Unit
    weather = Weather(unit=Unit.CELSIUS)

    # Lookup WOEID via http://weather.yahoo.com.

    lookup = weather.lookup(560743)
    condition = lookup.condition()
    print(condition.text())

    # Lookup via location name.

    location = weather.lookup_by_location('dublin')
    condition = location.condition()
    print(condition.text())
    
    # Get weather forecasts for the upcoming days.

    forecasts = location.forecast()
    for forecast in forecasts:
        print(forecast.text())
        print(forecast.date())
        print(forecast.high())
        print(forecast.low())


CLI Usage
---------

.. code::

      usage: weather [-h] [--unit [{c,f}]] location

      positional arguments:
        location        The location to lookup.

      optional arguments:
        -h, --help      show this help message and exit
        --unit [{c,f}]

Example
~~~~~~~

.. code::
        
        $ weather dublin --u c
        
.. _API documentation: https://developer.yahoo.com/weather/

.. |Build Status| image:: https://travis-ci.org/AnthonyBloomer/weather-api.svg?branch=master
    :target: https://travis-ci.org/AnthonyBloomer/weather-api
.. |codecov| image:: https://codecov.io/gh/AnthonyBloomer/weather-api/branch/master/graph/badge.svg
    :target: https://codecov.io/gh/AnthonyBloomer/weather-api
