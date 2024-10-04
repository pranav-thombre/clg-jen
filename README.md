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
