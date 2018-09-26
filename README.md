Wildfly
=======

Ansible role to manage jBoss/Wildfly AS. All server components are running on 
localhost, and the role is meant to be exposed by some kind of HTTP proxy. For ex.
[my nginx HTTP proxy role](https://github.com/kkoralsky/ansible_nginx_http_proxy)
can be used.

Role Variables
--------------

- `wildfly_user` - user running AS, as well as one authorized to manage & configure
  the server; defaults to user that runs the playbook; if user does not exist,
  it will be created
- `wildfly_install` - whether download & install the server (defualt: yes)
- `wildfly_version` - wildfly version to download from official project website 
- `wildfly_download_url` - specify own download url of ZIP bundle (we're using official link sheme by default) 

- `wildfly_deployments` - local folder where deployments should be;
- `wildfly_configuration` - local folder where configration files are to be copied

jBoss deployments are managed through [filesystem scanner](https://docs.jboss.org/author/display/WFLY10/Application+deployment#Applicationdeployment-DeploymentScannerModes).
Both last variables, best if they're absolute paths. By default they're, accordingly
`./wildfly/deployments` and `./wildfly/configuration` relative to path from where
playbook is executed. 


Example Playbook
----------------

Including an example of how to use your role (for instance, with variables
passed in as parameters) is always nice for users too:

    - hosts: jboss
      roles:
         - role: wildfly
           wildfly_version: 14.0.1.Final 

License
-------

BSD
