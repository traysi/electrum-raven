Electrum-rvn - Lightweight Ravencoin client
=====================================

::

  Licence: MIT Licence
  Author: Thomas Voegtlin
  Port Maintainer: standadout-error (Electrum-rvn)
  Language: Python (>= 3.6)
  Homepage: https://ravencoin.org/


.. image:: https://minermore.com/images/ravencoin.svg
    :width: 100px
    :target: https://github.com/standard-error/electrum-raven
    :alt: Build Status


Getting started
===============

Electrum-raven is a pure python application. If you want to use the
Qt interface, install the Qt dependencies::

    sudo apt-get install python3-pyqt5

If you downloaded the official package (tar.gz), you can run
Electrum-raven from its root directory, without installing it on your
system; all the python dependencies are included in the 'packages'
directory. To run Electrum-raven from its root directory, just do::

    ./run_electrum

You can also install Electrum-raven on your system, by running this command::

    sudo apt-get install python3-setuptools
    python3 -m pip install .[fast]

This will download and install the Python dependencies used by
Electrum-raven, instead of using the 'packages' directory.
The 'full' extra contains some optional dependencies that we think
are often useful but they are not strictly needed.

If you cloned the git repository, you need to compile extra files
before you can run Electrum-raven. Read the next section, "Development
Version".



Development version
===================

Check out the code from GitHub::

    git clone https://github.com/wakiyamap/electrum-raven.git
    cd electrum-raven

Need x16r_hash::

    pip3 install https://github.com/traysi/x16r_hash/releases/download/1.0/1.0.zip

Run install (this should install dependencies)::

    python3 -m pip install .[fast]

Render the SVG icons to PNGs (optional)::

    for i in lock unlock confirmed status_lagging status_disconnected status_connected_proxy status_connected status_waiting preferences; do convert -background none icons/$i.svg icons/$i.png; done

Compile the icons file for Qt::

    sudo apt-get install pyqt5-dev-tools
    pyrcc5 icons.qrc -o electrum/gui/qt/icons_rc.py

Compile the protobuf description file::

    sudo apt-get install protobuf-compiler
    protoc --proto_path=electrum --python_out=electrum electrum/paymentrequest.proto

Create translations (optional)::

    sudo apt-get install python-requests gettext
    ./contrib/make_locale




Creating Binaries
=================


To create binaries, create the 'packages' directory::

    ./contrib/make_packages

This directory contains the python dependencies used by Electrum-raven.

Mac OS X / macOS
--------

See `contrib/build-osx/`.

Windows
-------

See `contrib/build-wine/`.


Android
-------

See `electrum/gui/kivy/Readme.md` file.
