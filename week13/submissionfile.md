## Automated ELK Stack Deployment

The files in this repository were used to configure the network depicted below.

![picture](images/diagram.PNG)

These files have been tested and used to generate a live ELK deployment on Azure. They can be used to either recreate the entire deployment pictured above. Alternatively, select portions of the **.yml** file may be used to install only certain pieces of it, such as Filebeat.

   [Install Elk-playbook](./images/install-elk.yml)
  

This document contains the following details:
- Description of the Topology
- Access Policies
- ELK Configuration
  - Beats in Use
  - Machines Being Monitored
- How to Use the Ansible Build


### Description of the Topology

The main purpose of this network is to expose a load-balanced and monitored instance of DVWA, the D*mn Vulnerable Web Application.

Load balancing ensures that the application will be highly **available**, in addition to restricting **access** to the network.

 
 
     Load balancers receives traffic (external Ip address) and distributes it to server.

      A jump box is a gateway, which is a firewall and router combined. The jump box is also a provisioner that is used to configure VM or containers

Integrating an ELK server allows users to easily monitor the vulnerable VMs for changes to the **datas** and system **logs**.

      Filebeat is installed to collect data from file system (web servers).

     
      Metricbeat collects machine metrics such as cpu and ram, etc

The configuration details of each machine may be found below.
_Note: Use the [Markdown Table Generator](http://www.tablesgenerator.com/markdown_tables) to add/remove values from the table_.

| Name     | Function | IP Address    | Operating System  |
|----------|----------|---------------|------------------ |
| Mary     |  Host    |Temp 74.56.15.2| Windows 10        |
| Jump Box | Gateway  | 10.0.0.4      | Linux Ubuntu 18.4 |
| Web-1    |  DVWA    | 10.0.0.2      | Linux Ubuntu 18.4 |
| Web-2    |  DVWA    | 10.0.0.3      | Linux Ubuntu 18.4 |
|Elk-Server|Monitoring| 10.1.0.6      | Linux Ubuntu 18.4 |
### Access Policies
The machines on the internal network are not exposed to the public Internet. 

Only the **Jumpbox provisioner** machine can accept connections from the Internet. Access to this machine is only allowed from the following IP addresses:
- _TODO: Add whitelisted IP addresses_  

    
      Local personal IP address: Temp 74.56.15.2


Machines within the network can only be accessed by **Jumpbox Provisioner**.
- _TODO: Which machine did you allow to access your ELK VM? What was its IP address?_


      Jumpbox private IP 10.0.0.4 via port 22 SSH
      Temp 74.56.15.2 port 5601 TCP


A summary of the access policies in place can be found in the table below.

| Name     | Publicly Accessible | Allowed IP Addresses     |
|----------|---------------------|--------------------------|
| Mary     | Yes                 |10.0.0.0/16 - 10.1.0.0/16 | 
| Jump Box | Yes                 |10.0.0.0/16 - 10.1.0.0/16 |
| Web-1    | No                  |10.0.0.0/16 - 10.1.0.0/16 |
| Web-2    | No                  |10.0.0.0/16 - 10.1.0.0/16 |
|Elk-Server| No                  |10.1.0.6                  |               

### Elk Configuration

Ansible was used to automate configuration of the ELK machine. No configuration was performed manually, which is advantageous because...


      The main advantage of automating configurations with Ansible is to prevent human errors and help install and updated web servers.

The playbook implements the following tasks:
- _TODO: In 3-5 bullets, explain the steps of the ELK installation play. E.g., install Docker; download image; etc._
- Install Docker.io, python, Docker module.
- Configure Elk server's memory and increased it. 
- After DL docker elk container and configured it
- ![picture](images/elkinstall.PNG)

The following screenshot displays the result of running **docker ps** after successfully configuring the ELK instance.

![docker ps output](images\dockerps.PNG)

### Target Machines & Beats
This ELK server is configured to monitor the following machines:

            Web-1 10.0.0.2
            Web-2 10.0.0.3 

We have installed the following Beats on these machines:
- _TODO: Specify which Beats you successfully installed_

            Filebeat
            Metricbeat

![docker ps output](images\kibana-check-data.PNG)


![docker ps output](images\metricbeat-checkdata.PNG)


These Beats allow us to collect the following information from each machine:
- _TODO: In 1-2 sentences, explain what kind of data each beat collects, and provide 1 example of what you expect to see. E.g., `Winlogbeat` collects Windows logs, which we use to track user logon events, etc._

**Filebeat is a light-weight shipper that centralizes and forwards data logs.**
**Metricbeat is also a light-weight shipper that collects metric from your system and services. From CPU to Memory, Load to Network and Redis to NGINX and much more it is a light-weight way to send system and service statistics. Metricbeat collects data from your filebeat and sends it to your monitoring cluster.**

### Using the Playbook
In order to use the playbook, you will need to have an Ansible control node already configured. Assuming you have such a control node provisioned: 

        cd /etc/ansible/files then run theses below
        ansible-playbook install-elk.yml
        ansible-playbook filebeat-playbook.yml and ansible-playbook
        metricbeat-playbook.yml
        http://20.94.250.42:5601/app/kibana


###Configure ELK VM with Docker  

<br>
```bash
ansible-config      ansible-console     ansible-galaxy      ansible-playbook    ansible-vault
ansible-connection  ansible-doc         ansible-inventory   ansible-pull
root@171c1213c55f:/etc/ansible# ansible-playbook install-elk.yml
[WARNING]: ansible.utils.display.initialize_locale has not been called, this may result in incorrectly calculated text widths that can cause
Display to print incorrect line lengths

PLAY [Configure Elk VM with Docker] *************************************************************************************************************

TASK [Gathering Facts] **************************************************************************************************************************
ok: [10.1.0.6]

TASK [Install docker.io] ************************************************************************************************************************
ok: [10.1.0.6]

TASK [Install pip3] *****************************************************************************************************************************
ok: [10.1.0.6]

TASK [Install Docker python module] *************************************************************************************************************
ok: [10.1.0.6]

TASK [Use more memory] **************************************************************************************************************************
ok: [10.1.0.6]

TASK [download and launch a docker elk container] ***********************************************************************************************
[DEPRECATION WARNING]: The container_default_behavior option will change its default value from "compatibility" to "no_defaults" in
community.docker 2.0.0. To remove this warning, please specify an explicit value for it now. This feature will be removed from community.docker
in version 2.0.0. Deprecation warnings can be disabled by setting deprecation_warnings=False in ansible.cfg.
ok: [10.1.0.6]

TASK [Enable service docker on boot] ************************************************************************************************************
ok: [10.1.0.6]

PLAY RECAP **************************************************************************************************************************************
10.1.0.6                   : ok=7    changed=0    unreachable=0    failed=0    skipped=0    rescued=0    ignored=0
```








SSH into the control node and follow the steps below:
- Copy the _____ file to _____.
- Update the _____ file to include...
- Run the playbook, and navigate to ____ to check that the installation worked as expected.

_TODO: Answer the following questions to fill in the blanks:_
- _Which file is the playbook? Where do you copy it?_
- _Which file do you update to make Ansible run the playbook on a specific machine? How do I specify which machine to install the ELK server on versus which to install Filebeat on?_
- _Which URL do you navigate to in order to check that the ELK server is running?

_As a **Bonus**, provide the specific commands the user will need to run to download the playbook, update the files, etc._