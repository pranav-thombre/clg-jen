1) INSTALL JAVA :

sudo apt update
sudo apt upgrade -y
sudo apt install openjdk-17-jdk -y
java -version
--------------------------------------------------------------------
2) THEN FOLLOW THESE STEPS TO INSTALL JENKINS: 

sudo wget -O /usr/share/keyrings/jenkins-keyring.asc \
  https://pkg.jenkins.io/debian-stable/jenkins.io-2023.key
echo "deb [signed-by=/usr/share/keyrings/jenkins-keyring.asc]" \
  https://pkg.jenkins.io/debian-stable binary/ | sudo tee \
  /etc/apt/sources.list.d/jenkins.list > /dev/null
sudo apt-get update
sudo apt-get install jenkins
----------------------------------------------------------------------

3) COPY THE PUBLIC IP:8080
4) sudo cat /var/lib/jenkins/secrets/initialAdminPassword USE THE INITIAL PASS TO LOGIN THIS IS OLY FOR THE FIRST TIME
5) install the suggested plugins
6) username - admin
7) pass - admin1
8) full name - admin11

