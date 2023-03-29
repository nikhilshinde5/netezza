# Cloud Pak for Data System


[Full documentation](https://www.ibm.com/docs/en/cloud-paks/cloudpak-data-system/2.0?topic=getting-started)



## What is Cloud Pak for Data System(CPDS)?

Cloud Pak for Data System is an all-in-one cloud-native Data and AI platform in a box, that enables you to collect, organize and analyze data with unprecedented simplicity and agility, within a preconfigured and governed environment. 


## What is the difference between Cloud Pak for Data System and Cloud Pak for Data ?

Cloud Pak for Data and Cloud Pak for Data System are two different offerings from IBM that provide data and AI capabilities.

Cloud Pak for Data is a containerized software platform that runs on Red Hat OpenShift, designed to help organizations collect, organize, analyze, and operationalize data. It provides a variety of data and AI services, such as data virtualization, data governance, data science, and machine learning.

On the other hand, Cloud Pak for Data System is an all-in-one, integrated system that combines hardware, storage, and software to provide a turnkey solution for data and AI workloads. It is preconfigured with IBM Cloud Pak for Data software, making it easier for organizations to deploy and manage the platform.

In summary, while both offerings provide data and AI capabilities, Cloud Pak for Data is a software platform that runs on OpenShift, whereas Cloud Pak for Data System is an integrated hardware and software system that provides a turnkey solution for data and AI workloads.



## System Overview

Infrastructure ----> [Intel x86-based hyper-converged infrastructure](reference.md)

### Features of CPDS 

    1. All-in-one, pre-integrated system that consists of sophisticated hardware and software ready to   go from day 1 operations, and is optimized for data and AI workloads.
    
    2. Portability and scalability with Red Hat OpenShift - you can run the workloads consistently like in a public cloud.
    
    3. You can securely store and process data locally to leverage the AI ladder with Cloud Pak for Data: collect, organize, analyze data and infuse AI
    
    4. The system infrastructure provides an active-active 25Gb HA network and is 50x faster than the public cloud. 


### Hardware

hardware components installed in your own rack
                or
go with the integrated rack solution.

expand the base system with additional enclosures, redundant management and fabric switch, or even a spine switch.
Cloud Pak for Data System chassis is based on Lenovo ThinkSystem SD530.

### System Nodes

Physical nodes are contained in enclosures. Each enclosure contains four nodes. Nodes are assigned roles. The roles are implemented by deploying one or more virtual machines on a server node.
roles :
    1. Control :
        3 servers always assigned 
        designated as control plane
        candidate for Platform Manager hub
        they host one control virtual machine
        manages cluster and CPDS deployment.
        atleast 2 should be operational

    2. Worker :
        compute nodes 
        host 1 or more CPDS worker vm.
        runs services
        Two types of worker nodes :
            1. Universal: can host any service, container or pod
            2. Labled: dedicated vm for specific service


### Software

1. Red Hat Operating System
2. platform management (sys management, monitoring, events & alerts)
3. platform support elements (HPI-host platform interface, callhome, resource managers, ApUtil-cli to monitor & support system, ApComm-platform communication, ApStore-conf & monitoring of platform storage resources)
4. RedHat OpenShift (Build,deploy and Scale)
5. Cloud Pak for Data System Edition
6. Netezza Performance Server for Cloud Pak for Data System



### Network

1. [Fabric Switch (8831-25C)](reference.md)
2. [Management Switch (8831-S52)](reference.md)

### Storage


### Security

1. Air-gapped
2. encryption
3. built-in cryptographic algorithm and encryption key
4. self-encrypting SSD
5. high security protocol - FIPS/STIG
6. vulnerability reports within one click


### Administrative Interfaces

Cloud Pak for Data web client
system command line inteface apcli




# User Interfaces

1. system web console
2. cloud pak for data web console
3. openshift web cojnsole
4. netezza web console


# Loggin In

## Using CLI

with user apadmin or user from group ibmapsysadmins group

```bash
ssh apadmin@user_defined_IP_address
```
default system administrator credentials are: apadmin:password


## Using web console

<domain> - Cloud Pak for Data System floating public hostname;
*.<domain> - wildcard DNS example;
icpd-system.<domain> - Cloud Pak for Data System console;
icpd-zen.<domain> - Cloud Pak for Data console;
<new-service>.<domain> - services (add-ons), if any are installed.

1. with administrstive priviledges
    Login at: https://icpd-system.<domain>
    Default credentials: apadmin password
2. with application user priviledges:
    Login at: https://icpd-zen.<domain>



## Collecting the Cloud Pak for Data admin user password

run the following command to retrivwe the password:

```bash
oc extract secret/admin-user-details -n zen  --keys=initial_admin_password --to=-
```

