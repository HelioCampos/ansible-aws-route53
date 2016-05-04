AWS route53 [![Circle CI](https://circleci.com/gh/VivaReal/ansible-aws-route53.svg?style=svg&circle-token=aa613e01df2f966c73576c70aa9b26052a641e2f)](https://circleci.com/gh/VivaReal/ansible-aws-route53)
========= 

Manage AWS route53.

Requirements
------------

- Ansible 2.0.1 or higher.
- Tested on Ubuntu 14.04 and Amazon 7

Role Variables
--------------

| parameter             | required | default | choices | comments |
| --------------------- | -------- | ------- | -------- |-------- |
| aws_route53_command | yes| | |  |
| aws_route53_zone| yes| | |  |
| aws_route53_record| yes| | |  |
| aws_route53_ttl| yes| | |  | 
| aws_route53_type| yes| | |  |
| aws_route53_value| yes| | |  |
| aws_route53_overwrite| yes| | |  |
| aws_route53_weight | yes| | |  |

Ansible modules
--------------
[route_53](http://docs.ansible.com/ansible/route53_module.html)


Output variables
--------------
  
Example Playbook
----------------
   
    ---
    - hosts: localhost
      connection: local
      roles:
        - { role: VivaReal.aws-route53,
          aws_route53_command: create,
          aws_route53_zone: vivareal.info,
          aws_route53_type: CNAME,
          aws_route53_record: ansible.vivareal.info ,
          aws_route53_value: vivareal.com.br,
          aws_route53_overwrite: True
        }
   

License
-------

BSD

Author:
------------------

Giancarlo Rubio (<gianrubio@gmail.com>)