Role Name
=========

install amazon ssm agent on Linux systesm

Requirements
------------

Works on Rhel6/7, CentOS6/7, SLES 11

Role Variables
--------------

You will need to create activation 

```
aws ssm create-activation --default-instance-name "linux vms with ansible"
--iam-role "TheSSM/ServiceRole" --registration-limit 200 > /tmp/aa
```
You can then create variables:

```
ActivationCode=$(cat /tmp/aa |jq -r .ActivationCode)
ActivationId=$(cat /tmp/aa |jq -r .ActivationId)
 ```

Dependencies
------------

A list of other roles hosted on Galaxy should go here, plus any details in
regards to parameters that may need to be set for other roles, or variables that
are used from other roles.

Example Playbook
----------------

Including an example of how to use your role (for instance, with variables
passed in as parameters) is always nice for users too:

    - hosts: servers
      roles:
         - { role: ucopacme.aws-ssm-agent, x: 42 }

License
-------

BSD

Author Information
------------------

Eric Odell
