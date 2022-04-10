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


How to Use the Ansible Build


#### Description of the Topology
The main purpose of this network is to expose a load-balanced and monitored instance of DVWA, the D*mn Vulnerable Web Application.
Load balancing ensures that the application will be highly available and responsive, in addition to restricting access to the network.

##### What aspect of security do load balancers protect? 
Load balancers play a significant role in Security as they help to defend against denial-of-service (Ddos) attacks.

##### What is the advantage of a jump box?
The advantage of a jump box is their flexibily to manage multiple devices in a different zone in Security. Jump boxes also have extensive software libraries, automated backups as well as customizations. 

Integrating an ELK server allows users to easily monitor the vulnerable VMs for changes to the logs and system traffic.

##### What does Filebeat watch for?

##### What does Metricbeat record?


