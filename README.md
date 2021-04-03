## Automated ELK Stack Deployment

The files in this repository were used to configure the network depicted below.


These files have been tested and used to generate a live ELK deployment on Azure. They can be used to either recreate the entire deployment pictured above. Alternatively, select portions of the _yml and config__ file may be used to install only certain pieces of it, such as Filebeat.


This document contains the following details:
- Description of the Topology
- Access Policies
- ELK Configuration
  - Beats in Use
  - Machines Being Monitored
- How to Use the Ansible Build






### Description of the Topology

The main purpose of this network is to expose a load-balanced and monitored instance of DVWA, the D*mn Vulnerable Web Application.

Load balancing ensures that the application will be highly _available and efficient, in addition to restricting __traffic___ to the network.

Load balancers protect availability, web traffic, and web security. The advantage of a jump box is automation, security, network segmentation, and access control
Integrating an ELK server allows users to easily monitor the vulnerable VMs for changes to the __data and system logs___.
Filebeat detects changes to the file system.

Metricbeat records changes in system metrics. This can be used to log/detect SSH login attempts or failed sudo attempts.


The configuration details of each machine may be found below.

| Name     |  Function  |         IP Address         | Operating System |
|----------|------------|----------------------------|------------------|
| Jump Box | Gateway    | 10.0.0.4                   | Linux            |
| ELK      | Web Server | 10.1.0.4/Public IP address | Linux            |
| Web-1    | Web Server | 10.0.0.5                   | Linux            |
| Web-2    | Web Server | 10.0.0.6                   | Linux            |
| Web-3    | Web Server | 10.0.0.7                   | Linux            |



### Access Policies

The machines on the internal network are not exposed to the public Internet.
_
Only the _Elk server__ machine can accept connections from the Internet. Access to this machine is only allowed from the following IP addresses:

 Azure Public IP address with TCP 5601

Machines within the network can only be accessed by Jump-box Provisioner.
Jump-Box-Provisioner IP : 10.0.0.4 via SSH port 22
Workstation Public IP port TCP 5601


A summary of the access policies in place can be found in the table below.

| Name       | Publicly Accessible |  Allowed IP Addresses          |
|------------|---------------------|--------------------------------|
| Jump Box   | Yes                 | Workstation Public IP SSH 22   |
| Elk Server | No                  | Azure Public IP using TCP 5601 |
| Web-1      | No                  | 10.0.0.5                       |
| Web-2      | No                  | 10.0.0.6                       |
| Web-3      | No                  | 10.0.0.7                       |


### Elk Configuration

Ansible was used to automate configuration of the ELK machine. No configuration was performed manually, which is advantageous because...
Ansible allows for efficient deployment of multi-step programs

The playbook implements the following tasks:

- Step 1: Install Docker
Step 2: Add Elastic Repository. Elastic repositories enable access to all the open-source software in the ELK stack.
Step 3: Install Elasticsearch.
Step 4: Install Kibana.
Step 5: Install Logstash.
Step 6: Install Filebeat.


The following displays the result of running `docker ps` after successfully configuring the ELK instance.

- Run `sudo docker container list -a` if you need to see your container's name.

- Run `sudo docker ps` to view running containers.

- Run `docker attach container_name` to get a shell on your Ansible container.

### Target Machines & Beats
This ELK server is configured to monitor the following machines:

Web 1 10.0.0.5 and Web 2 10.0.0.6

We have installed the following Beats on these machines:

Web 1, Web 2, and Elk Server - Filebeat and Metricbeat

These Beats allow us to collect the following information from each machine:

Filebeat logs events and Metricbeat logs metrics and system statistics



### Using the Playbook
In order to use the playbook, you will need to have an Ansible control node already configured. Assuming you have such a control node provisioned:

SSH into the control node and follow the steps below:
- Copy the _'/etc/ansible/files/filebeat-config.yml'____ file to _'/etc/filebeat/filebeat-playbook.yml'____.
- Update the _curl -L -O https://artifacts.elastic.co/downloads/beats/filebeat/filebeat-7.6.1-amd64.deb____ file to include... installer
- Run the playbook, and navigate to _Kibana___ to check that the installation worked as expected.

- _Which file is the playbook? Where do you copy it?_
   For ANSIBLE : See Elk Install.yml
   For FILEBEAT: See Filebeat playbook
   For METRICBEAT: See Metricbeat-playbook.yml

- _Which file do you update to make Ansible run the playbook on a specific machine? How do I specify which machine to install the ELK server on versus which to install Filebeat on?_
- _Which URL do you navigate to in order to check that the ELK server is running?
- root@[your.root.id]:/etc/ansible# curl -L -O https://ansible.com/  > ansible.cfg
- root@[your.root.id]:/etc/ansible# nano ansible.cfg

Test Kibana on web : http://[your.ELK-VM.External.IP]:5601/app/kibana
Test Kibana on localhost: sysadmin@10.1.0.4: curl localhost:5601/app/kibana
