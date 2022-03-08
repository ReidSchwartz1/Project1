## Automated ELK Stack Deployment

The files in this repository were used to configure the network depicted below.

/Diagrams/CloudNetwork.png

These files have been tested and used to generate a live ELK deployment on Azure. They can be used to either recreate the entire deployment pictured above. Alternatively, select portions of the .yml file may be used to install only certain pieces of it, such as Filebeat.

  install-elk.yml filebeat-playbook.yml metricbeat-playbook.yml

This document contains the following details:
- Description of the Topology
- Access Policies
- ELK Configuration
  - Beats in Use
  - Machines Being Monitored
- How to Use the Ansible Build


### Description of the Topology

The main purpose of this network is to expose a load-balanced and monitored instance of DVWA, the Damn Vulnerable Web Application.

Load balancing ensures that the application will be highly available, in addition to restricting unauthorized access to the network.
Load balancers ensure availability, and a jump box allows connection to a network of VMs over a single IP.

Integrating an ELK server allows users to easily monitor the vulnerable VMs for changes to the _____ and system _____.
Filebeat is used to monitor changes and collect log data, such as a changed file. Metricbeat is used to collect metrics and statistics, such as server uptime and last patch.


The configuration details of each machine may be found below.

| Name               | Function    | IP             | OS           |
|--------------------|-------------|----------------|--------------|
| JumpBoxProvisioner | Gateway     | 20.121.39.229  | Linux/Ubuntu |
| Web-1              | DVWA Server | 10.0.0.7       | Linux/Ubuntu |
| Web-2              | DVWA Server | 10.0.0.8       | Linux/Ubuntu |
| Web-3              | DVWA Server | 10.0.0.9       | Linux/Ubuntu |
| ELKVM              | ELK Server  | 20.119.191.111 | Linux/Ubuntu |

### Access Policies

The machines on the internal network are not exposed to the public Internet. 

Only the JumpBoxProvisioner machine can accept connections from the Internet. Access to this machine is only allowed from the following IP addresses:
76.251.XX.XXX

Machines within the network can only be accessed by the JumpBoxProvisioner.
A personal machine was setup to access the ELK server at 76.251.XX.XXX:5601

A summary of the access policies in place can be found in the table below.

| Name               | Publicly Accessible | Allowed IP    |
|--------------------|---------------------|---------------|
| JumpBoxProvisioner | YES                 | 76.251.XX.XXX |
| Web-1              | NO                  | 10.0.0.4      |
| Web-2              | NO                  | 10.0.0.4      |
| Web-3              | NO                  | 10.0.0.4      |
| ELKVM              | YES                 | 76.251.XX.XXX |

### Elk Configuration

Ansible was used to automate configuration of the ELK machine. No configuration was performed manually, which is advantageous because Ansible allows simple execution of a playbook to set up a VM with specific parameters for specific purposes.

The playbook implements the following tasks:
- Installs the Docker container service
- Installs the ELK stack 
- Configures the machine to the network, and starts the services

The following screenshot displays the result of running `docker ps` after successfully configuring the ELK instance.

/Diagrams/docker-ps.png

### Target Machines & Beats
This ELK server is configured to monitor the following machines:
10.0.0.7 10.0.0.8 10.0.0.9

We have installed the following Beats on these machines:
Filebeat and Metricbeat

These Beats allow us to collect the following information from each machine:
Filebeat is used to monitor changes and collect log data, such as a changed file. Metricbeat is used to collect metrics and statistics, such as server uptime and last patch.

### Using the Playbook
In order to use the playbook, you will need to have an Ansible control node already configured. Assuming you have such a control node provisioned: 

SSH into the control node and follow the steps below:
- Copy the install-elk.yml file to /etc/ansible
- Update the hosts file to include the VM IP's 
- Run the playbook, and navigate to http://20.119.191.111:5601/app/kibana to check that the installation worked as expected.


