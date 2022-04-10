Tonda Lake
# Washington University CyberSecurity Bootcamp Project 1
## Automated Elk Stack Deployment 
The files in this respository were used to configure the network depicted below:
![Elk Stack Deployment drawio](https://user-images.githubusercontent.com/95553513/162596263-a5c5a999-70da-40e2-9904-150f642e060f.png)

These files have been tested and used to generate a live ELK deployment on Azure. They can be used to either recreate the entire deployment pictured above. Alternatively, select portions of the playbook.yml file may be used to install only certain pieces of it, such as Filebeat.

[My-Playbook.yml File](http://github.com/tslake/cyberbookcamp/raw/mainAnsible/My-Playook.txt)

This document contains the following details:

* Description of the Topology
* Access Policies
* ELK Configuration
    * Beats in Use
    * Machines Being Monitored
* How to Use the Ansible Build


#### Description of the Topology
The main purpose of this network is to expose a load-balanced and monitored instance of DVWA, the D*mn Vulnerable Web Application.
Load balancing ensures that the application will be highly available and responsive, in addition to restricting access to the network.

* Load balancers play a significant role in Security as they help to defend against distributed denial-of-service (DDos) attacks. The advantage of a jump box is their    flexibily to manage multiple devices in a different zone in Security. Jump boxes also have extensive software libraries, automated backups as well as customizations. 

Integrating an ELK server allows users to easily monitor the vulnerable VMs for changes to the logs and system traffic.

* Filebeat monitors for specified log files and locations, while also collecting log events.

* Metricbeat records metrics and statistics, and sends them to a specified output for further analysis.

The configuration details of each machine may be found below.


| Name          | Function      | IP Address  | Operating System  |
| ------------- |:-------------:| -----:      |  ---------------- |
| Jumpbox       | Gateway       | 10.0.0.4    | Linux (Ubuntu 18.04 LTS  |
| Web-1         | Web Server    | 10.0.0.9    | Linux (Ubuntu 18.04 LTS) |
| Web-2         | Web Server    | 10.0.0.8    | Linux (Ubuntu 18.04 LTS) |
| Elk Server    | Elk Stack     | 10.1.0.4    | Linux (Ubuntu 18.04 LTS) |


## Access Policies
The machines on the internal network are not exposed to the public Internet.
Only the Jumpbox Provisioner machine can accept connections from the Internet. Access to this machine is only allowed from the following IP addresses:

* Personal IP Address

Machines within the network can only be accessed by SSH.

* The machine allowed to access the ELK VM is the Jumpbox Provisioner. Its private IP address is: 10.0.0.4

A summary of the access policies in place can be found in the table below:

| Name          | Publicly Accessible  | Allowed IP Address| 
| ------------- |:-------------:       |  ---------------- |
| Jumpbox       | No                   | 20.25.125.184     |
| Web-1         | No                   | 10.0.0.9          |
| Web-2         | No                   | 10.0.0.8          |
| Elk Server    | No                   | 10.1.0.4          |

# Elk Configuration
Ansible was used to automate configuration of the ELK machine. No configuration was performed manually, which is advantageous because automation of the configuration process provided simple, reliable, and consistent configuration management and allowed for quick application deployment.

#### The playbook implements the following tasks:

* Installs docker.io
* Intalls pip3
* Installs docker Python module 
 #### Use apt module:
     - name: Install docker.io
      apt:
        update_cache: yes
        name: docker.io
        state: present
#### Use apt module:
    - name: Install pip3
      apt:
        force_apt_get: yes
        name: python3-pip
        state: present
#### Use pip module:
    - name: Install Docker python module
      pip:
        name: docker
        state: present


The following screenshot displays the result of running docker ps after successfully configuring the ELK instance:
![docker-ps](https://user-images.githubusercontent.com/95553513/162629559-0237a73c-ad91-46b1-b7a0-c8e89b19d5e4.png)

### Target Machines & Beats
This ELK server is configured to monitor the following machines:
* WEb-1 (IP Address 10.0.0.9)
* Web-2 (IP Address 10.0.08)

We have installed the following Beats on these machines:
* Filebeat
* Metricbeat
    
These Beats allow us to collect the following information from each machine:

* Filebeat monitors and collects audit logs, deprecation logs as well as server logs, in the Filebeat ElasticSearch module. From the audit logs, I would expect to see login attemps passess and failures as well as authentication successes and failures. Metricbeats collects metrics and statistics from the systems and services running on the servers. These metrics can produce statuses on the systems/services such as their uptime stats, CPU stats and connection stats. 

### Using the Playbook
In order to use the playbook, you will need to have an Ansible control node already configured. Assuming you have such a control node provisioned:

SSH into the control node and follow the steps below:

* Copy the filebeat-config.yml to /etc/ansible/files.
* Update the /etc/ansible/host file to include the Private IP of the ELK-Server to the ElasticSearch and Kibana Sections of the Configuration File
* Run the playbook, and navigate to ELK-Server-PublicIP:5601/app/kibana to check that the installation worked as expected.

* The filebeat playbook.yml is the playbook, and it was copied to /etc/ansible/files. 
* The /etc/ansible/host.config file is updated to make Ansible run the playbook on a specific machine.
* In the etc/ansible/hosts file, updates must be made to specify which machine to install Elk server on versus which to install Filebeat on. The webservers group  contains the IP addressess of the VMs that filebeat will be installed on and the elkservers group contains the IP address of the machine the Elk server will be installed on. 
* In a new web browser, navigating to (http://[your.ELK-VM.External.IP]:5601/app/kibana) will launch the Kibana Web Portal to verify the ELK server is running.

