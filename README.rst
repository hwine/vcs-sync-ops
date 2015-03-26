===============================
Build vcs-sync systems
===============================

Build docker/virtualbox/AWS image suitable for (legacy) vcs-sync.

* Free software: `Mozilla License`__

__ https://www.mozilla.org/MPL/

Installation
============


Documentation
=============

*tbd*

Development
===========

*tbd*

Requirements
------------

Using this project requires your environment to  have these
minimal dependencies:

* Setuptools_ - for building the package, wheels etc. Now-days
  Setuptools is widely available, it shouldn't pose a problem :)
* Ansible_ - for provisioning the boxes
* Vagrant_ - for managing the boxes. Also install vagrant-aws_ plugin

install::

    vagrant box add dummy https://github.com/mitchellh/vagrant-aws/raw/master/dummy.box

      
.. _Setuptools: https://pypi.python.org/pypi/setuptools
.. _Ansible: http://docs.ansible.com/
.. _Vagrant: https://www.vagrantup.com/
.. _vagrant-aws: https://github.com/mitchellh/vagrant-aws
