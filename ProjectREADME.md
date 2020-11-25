## Automated ELK Stack Deployment

The files in this repository were used to configure the network depicted below.

![SSDiagram.png](Diagrams/SSDiagram.png)

These files have been tested and used to generate a live ELK deployment on Azure. They can be used to either recreate the entire deployment pictured above. Alternatively, select portions of the playbook file may be used to install only certain pieces of it, such as Filebeat.

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

Load balancing ensures that the application will be highly available, in addition to restricting traffic to the network.
- What aspect of security do load balancers protect? What is the advantage of a jump box?
  
Load balancers protects applications from emerging threats and DDoS attacks. It protects the availability aspect. The advantage of a jump box is providing more security. Jump boxes are secure computers that admins connect to use as a starting point to connect to other servers.

Integrating an ELK server allows users to easily monitor the vulnerable VMs for changes to the logs and system traffic.

- What does Filebeat watch for? 

Filebeat watches for log files/locations and collects log events.

- What does Metricbeat record? 

Metricbeat collects metrics and statistics and ships them to the outputs that you want them to go.

The configuration details of each machine may be found below.
_Note: Use the [Markdown Table Generator](http://www.tablesgenerator.com/markdown_tables) to add/remove values from the table_.

| Name     | Function        | IP Address | Operating System |
|----------|-----------------|------------|------------------|
| Jump Box | Gateway         | 10.1.0.10  | Linux            |
| Web-1    | UbuntuServer    | 10.1.0.8   | Linux            |
| Web-2    | UbuntuServer    | 10.1.0.9   | Linux            |
| ELKVM    | UbuntuServer    | 10.3.0.4   | Linux            |

### Access Policies

The machines on the internal network are not exposed to the public Internet. 

Only the Jump Box machine can accept connections from the Internet. Access to this machine is only allowed from the following IP addresses:
- 96.245.194.1XX

Machines within the network can only be accessed by SSH.
- Which machine did you allow to access your ELK VM? What was its IP address?
The Jump Box is allowed to access my ELK VM via Ansible. The IP address is 10.1.0.10.

A summary of the access policies in place can be found in the table below.

| Name     | Publicly Accessible | Allowed IP Addresses |
|----------|---------------------|----------------------|
| Jump Box | Yes                 | 96.245.194.1XX       |
| Web-1    | No                  | 10.1.0.10            |
| Web-2    | No                  | 10.1.0.10            |
| ELKVM    | No                  | 10.1.0.10            |

### Elk Configuration

Ansible was used to automate configuration of the ELK machine. No configuration was performed manually, which is advantageous because...
- What is the main advantage of automating configuration with Ansible?
   You can put commands from multiple servers into a single playbook. 

The playbook implements the following tasks:
- In 3-5 bullets, explain the steps of the ELK installation play. E.g., install Docker; download image; etc._
- Install docker.io
- Install python3-pip
- Install docker module
- Increase virtual memory
- Using more memory
- Download and install docker elk container

The following screenshot displays the result of running `docker ps` after successfully configuring the ELK instance.

![dockerPS](Screenshots/dockerPS.png)

### Target Machines & Beats
This ELK server is configured to monitor the following machines:

Web-1 10.1.0.8
Web-2 10.1.0.9

We have installed the following Beats on these machines:
- Metricbeat and Filebeat.

These Beats allow us to collect the following information from each machine:
- Filebeat collects all of the changes made on a machine. Metricbeat collects metrics and statistics.

### Using the Playbook
In order to use the playbook, you will need to have an Ansible control node already configured. Assuming you have such a control node provisioned: 

SSH into the control node and follow the steps below:
- Copy the _____ file to _____.
- Update the config file to include the ip address
- Run the playbook, and navigate to Kibana to check that the installation worked as expected.

_TODO: Answer the following questions to fill in the blanks:_
- _Which file is the playbook? Where do you copy it?
- _Which file do you update to make Ansible run the playbook on a specific machine? How do I specify which machine to install the ELK server on versus which to install Filebeat on? 
Edit the /etc/ansible/hosts file to the webservers/elk server ip address
- _Which URL do you navigate to in order to check that the ELK server is running? 
http://40.124.3.143:5601/app/kibana#/home

_As a **Bonus**, provide the specific commands the user will need to run to download the playbook, update the files, etc._