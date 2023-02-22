## Jenkins-Ansible-Apache Tomcat
## Image
![project-1](https://user-images.githubusercontent.com/111736742/220655568-ffe52c02-8dd5-4ac5-8af1-b7cf66661e73.jpg)
## Ansible-Installation
```bash
wget https://dl.fedoraproject.org/pub/epel/epel-release-latest-7.noarch.rpm
yum install epel-release-latest-7.noarch.rpm
yum update -y
yum install git python python-devel python-pip openssl ansible -y
ansible --version
```
![ansible-1server](https://user-images.githubusercontent.com/111736742/220700977-12fd2b7d-0761-428c-bce3-15a07abe17b0.png)

## Ansible-Node Configuration
```bash
cd /etc/ansible
sudo vi hosts
--------------------
#And Place This content
[TomcatServers]
#node-1
172.31.42.33
#node-2
172.31.34.221
#node-3
172.31.38.224
#node-4
172.31.35.200
----------------------
```
![ansible-2-node](https://user-images.githubusercontent.com/111736742/220701143-27305434-f8f4-456c-9785-747bcd145251.png)
## To check connectvity between ansible-master & nodes
![ansible-ping](https://user-images.githubusercontent.com/111736742/220707106-fb8979ff-bb1e-46ad-9e5c-0289020f0bb3.png)

