# jenkins-cypress

## Jenkins EC2 setup

Before Jenkins and EC2 Setup:

Verify you can SSH into your EC2 instance
`ssh -i "/path/to/jenkins2.pem" your-address.region.compute.amazonaws.com`

You may need to change the PEM permissions
`sudo chmod 600 /path/to/jenkins2.pem`

Step 1 : Connect to your Linux machine
SetUp JAVA PATH
Set up Custom TCP port: 8080 in AWS Security Groups

Step 2: Update Packages
sudo yum update

Step 3 : Check Java is installed. If not install java  
`java -version`
`sudo yum install java-1.8.0`

To check and select one out of multiple java versions available
`sudo /usr/sbin/alternatives --config java`

Step 4 : Download latest Jenkins code package
`sudo wget -O /etc/yum.repos.d/jenkins.repo http://pkg.jenkins-ci.org/redhat/jenkins.repo`

Step 5 : Import a key file from Jenkins-CI to enable installation from the package
`sudo rpm --import http://pkg.jenkins-ci.org/redhat/jenkins-ci.org.key`

Step 6 : Install Jenkins
`sudo yum install jenkins`

Step 7 : Start jenkins
`sudo service jenkins start`

Step 8 : Access Jenkins server using the public DNS of your ec2 on port 8080
http://{ec2-public-dns}:8080
example : http://3.89.79.74:8080/
you can find this on the ec2 instance "IPv4 Public IP"

Note : Here you might have to allow port 8080 in your security group settings

Setp 9: Get default admin password
`sudo cat /var/lib/jenkins/secrets/initialAdminPassword`

Step 10: Install Git plugin through plugin manager

Step 11: Configure git plugin with branch url, branches, and when to run git hook (Github hook trigger for GITScm polling)

Step 12: Add webhook to Git
