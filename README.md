## Automated ELK Stack Deployment

The files in this repository were used to configure the network depicted below.

README\Images\Project 1 Diagram.png

These files have been tested and used to generate a live ELK deployment on Azure. They can be used to either recreate the entire deployment pictured above. Alternatively, select portions of the _Playbook____ file may be used to install only certain pieces of it, such as Filebeat.

 README\Images\myplaybook file.yml
			Filebeat.yml
			Metricbeat.yml
			install2-elk.yml

This document contains the following details:
- Description of the Topology
- Access Policies
- ELK Configuration
  - Beats in Use
  - Machines Being Monitored
- How to Use the Ansible Build


### Description of the Topology

The main purpose of this network is to expose a load-balanced and monitored instance of DVWA, the D*mn Vulnerable Web Application.

Load balancing ensures that the application will be highly __avaliable___, in addition to restricting ___access__ to the network.
- What aspect of security do load balancers protect? What is the advantage of a jump box?_ The load balancers protects the network from attackers that are trying to take it down by overloading it. It distributes the traffic. The advantage of having a jump box, is that it’s a single unit that is secured and can be monitored by admins.

Integrating an ELK server allows users to easily monitor the vulnerable VMs for changes to the __logs___ and system __traffic___.
-  What does Filebeat watch for?_ Filebeat is meant to watch system logs and send off and changes to a host for recording.
-  What does Metricbeat record? Metricbeat records metrics and stats from the webservers to helps monitor the traffic. 

The configuration details of each machine may be found below.
_Note: Use the [Markdown Table Generator](http://www.tablesgenerator.com/markdown_tables) to add/remove values from the table_.

| Name     | Function | IP Address | Operating System |
|----------|----------|------------|------------------|
| Jump Box | Gateway  | 10.0.0.4   | Linux            |
| WEB1     | Webserver | 10.0.0.5  | Linux            |
| WEB2     | Webserver | 10.0.0.6  | Linux            |
| ProjVM   | ELK Sever | 10.1.0.4   | Linux            |

### Access Policies

The machines on the internal network are not exposed to the public Internet. 

Only the __Jumpbox___ machine can accept connections from the Internet. Access to this machine is only allowed from the following IP addresses:
- 174.44.129.183

Machines within the network can only be accessed by __Jumpbox running Ansible_Container__.
- Jumpbox using ansible.
 104.211.0.244 - Public
 10.0.0.4 - Private
A summary of the access policies in place can be found in the table below.

| Name     | Publicly Accessible | Allowed IP Addresses |
|----------|---------------------|----------------------|
| Jump Box | Yes                 | 174.44.129.183       |
| Web1     | No                  | Private 10.0.0.4     |
| Web2     | No                  | Private 10.0.0.4     |                   
| ELK Sever| No/Yes-Software     | Kibana/ 10.0.0.4     |


### Elk Configuration

Ansible was used to automate configuration of the ELK machine. No configuration was performed manually, which is advantageous because...
- What is the main advantage of automating configuration with Ansible?
Automating configuration with Ansible is simple to set up. Using the provided tool, you can customize as you need. It basically automates a selected server and has little to no errors in doing so. 

The playbook implements the following tasks:
- _TODO: In 3-5 bullets, explain the steps of the ELK installation play. E.g., install Docker; download image; etc._
- Installing the Docker.io
- Installing pip3
- Installing the docker Module
- Increasing the virtual memory 
- the last set involves downloading and launching the docker. 


The following screenshot displays the result of running `docker ps` after successfully configuring the ELK instance.

README\Images\DockerPs



### Target Machines & Beats
This ELK server is configured to monitor the following machines:
- Web1-Private IP- 10.0.0.5
- Web2-Private Ip- 10.0.0.6
We have installed the following Beats on these machines:
- Metricbeat and Filebeat were installed on these machines. 

These Beats allow us to collect the following information from each machine:
- Filebeat is basically a monitoring agent that log files and forwards data to a more advanced processing software.
- MetricBeat collects metrics and stats and forwards them to be viewed. It helps monitor your systema and the running systems. 

### Using the Playbook
In order to use the playbook, you will need to have an Ansible control node already configured. Assuming you have such a control node provisioned: 

SSH into the control node and follow the steps below:
- Copy the __Filebeat config___ file to ___roles it was copied to filebeat/filebeat.__.
- Update the _Host____ file to include the private IP of your webservers and ELK server.
- Run the playbook, and navigate to _ http://23.99.214.110:5601/app/kibana___ to check that the installation worked as expected.

 Answer the following questions to fill in the blanks:_
- _Which file is the playbook? Where do you copy it?_ the ELK playbook was copied to the /etc/ansible directory
- _Which file do you update to make Ansible run the playbook on a specific machine? You update the host config file. 
-How do I specify which machine to install the ELK server on versus which to install Filebeat on?_With in the ELK yml file you specify the host you want it installed on. 
- _Which URL do you navigate to in order to check that the ELK server is running? http://23.99.214.110:5601/app/kibana

_As a **Bonus**, provide the specific commands the user will need to run to download the playbook, update the files, etc._

