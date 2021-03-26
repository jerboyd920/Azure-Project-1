## Automated ELK Stack Deployment

The files in this repository were used to configure the network depicted below.

<figure><img src="/Diagrams/Azure%20Network%20Diagram.png"><figcaption></figcaption></figure>
  
These files have been tested and used to generate a live ELK deployment on Azure. They can be used to either recreate the entire deployment pictured above. Alternatively, select portions of the install-elk.yml file may be used to install only certain pieces of it, such as Filebeat.

  - [pentest.yml](https://github.com/jerboyd920/Azure-Project-1/blob/main/Ansible/pentest.yml)
  - [install-elk.yml](https://github.com/jerboyd920/Azure-Project-1/blob/main/Ansible/install-elk.yml)
  - [filebeat-config.yml](https://github.com/jerboyd920/Azure-Project-1/blob/main/Ansible/filebeat-playbook.yml)
  - [filebeat](https://github.com/jerboyd920/Azure-Project-1/blob/main/Ansible/filebeat-playbook.yml)
  - [metricbeat-config](https://github.com/jerboyd920/Azure-Project-1/blob/main/Ansible/metricbeat-config.yml)
  - [metricbeat](https://github.com/jerboyd920/Azure-Project-1/blob/main/Ansible/metricbeat-playbook.yml)
  
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


Integrating an ELK server allows users to easily monitor the vulnerable VMs for changes to the logs and system traffic.
Filebeat watches for changes to the system logs and Metricbeat monitors system traffic.


The configuration details of each machine may be found below.
_Note: Use the [Markdown Table Generator](http://www.tablesgenerator.com/markdown_tables) to add/remove values from the table_.

| Name      | Function     | IP Address | Operating System |
|-----------|--------------|------------|------------------|
| Jump Box  | Gateway      | 10.0.0.4   | Linux - Ubuntu   |
| Elk Server| Cloud Monitor| 10.1.0.5   | Linux - Ubuntu   |
| Web-1     | Web Server   | 10.0.0.5   | Linux - Ubuntu   |
| Web-2     | Web Server   | 10.0.0.7   | Linux - Ubuntu   |
| DVWA-VM3  | Web Server   | 10.0.0.6   | Linux - Ubuntu   |


### Access Policies

The machines on the internal network are not exposed to the public Internet. 

Only the Jump Box and Elk Server machines can accept connections from the Internet via a static IP address. 

Machines within the network can only be accessed by the docker container on the Jump Box.

A summary of the access policies in place can be found in the table below.

| Name      | Publicly Accessible | Allowed IP Addresses  |
|-----------|---------------------|-----------------------|
| Jump Box  |         No          |      76.29.7.67       |
| Elk Server|         No          | 76.29.7.67 & 10.0.0.4 |        
| Web-1     |         No          |      10.0.0.4         |
| Web-1     |         No          |      10.0.0.4         |
| DVWA-VM3  |         No          |      10.0.0.4         |


### Elk Configuration

Ansible was used to automate configuration of the ELK machine. No configuration was performed manually, which is advantageous because the machine can be quickly configured and redeployed without being offline for any extended period of time.


The playbook implements the following tasks:

- Install docker.io
- Install python3-pip
- Install docker package
- Increase virtual memory
- publish ports 5601, 9200, 5044
- enable docker on boot

The following screenshot displays the result of running `docker ps` after successfully configuring the ELK instance.

<figure><img src="/Images/Docker%20ps.png"><fig caption></fig caption></figure>

### Target Machines & Beats
This ELK server is configured to monitor the following machines:

|  Name    |  IP Adress |
|----------|------------|
| Web-1    | 10.0.0.5   |
| Web-2    | 10.0.0.7   |
| DVWA-VM3 | 10.0.0.6   |

We have installed the following Beats on these machines:

-FileBeats
-MetricBeats

These Beats allow us to collect the following information from each machine:

- FileBeats collects systems logs of changes to the systems on which it's installed. An example would be if there was a failed login attempt to a machine which would be documented in the auth.log.
- MetricBeats monitors and reports system metrics. It analyzes CPU, memory and traffic usage. 
### Using the Playbook
In order to use the playbook, you will need to have an Ansible control node already configured. Assuming you have such a control node provisioned: 

SSH into the control node and follow the steps below:
- Copy the filebeat- file to _____.
- Update the _____ file to include...
- Run the playbook, and navigate to ____ to check that the installation worked as expected.

_TODO: Answer the following questions to fill in the blanks:_
- _Which file is the playbook? Where do you copy it?_
- _Which file do you update to make Ansible run the playbook on a specific machine? How do I specify which machine to install the ELK server on versus which to install Filebeat on?_
- _Which URL do you navigate to in order to check that the ELK server is running?

_As a **Bonus**, provide the specific commands the user will need to run to download the playbook, update the files, etc._
