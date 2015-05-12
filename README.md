Prometheus
=========

[![Build Status](https://travis-ci.org/gotansible/prometheus.svg?branch=master)](https://travis-ci.org/gotansible/prometheus)
[![Ansible Galaxy](http://img.shields.io/badge/galaxy-prometheus-blue.svg?style=flat)](https://galaxy.ansible.com/list#/roles/3752)

Installs and configures a Prometheus monitoring server. [Prometheus.io](http://prometheus.io/)

Requirements
------------

Systems: 

* Debian (Ubuntu) 
* RedHat (CentOS) 


Role Variables
--------------

See the Prometheus Docs
http://prometheus.io/docs/operating/configuration/
https://github.com/prometheus/prometheus/blob/master/config/config.proto

Dependencies
------------

* gotansible.runit

Example Playbook
----------------

Including an example of how to use your role (for instance, with variables passed in as parameters) is always nice for users too:

    - hosts: servers
      roles:
         - role: gotansible.prometheus
	       prometheus_global_labels:
             key: value
           prometheus_rule_files:
             - monitor.rules
           prometheus_sd_jobs:
             - job:
               name: 'api-server'
               scrape_interval: '5s'
               scrape_timeout: '10s'
               sd_name: 'dns.resovl.name.prod'
               sd_refresh_interval: '30s'
               metrics_path: '/metrics'
           prometheus_target_jobs:
             - job:
               name: api-server
               scrape_interval: 5s
               scrape_timeout: 10s
               target_group:
               - target: http://10.0.2.7:9090/metrics
               - target: http://10.0.2.8:9090/metrics
               labels:
                 role: web
                 cluster: west


License
-------

MIT

Author Information
------------------

Created by Franklin Wise in Santa Monica, CA.
