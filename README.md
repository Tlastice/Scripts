## Automated ELK Stack Deployment

The files in this repository were used to configure the network depicted below.

![(Scripts/Images/networkdiagram.png)]

These files have been tested and used to generate a live ELK deployment on Azure. They can be used to either recreate the entire deployment pictured above. Alternatively, select portions of the _____ file may be used to install only certain pieces of it, such as Filebeat.

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

Load balancing ensures that the application will be highly available, in addition to restricting inbound traffic to the network.
What aspect of security do load balancers protect? Load balancers protect against DDoS attacks by redirecting bad traffic
What is the advantage of a jump box? it allows accessing multiple computers from a secure, non-physical point in the network

Integrating an ELK server allows users to easily monitor the vulnerable VMs for changes to the file system's traffic and system metrics.
What does Filebeat watch for? Log files and locations, and collects log events
What does Metricbeat record? Records metrics and statistics

The configuration details of each machine may be found below.
_Note: Use the [Markdown Table Generator](http://www.tablesgenerator.com/markdown_tables) to add/remove values from the table_.

| Name     | Function | IP Address | Operating System |
|----------|----------|------------|------------------|
| Jump Box | Gateway | 10.0.0.1 | Linux |
| WEB 1       |  DVWA 1 |  10.0.0.5 | Linux |
| WEB 2      |  DVWA 2 |  10.0.0.6 | Linux |
| Elk VM     |  Monitor |  10.1.0.4  | Linux |

### Access Policies

The machines on the internal network are not exposed to the public Internet. 

Only the Jumpbox machine can accept connections from the Internet. Access to this machine is only allowed from the following IP addresses:
- _TODO: Add whitelisted IP addresses_ [Redacted: My IP]

Machines within the network can only be accessed by one another.
- _TODO: Which machine did you allow to access your ELK VM? What was its IP address? Jumpbox : 20.22.201.103

A summary of the access policies in place can be found in the table below.

| Name     | Publicly Accessible | Allowed IP Addresses |
|----------|---------------------|----------------------|
| Jump Box | Yes  |  20.222.201.103  |
|  Web 1  |   No   |  10.0.0.5  |
|  Web 2 |    No   | 10.0.0.6  |
| Elk VM  |   No   | 10.1.0.4   |

### Elk Configuration

Ansible was used to automate configuration of the ELK machine. No configuration was performed manually, which is advantageous because...
- _TODO: What is the main advantage of automating configuration with Ansible?
	Ansible allows administrators to automate daily tasks so that they can also focus on other tasks.

The playbook implements the following tasks:
- _TODO: In 3-5 bullets, explain the steps of the ELK installation play. E.g., install Docker; download image; etc._
- install docker
- install pyhton-pip
- install docker

The following screenshot displays the result of running `docker ps` after successfully configuring the ELK instance.


![TODO: Update the path with the name of your screenshot of docker ps output](Scripts/Images/docker-ps.png)

### Target Machines & Beats
This ELK server is configured to monitor the following machines:
- _TODO: List the IP addresses of the machines you are monitoring 10.0.0.5 & 10.0.0.6

We have installed the following Beats on these machines:
- _TODO: Specify which Beats you successfully installed: Filebeat & Metricbeat
	

These Beats allow us to collect the following information from each machine:
- _TODO: In 1-2 sentences, explain what kind of data each beat collects, and provide 1 example of what you expect to see. E.g., `Winlogbeat` collects Windows logs, which we use to track user logon events, etc._
	Filebeat collects changes. Metricbeat collects metrics/statistics

### Using the Playbook
In order to use the playbook, you will need to have an Ansible control node already configured. Assuming you have such a control node provisioned: 

SSH into the control node and follow the steps below:
- Copy the playbook.yml file to /etc/ansible/roles/.
- Update the hosts file to include Elk VM 10.1.0.4
- Run the playbook, and navigate to http://20.248.186.217:5601/app/kibana to check that the installation worked as expected.

_TODO: Answer the following questions to fill in the blanks:_
- _Which file is the playbook? Where do you copy it?_ /etc/ansible/filebeat-configuration.yml
- _Which file do you update to make Ansible run the playbook on a specific machine? How do I specify which machine to install the ELK server on versus which to install Filebeat on?_ modify the /etc/ansible/hosts file to include web vms and the elk server in separate categories: [webservers] & [elk]
- _Which URL do you navigate to in order to check that the ELK server is running?   http://20.248.186.217:5601/app/kibana

_As a **Bonus**, provide the specific commands the user will need to run to download the playbook, update the files, etc._ ansible-playbook.yml filebeat-playbook.yml
