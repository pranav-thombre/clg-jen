## DevOps Ass 5
QUESTION: APPLYING CI/CD PRINCIPLES TO WEB DEVELOPMENT USING JENKINS,GIT, AND LOCAL HTTP SERVER(index.html , index.css files used)
- LAUNCH A UNIX/LINUX INSTANCE (AWS/GCP/AZURE) TAKE ACCESS OF IT (MOBAXTERM) KEEP THE KEY PAIRS HANDY AS THEY ARE IN USE FREQUENTLY.
- FOR THE INSTANCE GIVE SSH(22) ,HTTP(80) ,HTTPS(443) ,CUSTOM TCP (8080), IN YOUR INBOUND SECURITY GROUP.
- ALSO GIVE 0.0.0.0/0 (CIDR) IN YOUR OUTBOUND SECURITY GROUP.
- HERE I HAVE USED UBUNTU(24.04).
- ON THE SERVER INSTALL APACHE OR NGINX
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

3) COPY THE PUBLIC IP OF INSTANCE:8080
4) sudo cat /var/lib/jenkins/secrets/initialAdminPassword (THIS IS THE INITIAL PASS TO LOGIN. THIS IS ONLY FOR THE FIRST TIME)
5) click on ->install the suggested plugins

GIVE THE NECESSARY CRED :

6) username - 
7) pass - 
8) full name - admin11

- NOTE : INSTALL THE (publish over ssh) PLUGIN (RESTART OPTIONAL) 
-----------------------------------------------------------------------
## JENKINS OPERATIONS:
9) COPY THE PUBLIC IP OF THE INSTANCE:8080 -> LOGIN INTO JENKINS
10) GO TO JENKINS DASHBOARD -> MANAGE JENKINS ->  CONFIGURE SYSTEM -> LOOK FOR PUBLISH OVER SSH
11) IN "KEY" COPY THE PRIVATE KEY CONTENTS
12) IN SSH SERVERS -> CLICK ON ADD
13) PROVIDE NAME(DEMO-SERVER)
    PROVIDE HOSTNAME(IP ADD OF INSTANCE(REMOVE http://_/)(KEEP ONLY THE IP))
    PROVIDE USERNAME(ubuntu/ec2-user)
    PROVIDE REMOTE DIRECTORY(/var/www/html/) -> CLICK ON TEST CONFIGURATION(TO CHECK IF THE   SETUP IS DONE CORRECTLY OR NOT) -> CLICK ON APPLY -> CLICK ON SAVE
14) CLICK ON NEW ITEM -> PROVIDE ITEM NAME(DEMO-PROJECT) -> CLICK ON FREESTYLE PROJECT -> CLICK ON OK
15) PROVIDE DESCRIPTION -> CLICK ON GitHub project -> PROVIDE THE PROJECT URL(COPY THE GITHUB URL FROM THE TAB()MUST BE A PUBLIC REPO) -> PROVIDE THE SCM(Git) -> PROVIDE THE REPOSITORY URL(GO TO GitHub IN REPO -> CLICK ON CODE -> COPY THE HTTPS URL) -> SPECIFY THE BRANCH(MASTER OR MAIN)
16) PROVIDE THE BUILD TRIGGER(GitHub hook trigger for GITScm polling)
    ## MUST ADD A WEBHOOK IN GITHUB 
    - GO TO GitHub -> YOUR REPO -> SETTINGS -> WEBHOOKS -> COPY THE JENKINS URL FROM THE TAB(http://IP:8080/YOUR_REPO_NAME/) AND PASTE IT IN PAYLOAD URL -> CHECK JUST THE PUSH EVENT -> CLICK ON OK OR UPDATE 
17) PROVIDE THE BUILD ENVIRONMENT(send files or execute commands over SSH after the build runs)
  - YOUR SERVER NAME WILL NOW BE VISIBLE
  - PROVIDE THE SOURCE FILES(**/*.html,**/*.css)(WILL ONLY ALLOWS THOSE FILES WITH THESE EXTENSIONS)
  - PROVIDE THE REMOTE DIRECTORY(/) 
18) CLICK ON APPLY -> CLICK ON SAVE
## TILL HERE WE HAVE CREATED OUR PIPELINE

19) 


-----------------------------------------------------------------------------------------------
) WHEN YOU START/STOP THE INSTANCE CHANGE THE IP IN THE FOLLOWING :

) CHANGE THE HOSTNAME (UPDATED IP)(PAYLOAD URL) IN GITHUB WEBHOOK (GO INSIDE OF THE REPO->SETTINGS->WEBHOOK'S)
) IN JENKINS -> MANAGE JENKINS -> SYSTEM -> LOOK FOR PUBLISH OVER SSH
) GO IN THE JOB, CLICK ON APPLY -> SAVE
) GO TO YOUR PIPEPLINE AND THEN CLICK ON BUILD NOW
----------------------------------------------------------------------
TO UNDERSTAND BETTER REFER HERE :(USED UBUNTU 24.04)

- SETUP JENKINS, JAVA -> https://youtu.be/tn2Be1AAiVw?si=OEwN-IGS_wzkG9j-

- To Deploy Github Code to Live Server -> https://youtu.be/8RIFmoWPbhQ?si=fB0glwl6NeM2taTH
--------------------------------------------------------------------------------------------------
