Ansible role to install and configure AWS Cloudwatch Agent on both Windows and Linux

[![Build Status](https://travis-ci.org/riponbanik/ansible-role-aws-cloudwatch-agent.svg?branch=master)](https://travis-ci.org/riponbanik/ansible-role-aws-cloudwatch-agent)

## Requirements

None.

## Role Variables

Available variables are listed below, along with default values (see `defaults/main.yml`):

Windows EventLog Monitoring
```
aws_cw_windows_events: 
	- name: 'System'
	  levels: ['ERROR', 'CRITICAL']
	  format: 'text'
	  log_group: 'Windows/System'            
	- name: 'Application'
	  levels: ['ERROR']
	  format: 'text'
	  log_group: 'Windows/Application' 
```

Log files Monitoring
```
aws_cw_logfiles
 - path: /var/log/auth.log
   timestamp_format: "%b %d %H:%M:%S"
   log_group: "auth"
```	 
   
Allows to use custom cloudwatch template e.g. the following can be put same level as the playbook
```
aws_cw_config_template_path: 'templates/CloudwatchConfig.json'

```
Enable Debug Log
```
aws_cw_log_debug: true
```

## Dependencies

None.

## Example Playbook

    - hosts: all
      roles:
        - { role: riponbanik.aws-cloudwatch-agent }

## License

MIT / BSD

## Author Information

This role was created in 2019 by [Ripon Banik ](https://www.linkedin.com/in/ripon-banik-79956b23/)
