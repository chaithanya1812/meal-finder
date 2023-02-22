## Jenkins-Ansible-Apache Tomcat
## Image
![ansible-1](https://user-images.githubusercontent.com/111736742/220746641-259b683e-84d4-49db-90d7-964c61aa90ea.jpg)

## Ansible-Installation
```bash
wget https://dl.fedoraproject.org/pub/epel/epel-release-latest-7.noarch.rpm
yum install epel-release-latest-7.noarch.rpm
yum update -y
yum install git python python-devel python-pip openssl ansible -y
ansible --version
```
![ansibleproject](https://user-images.githubusercontent.com/111736742/220749486-3f453b52-0d4a-4813-b72b-9383418dd447.png)
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
## copy this [1.context.xml  2.tomcat-users.xml  3.tomcat.yaml]  content into ansible-master home directory.
#which is there in github-repository.
![ansible-copy-content](https://user-images.githubusercontent.com/111736742/220710173-b34ffe15-d10c-4fcd-80b7-8f2b27a39538.png)

## SonarQube Download & Installation
```bash
cd /opt
wget https://binaries.sonarsource.com/Distribution/sonarqube/sonarqube-8.9.10.61524.zip
unzip sonarqube-8.9.10.61524.zip
mv sonarqube-8.9.10.61524 sonarqube
useradd chaitu
passwd chaitu
chown -R chaitu:chaitu sonarqube
cd /opt/sonarqube/bin/linux-x86-64
vi sonar.sh 
--------------
edit this
#RUN_AS_USER=
RUN_AS_USER=chaitu
su - chaitu
[And start SonarQube]
cd /opt/sonarqube/bin/linux-x86-64
sh sonar.sh start
sh sonar.sh status
ip:9000
```

## Nexus Download & Installation
```bash
yum install java-1.8* -y
cd /opt
wget https://download.sonatype.com/nexus/3/nexus-3.47.1-01-unix.tar.gz
tar -xvzf  nexus-3.47.1-01-unix.tar.gz
mv nexus-3.47.1-01 nexus
useradd chaitu
passwd chaitu
chown -R chaitu:chaitu nexus
chown -R chaitu:chaitu sonatype-work
cd /opt/nexus/bin
vi nexus.rc
--------edit---------
#run_as_user="chaitu"
----------edit--------
sh nexus start
sh nexus status
ip:8081
```
## Before-changes
# Jenkins integration with ansible-master Server
#Goto Manage Jenkins---->Configure System---->SSH Servers
![ansible-Jenkins](https://user-images.githubusercontent.com/111736742/220753163-d50179b8-3da8-4219-afa1-20d82c5c0228.png)
#In index.html
![ansiblebefore-change](https://user-images.githubusercontent.com/111736742/220749101-df46c3a9-fc91-4fc2-a2c7-8cb86558ceee.png)
#JenkinsDashboard
![ansiblejenkins](https://user-images.githubusercontent.com/111736742/220748733-f4ddfa38-588d-4a6f-b967-5391cd355d3a.png)
#Nexus-Artifact
![ansible-nexus](https://user-images.githubusercontent.com/111736742/220749652-cd25e94c-18a8-48b7-bb8b-9581c94c51dc.png)
#Apache-Tomcat-Srever
![ansible-output1](https://user-images.githubusercontent.com/111736742/220749770-6188a933-88b5-460f-b084-93eaf462705b.png)
## After Changes
#index.html
![ansiblefinalchanhe](https://user-images.githubusercontent.com/111736742/220750089-192777ad-7d6d-4f2a-a855-4b55d0cb9d8f.png)
#Apache-Tomcat-Server
![ansiblefinal](https://user-images.githubusercontent.com/111736742/220750225-57abba7a-9afa-4484-845c-8d0f7d8e23a2.png)





