.. meta::
    :scope: user_only

==========================================
Install the OpenStack command-line clients
==========================================

Install the prerequisite software and the Python package for each
OpenStack client.

Install the prerequisite software
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Most Linux distributions include packaged versions of the command-line
clients that you can install directly, see Installing_from_packages_.

If you need to install the command-line packages source packages, the
following table lists the software that you need to have to run the
command-line clients, and provides installation instructions as needed.

+-----------------------+-----------------------------------------------------+
| Prerequisite          | Description                                         |
+=======================+=====================================================+
| Python 2.7 or later   | Currently, the clients do not support Python 3.     |
+-----------------------+-----------------------------------------------------+
| setuptools package    | Installed by default on Mac OS X.                   |
|                       |                                                     |
|                       | Many Linux distributions provide packages to make   |
|                       | setuptools easy to install. Search your package     |
|                       | manager for setuptools to find an installation      |
|                       | package. If you cannot find one, download the       |
|                       | setuptools package directly from                    |
|                       | http://pypi.python.org/pypi/setuptools.             |
|                       |                                                     |
|                       | The recommended way to install setuptools on        |
|                       | Microsoft Windows is to follow the documentation    |
|                       | provided on the setuptools website                  |
|                       | (https://pypi.python.org/pypi/setuptools#windows).  |
|                       | Another option is to use the unofficial binary      |
|                       | installer maintained by Christoph Gohlke            |
|                       | (http://www.lfd.uci.edu/~gohlke/pythonlibs/         |
|                       | #setuptools).                                       |
+-----------------------+-----------------------------------------------------+
| pip package           | To install the clients on a Linux, Mac OS X, or     |
|                       | Microsoft Windows system, use pip. It is easy to    |
|                       | use, ensures that you get the latest version of the |
|                       | clients from the                                    |
|                       | `Python Package Index <http://pypi.python.org/>`__, |
|                       | and lets you update or remove the packages later on.|
|                       |                                                     |
|                       | Since the installation process compiles source      |
|                       | files, this requires the related Python development |
|                       | package for your operating system and distribution. |
|                       |                                                     |
|                       | Install pip through the package manager for your    |
|                       | system:                                             |
|                       |                                                     |
|                       | **MacOS**                                           |
|                       |                                                     |
|                       | .. code::                                           |
|                       |                                                     |
|                       |   # easy_install pip                                |
|                       |                                                     |
|                       | **Microsoft Windows**                               |
|                       |                                                     |
|                       | Ensure that the ``C:\Python27\Scripts`` directory is|
|                       | defined in the ``PATH`` environment variable, and   |
|                       | use the ``easy_install`` command from the setuptools|
|                       | package:                                            |
|                       |                                                     |
|                       | .. code::                                           |
|                       |                                                     |
|                       |     C:\>easy_install pip                            |
|                       |                                                     |
|                       | Another option is to use the unofficial binary      |
|                       | installer provided by Christoph Gohlke              |
|                       | (http://www.lfd.uci.edu/~gohlke/pythonlibs/#pip).   |
|                       |                                                     |
|                       | **Ubuntu and Debian**                               |
|                       |                                                     |
|                       | .. code::                                           |
|                       |                                                     |
|                       |     # apt-get install python-dev python-pip         |
|                       |                                                     |
|                       | Note that extra dependencies may be required, per   |
|                       | operating system, depending on the package being    |
|                       | installed, such as is the case with Tempest.        |
|                       |                                                     |
|                       | **Red Hat Enterprise Linux, CentOS, or Fedora.**    |
|                       |                                                     |
|                       | A packaged version enables you to use yum to install|
|                       | the package:                                        |
|                       |                                                     |
|                       | .. code::                                           |
|                       |                                                     |
|                       |     # yum install python-devel python-pip           |
|                       |                                                     |
|                       | There are also packaged versions of the clients     |
|                       | available in `RDO <https://www.rdoproject.org/>`__  |
|                       | that enable yum to install the clients as described |
|                       | in Installing_from_packages_.                       |
|                       |                                                     |
|                       | **SUSE Linux Enterprise Linux 11**                  |
|                       |                                                     |
|                       | A packaged version available in the Open Build      |
|                       | Service (https://build.opensuse.org/package/show?   |
|                       | package=python-pip&project=Cloud:OpenStack:Master)  |
|                       | enables you to use or zypper to install the package.|
|                       | First, add the Open Build Service repository:       |
|                       |                                                     |
|                       | .. code::                                           |
|                       |                                                     |
|                       |     # zypper addrepo -f obs://Cloud:OpenStack: \    |
|                       |     Icehouse/SLE_11_SP3 Icehouse                    |
|                       |                                                     |
|                       | Then install pip and use it to manage client        |
|                       | installation:                                       |
|                       |                                                     |
|                       | .. code::                                           |
|                       |                                                     |
|                       |     # zypper install python-devel python-pip        |
|                       |                                                     |
|                       | There are also packaged versions of the clients     |
|                       | available that enable zypper to install the clients |
|                       | as described in Installing_from_packages_.          |
|                       |                                                     |
|                       | **openSUSE**                                        |
|                       |                                                     |
|                       | You can install pip and use it to manage client     |
|                       | installation:                                       |
|                       |                                                     |
|                       | .. code::                                           |
|                       |                                                     |
|                       |     # zypper install python-devel python-pip        |
|                       |                                                     |
|                       | There are also packaged versions of the clients     |
|                       | available that enable zypper to install the clients |
|                       | as described in Installing_from_packages_.          |
+-----------------------+-----------------------------------------------------+

Install the clients
~~~~~~~~~~~~~~~~~~~

When following the instructions in this section, replace PROJECT with
the lowercase name of the client to install, such as ``nova``. Repeat
for each client. The following values are valid:

-  ``ceilometer`` - Telemetry API

-  ``cinder`` - Block Storage API and extensions

-  ``glance`` - Image Service API

-  ``heat`` - Orchestration API

-  ``neutron`` - Networking API

-  ``nova`` - Compute API and extensions

-  ``sahara`` - Database Processing API

-  ``swift`` - Object Storage API

-  ``trove`` - Database service API

-  ``openstack`` - Common OpenStack client supporting multiple services

The following CLIs are deprecated in favor of ``openstack``, the
Common OpenStack client supporting multiple services:

-  ``keystone`` - Identity service API and extensions

The following example shows the command for installing the nova client
with ``pip``.

.. code::

  # pip install python-novaclient

Installing with pip
-------------------

Use pip to install the OpenStack clients on a Linux, Mac OS X, or
Microsoft Windows system. It is easy to use and ensures that you get the
latest version of the client from the `Python Package
Index <http://pypi.python.org/pypi>`__. Also, pip enables you to update
or remove a package.

Install each client separately by using the following command:

-  For Mac OS X or Linux::

     # pip install python-PROJECTclient

-  For Microsoft Windows::

     C:\>pip install python-PROJECTclient

.. _Installing_from_packages:

Installing from packages
------------------------

RDO, openSUSE and SUSE Linux Enterprise have client packages that can be
installed without ``pip``.

-  On Red Hat Enterprise Linux, CentOS, or Fedora, use ``yum`` to install
   the clients from the packaged versions available in
   `RDO <https://www.rdoproject.org/>`__::

     # yum install python-PROJECTclient

-  For openSUSE, use zypper to install the clients from the distribution
   packages Service::

     # zypper install python-PROJECT

-  For SUSE Linux Enterprise Server, use zypper to install the clients from
   the distribution packages in the Open Build Service. First, add the Open
   Build Service repository::

     # zypper addrepo -f obs://Cloud:OpenStack:Icehouse/SLE_11_SP3 Icehouse

   Then you can install the packages::

     # zypper install python-PROJECT

Upgrade or remove clients
~~~~~~~~~~~~~~~~~~~~~~~~~

To upgrade a client, add the ``--upgrade`` option to the ``pip install``
command::

  # pip install --upgrade python-PROJECTclient

To remove the a client, run the ``pip uninstall`` command::

  # pip uninstall python-PROJECTclient

What's next
~~~~~~~~~~~

Before you can run client commands, you must create and source the
:file:`PROJECT-openrc.sh` file to set environment variables. See
:doc:`../common/cli_set_environment_variables_using_openstack_rc`.
