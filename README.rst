steamfiles
==========

.. image:: https://badge.fury.io/py/steamfiles.svg
    :target: http://badge.fury.io/py/steamfiles
    :alt: Latest version

.. image:: https://travis-ci.org/leovp/steamfiles.svg?branch=master
    :target: https://travis-ci.org/leovp/steamfiles
    :alt: Travis-CI

| Python library for parsing the most common Steam file formats.
| The library has a familiar JSON-like interface: ``load()`` / ``loads()`` for loading the data,
| and ``dump()`` / ``dumps()`` for saving the data back to the file.

Format support
--------------

+-------------+-------+-------+
|             | Read  | Write |
+-------------+-------+-------+
| acf         | **+** | **+** |
+-------------+-------+-------+
| appinfo.vdf | **+** | **+** |
+-------------+-------+-------+
| Manifest    | **+** | **+** |
+-------------+-------+-------+

Quickstart
----------

`steamfiles` requires Python 3.3+

Install the latest stable version:

::

    pip install steamfiles

Import a module for your desired format:
::

    # Use one of these, or all at once!
    from steamfiles import acf
    from steamfiles import appinfo
    from steamfiles import manifest

Easily load data, modify it and dump back:
::

    with open('appinfo.vdf', 'rb') as f:
        data = appinfo.load(f)
        
    # Calculate the total size of all apps.
    total_size = sum(app['size'] for app in data.values())
    print(total_size)
    
    # Downgrade a change number for all apps.
    for app in data.values():
        app['change_number'] -= 1
    
    with open('new_appinfo.vdf', 'wb') as f:
        appinfo.dump(data, f)

Documentation
-------------

`ACF format overview <https://github.com/leovp/steamfiles/blob/master/docs/acf_overview.rst>`_

More in progress…

TODO
----

- [✓] ACF support
- [✓] appinfo.vdf support (Binary VDF)
- [✓] Manifest support
- [?] packageinfo.vdf (Another binary VDF)
- [?] UserGameStats (achievements)
- [?] Text VDF files (are they actually ACF?)

License
-------

`steamfiles` is distributed under the terms of the MIT license.

See the bundled `LICENSE <https://github.com/leovp/steamfiles/blob/master/LICENSE>`_ file for more details.

