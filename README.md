# 3-Tier Windows/SQL Architecture on Microsoft Azure  
Created 3-tier architecture on Microsoft Azure with following components:
- Jump Box
- Web Server (IIS)
- Application Gateway
- Active Directory
- SQL Server
- Blob Storage 

Windows Server 2016 Data Center edition was used for all VMs and SQL Server 2016 SP1 for the backend DB.

To access the test website please go to this URL http://20.43.99.39

The network topology was designed as follows:
![alt text](https://github.com/amirzade/test-repository/blob/master/topology.svg)

Each tier componenet was provisioed in its own subnet with a configured Network Security Group (NSG) to manage incoming and outgoing traffic.

The Jump Box is accessible from the internet via a Public IP 20.43.100.9 to allow management and configuration of all VMs, this VM is intended to be used only during build and mainteance hours and any other time will remain shutdown.

The Web Server (IIS) was configured with an Application Gateway with public IP 20.43.99.39 to allow the security management of web traffic. For demonstration purposes only HTTP on port 80 was opened.

The Active Directory server was built but NOT yet configured with an internal domain, the purpose of this is to centrally manage authentication, group policy and security updates via WSUS.

SQL Server was built and configured with local admin user. Once AD is fully provisioned it will be joined to the internal domain.

Blob Storage has been created to store SQL database backups.

# Deployment Steps
Copy the ARM template from this repository and deploy via Azure Portal.
1. Click on New and select Template Deployment
2. Select Custom Deployment
3. Click on Edit Template
4. Load ARM tempalte from the JSON file

![alt text](https://github.com/amirzade/test-repository/blob/master/deploy_template.png)
