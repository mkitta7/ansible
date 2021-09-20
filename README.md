## Automated ELK Stack Deployment

The files in this repository were used to configure the network depicted below.

[Diagrams/Network Diagram.pdf](https://github.com/mkitta7/ansible/blob/00e43e9fdaa794699f69a35c2a7da7545f181a41/Diagrams/Network%20Diagram.pdf) 

These files have been tested and used to generate a live ELK deployment on Azure. They can be used to either recreate the entire deployment pictured above. Alternatively, select portions of the yml file may be used to install only certain pieces of it, such as Filebeat.

  - _TODO: Enter the playbook file._

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

![TODO: Update the path with the name of your screenshot of docker ps output](Images/docker_ps_output.png)

### Target Machines & Beats
This ELK server is configured to monitor the following machines:
- _TODO: List the IP addresses of the machines you are monitoring_

We have installed the following Beats on these machines:
- _TODO: Specify which Beats you successfully installed_

These Beats allow us to collect the following information from each machine:
- _TODO: In 1-2 sentences, explain what kind of data each beat collects, and provide 1 example of what you expect to see. E.g., `Winlogbeat` collects Windows logs, which we use to track user logon events, etc._

### Using the Playbook
In order to use the playbook, you will need to have an Ansible control node already configured. Assuming you have such a control node provisioned: 

SSH into the control node and follow the steps below:
- Copy the _____ file to _____.
- Update the _____ file to include...
- Run the playbook, and navigate to ____ to check that the installation worked as expected.

_TODO: Answer the following questions to fill in the blanks:_
- _Which file is the playbook? Where do you copy it?_
- _Which file do you update to make Ansible run the playbook on a specific machine? How do I specify which machine to install the ELK server on versus which to install Filebeat on?_
- _Which URL do you navigate to in order to check that the ELK server is running?

_As a **Bonus**, provide the specific commands the user will need to run to download the playbook, update the files, etc._
