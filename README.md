# Automated-ELK-Stack-Deployment
Automated ELK Stack Deployment with Filebeat and Metricbeat using Ansible

The files in this repository were used to configure the network depicted below.

https://github.com/mtslutz/Automated-ELK-Stack-Deployment/blob/main/images/network-diagram.png

These files have been tested and used to generate a live ELK deployment on Azure. They can be used to recreate the entire deployment pictured above. Alternatively, select portions of the install-elk.yml file may be used to install only certain pieces of it, such as Filebeat or Metricbeat.

 https://github.com/mtslutz/Automated-ELK-Stack-Deployment/blob/main/install-elk.yml

This document contains the following details:
- Description of the Topology
- Access Policies
- ELK Server Configuration
- ELK Configuration
  - Beats in Use
  - Machines Being Monitored
- How to Use the Ansible Build


### Description of the Topology

The main purpose of this network is to expose a load-balanced and monitored instance of DVWA, the D*mn Vulnerable Web Application.

Load balancing ensures that the application will be highly available, in addition to restricting unwanted inbound access to the network. The load balancer ensures incoming traffic will be shared by both vulnerable web servers. Access controls will ensure that only authorized users--namely, ourselves--will be able to connect in the first place.

Integrating an ELK server allows users to easily monitor the vulnerable VMs for changes to the file systems of the VMs on the network, as well as watch system metrics like CPU usage, attempted SSH logins, sudo escalation failutes, etc.

The configuration details of each machine may be found below.

| Name                 | Function   | IP Address | Operating System |
|----------------------|------------|------------|------------------|
| Jump-Box-Provisioner | Gateway    | 10.0.0.4   | Linux            |
| Web-1                | Web Server | 10.0.0.5   | Linux            |
| Web-2                | Web Server | 10.0.0.6   | Linux            |
| Web-3                | Web Server | 10.0.0.7   | Linux            |
| ELK-SERVER           | Monitoring | 10.1.0.4   | Linux            |

In addition to the above, I have provisioned a load balancer in Azure in front of all machines except Jump-Box-Provisioner. The load balancer is named Red-Team-LB and its targets are organized into the following availability zones:
- Availability Zone 1: Web-1 + Web-2 + Web-3
- Availability Zone 2: ELK-SERVER

### Access Policies

The machines on the internal network are not exposed to the public Internet. 

Only the Jump-Box-Provisioner machine can accept connections from the Internet. Access to this machine is only allowed from the following IP address: 70.112.146.48.

Machines within the network can only be accessed by the Jump-Box-Provisioner and each other using SSH. The Web-1, Web-2, and Web-3 virtual machines all send traffic to the ELK server.

A summary of the access policies in place can be found in the table below.

| Name                 | Publicly Accessible | Allowed IP Addresses |
|----------------------|---------------------|----------------------|
| Jump-Box-Provisioner | Yes                 | 70.112.146.48        |
| Web-1                | No                  | 10.0.0.1-254         |
| Web-2                | No                  | 10.0.0.1-254         |
| Web-3                | No                  | 10.0.0.1-254         |
| ELK-SERVER           | Yes                 | 70.112.146.48        |

### ELK Server Configuration
The ELK VM exposes an Elastic Stack instance. Docker is used to download and manage an ELK container.

Rather than configure ELK manually, I developed a reusable Ansible Playbook to accomplish the task. This playbook is duplicated below.

To use this playbook, one must log into Jump-Box-Provisioner, then use the command: ansible-playbook install_elk.yml elk. This runs the install_elk.yml playbook on the elk host.

### Elk Configuration

Ansible was used to automate configuration of the ELK machine. No configuration was performed manually, which is advantageous because...
- _TODO: What is the main advantage of automating configuration with Ansible?_

The playbook implements the following tasks:
- _TODO: In 3-5 bullets, explain the steps of the ELK installation play. E.g., install Docker; download image; etc._
- ...
- ...

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
