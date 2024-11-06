## DevOps Ass 5
QUESTION: APPLYING CI/CD PRINCIPLES TO WEB DEVELOPMENT USING JENKINS,GIT, AND LOCAL HTTP SERVER(index.html , index.css files used)
- LAUNCH A UNIX/LINUX INSTANCE (AWS/GCP/AZURE) TAKE ACCESS OF IT (MOBAXTERM) KEEP THE KEY PAIRS HANDY AS THEY ARE IN USE FREQUENTLY.
- FOR THE INSTANCE GIVE SSH(22) ,HTTP(80) ,HTTPS(443) ,CUSTOM TCP (8080), IN YOUR INBOUND SECURITY GROUP.
- ALSO GIVE 0.0.0.0/0 (CIDR) IN YOUR OUTBOUND SECURITY GROUP.
- HERE I HAVE USED UBUNTU(24.04).
1) INSTALL JAVA :

sudo apt update

sudo apt upgrade -y

sudo apt install openjdk-17-jdk -y

java --version
--------------------------------------------------------------------

2) THEN FOLLOW THESE STEPS TO INSTALL JENKINS: 

-(THESE ARE LONG TERM SUPPORT(LTS) / STABLE RELEASE)

sudo wget -O /usr/share/keyrings/jenkins-keyring.asc \
  https://pkg.jenkins.io/debian-stable/jenkins.io-2023.key
echo "deb [signed-by=/usr/share/keyrings/jenkins-keyring.asc]" \
  https://pkg.jenkins.io/debian-stable binary/ | sudo tee \
  /etc/apt/sources.list.d/jenkins.list > /dev/null
sudo apt-get update
sudo apt-get install jenkins

jenkins --version (optional)
----------------------------------------------------------------------

3) COPY THE PUBLIC IP:8080
4) sudo cat /var/lib/jenkins/secrets/initialAdminPassword USE THE INITIAL PASS TO LOGIN THIS IS ONLY FOR THE FIRST TIME
5) click on ->install the suggested plugins

GIVE THE NECESSARY CRED :

6) username - 
7) pass - 
8) full name - admin11

- NOTE : INSTALL THE PUBLISH OVER SSH PLUGIN (RESTART OPTIONAL) 
-----------------------------------------------------------------------

9) WHEN YOU START/STOP THE INSTANCE CHANGE THE IP IN THE FOLLOWING :

10) CHANGE THE HOSTNAME (UPDATED IP)(PAYLOAD URL) IN GITHUB WEBHOOK (GO INSIDE OF THE REPO->SETTINGS->WEBHOOK'S)
11) IN JENKINS -> MANAGE JENKINS -> SYSTEM -> LOOK FOR PUBLISH OVER SSH
12) GO IN THE JOB, CLICK ON APPLY -> SAVE
13) GO TO YOUR PIPEPLINE AND THEN CLICK ON BUILD NOW
----------------------------------------------------------------------
TO UNDERSTAND BETTER REFER HERE :(USED UBUNTU 24.04)

- SETUP JENKINS, JAVA -> https://youtu.be/tn2Be1AAiVw?si=OEwN-IGS_wzkG9j-

- To Deploy Github Code to Live Server -> https://youtu.be/8RIFmoWPbhQ?si=fB0glwl6NeM2taTH
--------------------------------------------------------------------------------------------------
