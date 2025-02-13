CICD Project for practice
Tools used in this project:
   git, github. maven, jenkins, Tomcat

Commands for Tools installlation
1) Install Git
   # Yum install git -y
2) Install Maven
   # yum install maven -y

3) Downloading and installing Jenkins
OPEN Link In Browser : https://www.jenkins.io/doc/tutorials/tutorial-for-installing-jenkins-on-AWS/

To perform a quick software update:
[ec2-user ~]$ sudo yum update –y

Add the Jenkins repo using the following command:
[ec2-user ~]$ sudo wget -O /etc/yum.repos.d/jenkins.repo \
    https://pkg.jenkins.io/redhat-stable/jenkins.repo

Import a key file from Jenkins-CI to enable installation from the package:
[ec2-user ~]$ sudo rpm --import https://pkg.jenkins.io/redhat-stable/jenkins.io-2023.key
[ec2-user ~]$ sudo yum upgrade

Install Java (Amazon Linux 2023):
[ec2-user ~]$ sudo dnf install java-17-amazon-corretto -y

Install Jenkins:
[ec2-user ~]$ sudo yum install jenkins -y

Enable the Jenkins service to start at boot:
[ec2-user ~]$ sudo systemctl enable jenkins

Start Jenkins as a service:
[ec2-user ~]$ sudo systemctl start jenkins

You can check the status of the Jenkins service using the command:
[ec2-user ~]$ sudo systemctl status jenkins

4) Install Tomcat
   OPen Link in Browser: https://downloads.apache.org/tomcat/tomcat-11/v11.0.3/bin/
cd /opt
wget https://downloads.apache.org/tomcat/tomcat-11/v11.0.3/bin/apache-tomcat-11.0.3.tar.gz
tar -zxvf apache-tomcat-11.0.3.tar.gz
cd apache-tomcat-11.0.3
cd bin/ ---> ./shutdown.sh
cd conf/   -->vi server.xml  --> change port number 8080 to (8082 or any)
cd conf/   -->vi tomcat-users.xml  --> 3YY copy 3lines and paste P
     add roles and user name and password
     -->
     <role rolename="manager-gui" />
     <role rolename="manager-script" />
     <role rolename="manager-jmx" />
     <role rolename="manager-status" />
     <role rolename= "admin-gui" />
     <user username="tomcat" password="123456" roles="manager-gui, manager-script, manager-jmx, manager-status, admin-gui"/>

cd webapps/manager/META-INF/ -->vi context.xml  --> delete 2 lines 2DD <valve....>
cd bin/  ---> ./startup.sh

5) open browser    public ip of ec2:8082    enter username & password

jenkins>>>>manage jenkins>manage plugins>available plugin>deploy to container (install plugin for deployment)
jenkins>>>>newitem>job1>freestyle project>
 git:provide url  
 build steps>clean package
 post build actions> deploy war/ear to container> tomcat 9.x server> provide credentials(username&password) and URL of tomcat
 save and Build now  >>> application will be deployed






   
