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
| Jumpbox       | No                   | 10.0.0.4          |
| Web-1         | Yes/No               | 10.0.0.9          |
| Web-2         | Yes/No               | 10.0.0.8          |
| Elk Server    | Yes/No               | 10.1.0.4          |

# Elk Configuration
Ansible was used to automate configuration of the ELK machine. No configuration was performed manually, which is advantageous because automation of the configuration process provided simple, reliable, and consistent configuration management and allowed for quick application deployment.

#### The playbook implements the following tasks:

* Installs docker.io
* Intalls pip3
* Installs docker Python module 
Use apt module:
    - name: Install docker.io
      apt:
        update_cache: yes
        name: docker.io
        state: present
Use apt module:
    - name: Install pip3
      apt:
        force_apt_get: yes
        name: python3-pip
        state: present
Use pip module:
    - name: Install Docker python module
      pip:
        name: docker
        state: present


The following screenshot displays the result of running docker ps after successfully configuring the ELK instance.
Note: The following image link needs to be updated. Replace docker_ps_output.png with the name of your screenshot image file.


Target Machines & Beats
This ELK server is configured to monitor the following machines:

TODO: List the IP addresses of the machines you are monitoring

We have installed the following Beats on these machines:

TODO: Specify which Beats you successfully installed

These Beats allow us to collect the following information from each machine:

TODO: In 1-2 sentences, explain what kind of data each beat collects, and provide 1 example of what you expect to see. E.g., Winlogbeat collects Windows logs, which we use to track user logon events, etc.


Using the Playbook
In order to use the playbook, you will need to have an Ansible control node already configured. Assuming you have such a control node provisioned:
SSH into the control node and follow the steps below:

Copy the _____ file to _____.
Update the _____ file to include...
Run the playbook, and navigate to ____ to check that the installation worked as expected.

TODO: Answer the following questions to fill in the blanks:

Which file is the playbook? Where do you copy it?
Which file do you update to make Ansible run the playbook on a specific machine? How do I specify which machine to install the ELK server on versus which to install Filebeat on?
_Which URL do you navigate to in order to check that the ELK server is running?

