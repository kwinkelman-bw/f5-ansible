# f5devcentral.f5ansible

Using this role, you will be able to use the latest version, and version specific F5 Networks
Ansible Modules.

This is a stop-gap solution until Ansible Galaxy's "Collection" feature is stable and globally
available.

## Requirements

 - python >= 2.7
 - f5-sdk

This role requires Ansible 2.7 or higher. Requirements are listed in the metadata file.

Please install f5-sdk from pip prior to running this module.

```
pip install f5-sdk --upgrade
```

## Installation

This role is released in two forms.

* daily
* bi-weekly

The form that you choose should be based on your tolerance for unstable code. F5 makes
**no** guarantees that the bi-weekly release is more stable. However, it aligns with
some individual's tolerance for product updates.
 
For instance, updating daily can be a burden to the maintainer of the playbooks and
can introduce problems at a time that is untenable for them. In this case, a bi-weekly
update is more logical.

On the other hand, some people prefer to live on the edge of technology, and for those
people, a daily build is acceptable. 

To install the bi-weekly build of the F5 Networks Ansible Role, please issue the command
on the machine you will run Ansible from.

```
ansible-galaxy install -f f5devcentral.f5ansible
```

To install the daily build of the F5 Networks Ansible Role, please issue the command
on the machine you will run Ansible from.

```
ansible-galaxy install -f f5devcentral.f5ansible,master
```

For more information please visit http://docs.ansible.com/ansible/galaxy.html

## Role Variables

Available variables are listed below, along with default values (see `defaults/main.yml`):

    f5ansible_debug: no

Enables the installation and configuration of debugging functionality. This is useful when
working with the F5 Networks Ansible developers to debug problems.

## Example Playbooks

The following example is generic, applies to any module.

```

---

- hosts: localhost
  connection: local

  roles:
    - role: f5devcentral.f5ansible

  tasks:
    - name: Some task
      bigip_<module_name>:
        provider:
          server: 1.1.1.1
          user: admin
          password: secret
      ......
```

This example shows usage of the bigip_virtual_server module included in this role.

```

---

- hosts: localhost
  connection: local

  roles:
    - role: f5devcentral.f5ansible

  tasks:
    - name: Create virtual server
      bigip_virtual_server:
        name: virt1
        destination: 2.1.3.4
        port: 9000
        description: My description
        snat: Automap
        pool: pool1
        provider:
          user: admin
          server: 1.1.1.1
          password: secret
          validate_certs: no
  register: result
```

There are many more examples located at in the ``EXAMPLES`` within each module.

## License

Apache 2.0

## Releases

This role is updated in Ansible Galaxy on a bi-weekly basis. If you want to install
an interim release of this role, use the following ``ansible-galaxy`` command

    ansible-galaxy install f5devcentral.f5ansible,master

Note the inclusion of the "comma" and "master" at the end of the command. 

## Author Information

F5 Networks
[F5 Networks](http://www.f5.com)
