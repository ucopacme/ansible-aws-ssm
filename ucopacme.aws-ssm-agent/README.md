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

Run the role in a playbook:

```
ansible-playbook -i your-inventory -u your-user --key-file your-key-file  -e "ActivationCode=$ActivationCode" -e "ActivationId=$ActivationId" aws-ssm.yaml
```

with playbook aws-ssm.yaml:

```
# This playbook installs and configures aws ssm
- name: "Install AWS ssm agent"
  become: true
  gather_facts: true
  hosts: all
  roles:
    - role: ucopacme.aws-ssm-agent
```

License
-------

BSD

Author Information
------------------

Eric Odell
