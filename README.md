ansible deployment for openstack demo
=====================================

The purpose of this ansible deployment is to configure and set up 
a basic openstack system for demonstration purposes.

Author Information
------------------

https://github.com/openstack-ansible

Todo
----

- roles should have distinct install and configuration phases only, with 
  configuration occurring at startup in docker using a launch script, all
  long-running processes should be managed by supervisor

- all test/demo variables should be moved out of defaults/ and group_vars/ and
  and set at the top of test.yml

- every role should have a test and be set up for ci in travis...

- consistent use of admin token vs admin login user and password for keystone...
