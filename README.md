AWS ec2 provision
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
| aws_route53_command | yes| | | A list of VPC subnets to use when creating ELB. Zones should be empty if using this. |
| aws_route53_zone| no| internet-facing | internet-facing, internal|The scheme to use when creating the ELB. For a private VPC-visible ELB use 'internal'. |
| aws_route53_record| | | |A list of security groups to apply to the elb |
| aws_route53_ttl| | | | List of ports/protocols for this ELB to listen on (see [vars](defaults/main.yml)| 
| aws_route53_type| no | / | |The destination for the HTTP or HTTPS request. | 
| aws_route53_value|yes | | | The amount of time to wait when receiving a response from the health check, in seconds.| 
| aws_route53_overwrite | no| http| | The protocol to use to connect with the instance.|
| aws_route53_weight | no| http| | The port to use to connect with the instance, as a protocol:port pair. If the load balancer fails to connect with the instance at the specified port within the configured response timeout period, the instance is considered unhealthy. Ping protocols: TCP, HTTP, HTTPS, and SSL.|


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