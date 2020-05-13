Installation
============

gr-satellites is a GNU Radio out-of-tree module, and it should be installed as
such. The general steps for installing gr-satellites include making sure that
all the dependencies are installed and then building and installing the
out-of-tree module.

Dependencies
^^^^^^^^^^^^

gr-satellites requires `GNU Radio`_ version at least 3.8.


.. warning::
   There are some build dependencies for GNU Radio out-of-tree modules that
   are not required to run GNU Radio, so some distributions might not install them
   by default when GNU Radio is installed. The main ones that may cause problems
   are:

   * swig
   * liborc (in Debian-based distributions ``liborc-0.4-0-dev`` is needed)

Additionally, the following libraries are required:

* `libfec`_
* `construct`_, at least version 2.9.
* `requests`_

.. note::
   libfec can be built and installed from its git repository by doing

   .. code-block:: console

      $ git checkout https://github.com/quiet/libfec
      $ cd libfec
      $ mkdir build
      $ cmake ..
      $ make
      $ sudo make install

   construct and requests are Python packages and can be installed with `pip`_
   by doing

   .. code-block:: console

      $ pip install --user --upgrade construct requests

   Alternatively, construct and requests can be installed from your
   distribution's package manager
 
.. _GNU Radio: https://gnuradio.org/
.. _libfec: https://github.com/quiet/libfec
.. _construct: https://construct.readthedocs.io/en/latest/
.. _requests: https://pypi.org/project/requests/
.. _pip: https://pypi.org/project/pip/

Optional dependencies
^^^^^^^^^^^^^^^^^^^^^

To use the realtime image decoders, gr-satellites needs `feh`_

.. _feh: https://feh.finalrewind.org/

.. note::
   feh is best installed through your distribution's package manager

Building and installing
^^^^^^^^^^^^^^^^^^^^^^^

gr-satellites can be built and installed using cmake:

.. code-block:: console

   $ mkdir build
   $ cd build
   $ cmake ..
   $ make
   $ sudo make install

After running ``make``, you can run the tests by doing ``make test`` in the
``build/`` directory.

PYTHONPATH
^^^^^^^^^^

After installing gr-satellites, it is necessary to ensure that Python is able
to locate the gr-satellites Python module. Depending on the configuration of
Python on and the location where gr-satellites has been installed, it might be
necessary to set the ``PYTHONPATH`` environment variable.

If Python is not able to locate the gr-satellites module, it will produce an
error like this:

.. code-block:: python

   ModuleNotFoundError: No module named 'satellites'

Often, gr-satellites is installed into ``/usr/local/lib/python3/dist-packages/``
or a similar directory, in a subdirectory called ``satellites``. Therefore,

.. code-block:: console

   $ export PYTHONPATH=/usr/local/lib/python3/dist-packages/

can be used to allow Python to find the gr-satellites module. More information
about the ``PYTHONPATH`` can be found in Python's documentation description of
the `PYTHONPATH`_.

.. _PYTHONPATH: https://docs.python.org/3/using/cmdline.html#envvar-PYTHONPATH

.. _Downloading sample recordings:

Downloading sample recordings
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

The ``satellite-recordings/`` directory is a `git submodule`_ that contains many
short sample recordings of different satellites that can be used to test the
decoders. The submodule can be clone (downloaded) by running

.. code-block:: console

   $ git submodule update --init

inside the ``gr-satellites/`` directory.

Alternatively, it is possible to run

.. code-block:: console

   $ git clone --recursive https://github.com/daniestevez/gr-satellites

when cloning the gr-satellites repository to download both gr-satellites and the
satellite-recordings submodule.

The satellite-recordings sample recordings can also be downloaded from its
`own git repository <https://github.com/daniestevez/satellite-recordings/>`_.

.. _git submodule: https://git-scm.com/book/en/v2/Git-Tools-Submodules