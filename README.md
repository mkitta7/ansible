## Automated ELK Stack Deployment

The files in this repository were used to configure the network depicted below.

- [Diagrams/Network Diagram.pdf](https://github.com/mkitta7/ansible/blob/00e43e9fdaa794699f69a35c2a7da7545f181a41/Diagrams/Network%20Diagram.pdf) 

These files have been tested and used to generate a live ELK deployment on Azure. They can be used to either recreate the entire deployment pictured above. Alternatively, select portions of the yml file may be used to install only certain pieces of it, such as Filebeat.

  - [Linux/my-playbook.yml](https://github.com/mkitta7/ansible/blob/47712488ae4a94a41a1e3669fd06e9385cfe0efb/Linux/my-playbook.yml)

This document contains the following details:
- Description of the Topologu
- Access Policies
- ELK Configuration
  - Beats in Use
  - Machines Being Monitored
- How to Use the Ansible Build


### Description of the Topology

The main purpose of this network is to expose a load-balanced and monitored instance of DVWA, the D*mn Vulnerable Web Application.

Load balancing ensures that the application will be highly efficient, in addition to restricting high-traffic to the network.
- The load balancers provide web traffic flow management between the servers and the end points as to prevent the servers from overloading so that accessibility is maintained and is a prevention point for DDoS Attacks.  The Jump Box is a single entry point between networks which creates a more secure environment.

Integrating an ELK server allows users to easily monitor the vulnerable VMs for changes to the network and system logs.
- Filebeat monitors specified log files which then collects the log events and sends them to Elasticsearch or Logstash which indexes them.
- Metricbeat creates records for the metrics and statistics and sends them to Elasticsearch or Logstash.

The configuration details of each machine may be found below.

| Name     | Function | IP Address | Operating System |
|----------|----------|------------|------------------|
| Jump Box | Gateway  | 10.0.0.4   | Linux            |
| Web1     | Webserver| 10.0.0.5   | Linus            |
| Web2     | Webserver| 10.0.0.6   | Linux            |
| elk      | Webserver| 10.2.0.5   | Linux            |

### Access Policies

The machines on the internal network are not exposed to the public Internet. 

Only the Jump Box machine can accept connections from the Internet. Access to this machine is only allowed from the following IP addresses:
- 107.77.237.137 (Hotspot IP Address will change each time)

Machines within the network can only be accessed by the Jump Box.
- The Jump Box VM (10.0.0.4) will launch the Ansible Container which will then ssh into the Elk VM (10.2.0.5).

A summary of the access policies in place can be found in the table below.

| Name     | Publicly Accessible | Allowed IP Addresses |
|----------|---------------------|----------------------|
| Jump Box | Yes                 | 107.77.237.137       |
| Web1     | No                  | 10.0.0.4             |
| Web2     | No                  | 10.0.0.4             |
| elk      | No                  | 10.0.0.4             |

### Elk Configuration

Ansible was used to automate configuration of the ELK machine. No configuration was performed manually, which is advantageous because...
- When configuring multiple vm's this allows for a single point of update or even correction to take place and then be pushed out to all the other machines.  If machines are created at a high frequency this also allows for simple and quick configurations to take place anytime a new one is needed.  If in the event of an attack or even accidental deletion, it allows for a quick and clean restoration of the container.

The playbook implements the following tasks:
- Install Python Docker Module
- Download and launch a docker web container
- Enable docker service

The following screenshot displays the result of running `docker ps` after successfully configuring the ELK instance.

[Ansible/docker ps screenshot.png](https://github.com/mkitta7/ansible/blob/5975c48c12ac1a8647a99063540d697b49151f8f/Ansible/docker%20ps%20screenshot.png)

### Target Machines & Beats
This ELK server is configured to monitor the following machines:
- web1 (10.0.0.5)
- web2 (10.0.0.6)

We have installed the following Beats on these machines:
- Filebeat
- Metricbeat

These Beats allow us to collect the following information from each machine:
- The Filebeat Elasticsearch module can handle audit logs, deprecation logs, gc logs, server logs, and slow logs.
- Metricbeat collects metric data from your target servers, this could be operating system metrics such as CPU or memory or data related to services running on the server.
### Using the Playbook
In order to use the playbook, you will need to have an Ansible control node already configured. Assuming you have such a control node provisioned: 

SSH into the control node and follow the steps below:
- Copy the filebeat-config.yml file to /etc/ansible.
- Update the filebeat-config.yml file to include...
- Run the playbook, and navigate to URL http://VM-IP-address:5601/app/kibana to check that the installation worked as expected.

- Playbook is located in my-playbook.yml which is copied to the /etc/ansible#
- To make ansible run the playbook you will update the host file with the IP address of those virtual machines you want to be able to run it on.  Elk server should be installed on your vm that is monitoring the filebeat and will be linked to the Kibana.  Filebeat is installed on the webservers you wish to monitor and have data sent to Kibana.
- To check that the elk server is running use curl localhost/setup.php

_As a **Bonus**, provide the specific commands the user will need to run to download the playbook, update the files, etc._
### Bonus Steps
Here are the following commands to run the download, update and etc for the playbook:
- nano my-playbook.yml then copy and paste the provided yml file to your vm
- To run the playbook: ansible-playbook my-playbook.yml

