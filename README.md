OVERVIEW
========
	This ansible playbook configure High availbility tomcat servers using HAproxy server and deploys webbapp 
	on configured tomcat server. It also configures POSTGRESQL DB server. Roles are defined for each task i.e.
	1=> haproxy
	2=> tomcat
	3=>postgre

	all above mentioned roles are called in playbook "main.yml" 
ROLES
=====
  haproxy:
  =======
	this role install haproxy server in hostgroup "frontends" and push custom configurations written in jinja2 
	template. variables mentioned in configuration template are defined under "vars" dir of role.
  tomcat:
  ======
	this role installs some basic packages for tomcat, download and extract tomcat. it creates service file in systemd
	to manage tomcat as a service and then start and enable service.
  postgre:
  =======
	This role download postgresql-server, initialize it then start and enable the service.


Main.yml:
========
	This is main playbook that calls all above mentioned roles in sequence and after that it deploys webapp on 
	tomcat servers.

ansible.cfg:
===========
	This file contain configurations for ansible which can be customized as per user requirement.

hosts:
===== 
	this is the hists inventory file.

index.html:
==========
	this is the webapp playbook deployes on tomcat server.  

cleanup.yml:
===========
	this cleans up all configurations made by main.yml 	   	
