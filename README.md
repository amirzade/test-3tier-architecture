# test-repository
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

Each tier componenet was provisioed in its own subnet with a configured Network Security Group (NSG) to manage incoming and oitgoing traffic.

The Jump Box has is accessible from the internet via a Public IP address to allow management and configuration of all VMs, this VM is intended to be used only during build and mainteance hours and this will remain shutdown.

The Web Server (IIS) was configured with an Application Gateway with public IP 20.43.99.39 to allow the security management of web traffic. For demonstration purposes only HTTP on port 80 was opened.

The Active Directory server was built but NOY configured with an internal domain yet, the purpose of this is to centrally manage authentication, group policy and security updates via WSUS.

SQL Server was built and configured with local admin user.

Blob Storage has been created to store SQL database backups.

