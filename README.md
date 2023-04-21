#Installing-Jenkins-On_Ubuntu
Installation of jenkins on ubuntu

First of all we need to create an ec2 instance, i have created an ubuntu instance, after it we just need to connect to it and update the packages using command.

`sudo apt-get update`

Jenkins support only jdk8 and jdk11, so we need to install jdk11 on our instance.

`sudo apt-get install openjdk-11-jdk`

Now, we will install Jenkins on our system, the first command is used to add the key to our system. 
Issue the following four commands in sequence to initiate the installation from the Jenkins repository:

` curl -fsSL https://pkg.jenkins.io/debian-stable/jenkins.io.key | sudo tee \
/usr/share/keyrings/jenkins-keyring.asc > /dev/null`

`echo deb [signed-by=/usr/share/keyrings/jenkins-keyring.asc] \
  https://pkg.jenkins.io/debian-stable binary/ | sudo tee \
  /etc/apt/sources.list.d/jenkins.list > /dev/null`

`sudo apt-get update`

`sudo apt-get install jenkins`

Congratulations, jenkins has been installed, but now you need to start jenkins service using command

`sudo systemctl start jenkins.service`

You can check the status using command

`sudo systemctl status jenkins`

The default initial password to login to jenkins can be found here

`sudo cat /var/lib/jenkins/secrets/initialAdminPassword`

With Jenkins installed, we can proceed with adjusting the firewall settings. By default, Jenkins will run on port 8080.

In order to ensure that this port is accessible, we will need to configure the built-in Ubuntu firewall (ufw). To open the 8080 port and enable the firewall, use the following commands:

`sudo ufw allow 8080
sudo ufw enable`
Once done, test whether the firewall is active using this command:

`sudo ufw status`
