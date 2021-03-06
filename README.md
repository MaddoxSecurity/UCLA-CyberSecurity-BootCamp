# Cloud Network
## Automated ELK Stack Deployment

The files in this repository were used to configure the network depicted below.

![](Diagrams/cloud-network.png)

These files have been tested and used to generate a live ELK deployment on Azure. They can be used to either recreate the entire deployment pictured above. Alternatively, select portions of the ansible playbook file may be used to install only certain pieces of it, such as Filebeat.

  - [FileBeat Playbook](https://github.com/MaddoxSecurity/UCLA-CyberSecurity-BootCamp/blob/main/Ansible/File%20Beat%20Ansible%20playbook.txt)
  - [Metric Playbook](https://github.com/MaddoxSecurity/UCLA-CyberSecurity-BootCamp/blob/main/Ansible/Metricbeat-playbook.yml.txt)

This document contains the following details:
- Description of the Topology
- Access Policies
- ELK Configuration
  - Beats in Use
  - Machines Being Monitored
- How to Use the Ansible Build


### Description of the Topology

The main purpose of this network is to expose a load-balanced and monitored instance of DVWA.

Load balancing ensures that the application will have redundancy, in addition to restricting access to the network.
- Load balancing protects servers from denial-of-service attacks, in addition to providing scalability and efficiency. One benefit of using a jump box is it protects the VMs from public exposure.

Integrating an ELK server allows users to easily monitor the vulnerable VMs for changes to the files and system performance.
- Filebeat monitors log files and visualizes them in Kibana.
- Metricbeat collects metrics from the OS and from services running on the server. The results can be visualized in Kibana.

The configuration details of each machine may be found below.

| Name     | Function | IP Address | Operating System |
|----------|----------|------------|------------------|
| Jump Box | Gateway  | 10.0.0.4   |Linux Ubuntu 18.04|
| Web-1    | VM       | 10.0.0.5   |Linux Ubuntu 18.04|
| Web-2    | VM       | 10.0.0.6   |Linux Ubuntu 18.04|
|Elk-Server|ELk-Stack | 10.1.0.4   |Linux Ubuntu 18.04|

### Access Policies

The machines on the internal network are not exposed to the public Internet. 

Only the Jump machine can accept connections from the Internet. Access to this machine is only allowed from the following IP addresses:
- 136.26.118.87

Machines within the network can only be accessed by 10.0.0.4

A summary of the access policies in place can be found in the table below.

| Name     | Publicly Accessible | Allowed IP Addresses |
|----------|---------------------|----------------------|
| Jump Box | Yes                 | 136.26.118.87        |
|  Web-1   | No                  | 10.0.0.4             |
|  Web-2   | No                  | 10.0.0.4             |
|ELK Server| No                  | 10.0.0.4             |

### Elk Configuration

Ansible was used to automate configuration of the ELK machine. No configuration was performed manually, which is advantageous because ansible ensures all the machines were configured the same way and reduces the opportunity for human error, while saving time.

The playbook implements the following tasks:
- Change the memory on the ELK VM
-Install docker.io
-Install python3-pip
-Install docker python module
-Download and launch a docker ELK stack The following screenshot displays the result of running docker ps after successfully configuring the ELK instance.


![](Diagrams/sudo_docker_ps.png)

### Target Machines & Beats
This ELK server is configured to monitor the following machines:
- Web-1 10.0.0.5
- Web-2 10.0.0.6

We have installed the following Beats on these machines:
- Filebeat 7.4.0 amd64.deb
- Metricbeat 7.4.0 amd64.deb

These Beats allow us to collect the following information from each machine:
- Filebeat is used to monitor our log files and sends them to Kibana where they can be visualized.
- Metricbeat monitors our system services and metrics and sends them to Kibana where they can be visualized.

### Using the Playbook
In order to use the playbook, you will need to have an Ansible control node already configured. Assuming you have such a control node provisioned: 

SSH into the control node and follow the steps below:
-Copy the filebeat-config.yml and metricbeat-config.yml files to the ELK VM.
-Update the hosts file to include your webservers IP addresses.
-Run the playbook using ansible-playbook, and navigate to Kibana to check that the installation worked as expected.

