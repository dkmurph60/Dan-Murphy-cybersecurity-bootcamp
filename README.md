
## Automated ELK Stack Deployment

The files in this repository were used to configure the network depicted below.

https://github.com/dkmurph60/Dan-Murphy-cybersecurity-bootcamp/blob/main/Diagrams/Network%20Daiagram%20Unit%2012%20(1).png

These files have been tested and used to generate a live ELK deployment on Azure. They can be used to either recreate the entire deployment pictured above. Alternatively, select portions of the playbook file may be used to install only certain pieces of it, such as Filebeat.

  
This document contains the following details:
- Description of the Topology
- Access Policies
- ELK Configuration
  - Beats in Use
  - Machines Being Monitored
- How to Use the Ansible Build


### Description of the Topology

The main purpose of this network is to expose a load-balanced and monitored instance of DVWA, the D*mn Vulnerable Web Application.

Load balancing ensures that the application will be highly available, in addition to restricting access to the network.

Integrating an ELK server allows users to easily monitor the vulnerable VMs for changes to the file system and system metrics.
Filebeat allows monitoring of log directories and files
Metricbeat allows monitoring of metrics from the server systems and services.



The configuration details of each machine may be found below.


| Name     | Function | IP Address | Operating System |
|----------|----------|------------|------------------|
| Jump Box | Gateway  | 10.0.0.4   | Linux            |
| Web-1    |Web server| 10.0.0.7   | Linux            |
| web-2    |Web server| 10.0.0.8   | Linux            | 
| ELK      |ELK server| 10.1.0.4   | Linux            |

### Access Policies

The machines on the internal network are not exposed to the public Internet. 

Only the jump box provisioner machine can accept connections from the Internet. Access to this machine is only allowed from the following IP addresse:

Personal IP address

Machines within the network can only be accessed by the jump box.  The ELK server can be accessed from personal IP through port 5601.


A summary of the access policies in place can be found in the table below.

| Name          | Publicly Accessible | Allowed IP addresses |
|---------------|---------------------|----------------------|
|    Jump Box   |         Yes         |      Personal IP     |
| Load Balancer |         Yes         |         Open         |
|     Web-1     |          No         |       10.0.0.4       |
|     Web-2     |          No         |       10.0.0.4       |
|   Elk Server  |         Yes         |      Personal IP     |

### Elk Configuration

Ansible was used to automate configuration of the ELK machine. No configuration was performed manually, which is advantageous because it allows for quick deployment which is replicable on any number of machines. 




The playbook implements the following tasks:

 - Installs docker.io and python3-pip
 - Installs the docker module
 - Increases virtual memory
 - Downloads and intalls a docker ELK container (sebp/elk:761)



### Target Machines & Beats
This ELK server is configured to monitor the following machines:
 - Web-1 (10.0.0.7)
 - Web-2 (10.0.0.80

We have installed the following Beats on these machines:

 - Filebeat
 - Metricbeat

These Beats allow us to collect the following information from each machine:

 - Filebeat monitors log files, collects log events and forwards them for indexing.
 - Metricbeat collects metric data from the server it is installed on and forwards them.  Ths allows monitoring of sustem metrics such as CPU usage or memory, as well as data related to services running on the server.

https://github.com/dkmurph60/Dan-Murphy-cybersecurity-bootcamp/blob/main/Ansible/Install_filebeat.txt

### Using the Playbook
In order to use the playbook, you will need to have an Ansible control node already configured. Assuming you have such a control node provisioned: 

SSH into the control node and follow the steps below:

- Copy the configuration file to /etc/ansible/files/filebeat-config.yml.
- Update the hots file to include the IP address of the target machine (ELK Server).
- Run the playbook, and navigate to the ELK server public IP, http://20.94.60.25:5601/app/kibana to check that the installation worked as expected.

The command to run the playbook is ansible-playbok [playbook-name].yml
 
