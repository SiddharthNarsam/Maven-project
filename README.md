hiii
ccc
a
ok
oooookkkkk
okkkkkk
ytdjhg
trhvjbknm
https://github.com/SarvikaSomishetty/eclipse-maven-projects
[CRLF]> Please use the following password to proceed to installation:
[CRLF]>
[CRLF]> 060b0cabfb314bb58e000cd2227e8a9d
[CRLF]>
[CRLF]> This may also be found at: C:\Users\ndasa\.jenkins\secrets\initialAdminPassword
[CRLF]>



[CRLF]> 060b0cabfb314bb58e000cd2227e8a9d
[CRLF]>
[CRLF]> This may also be found at: C:\Users\ndasa\.jenkins\secrets\initialAdminPassword


"C:\Program Files\Java\jdk-17\bin\java" -jar C:\Users\ndasa\Downloads\jenkins.war --httpPort=9090


criz xfwy anun popm

<role rolename="manager-script"/>
  	<user username="admin" password="1234" roles="manager-script"/>


    Copy Artifact Plugin
    Delivery Pipeline Plugin
    Deploy to container Plugin
    Email Extension Plugin
    Pipeline
    Build Pipeline Plugin













    1. Steps for MavenJava Automation:
Maven Java Automation Steps:
Step 1: Open Jenkins (localhost:8080)
├── Click on "New Item" (left side menu
Step 2: Create Freestyle Project (e.g., MavenJava_Build)
├── Enter project name (e.g., MavenJava_Build)
├── Click "OK"
└── Configure the project:
├── Description: "Java Build demo"
├── Source Code Management:
└── Git repository URL: [GitMavenJava repo URL]
├── Branches to build: */Main or */master
└── Build Steps:
├── Add Build Step -> "Invoke top-level Maven targets"
└── Maven version: MAVEN_HOME
└── Goals: clean
├── Add Build Step -> "Invoke top-level Maven targets"
└── Maven version: MAVEN_HOME
└── Goals: install
└── Post-build Actions:
├── Add Post Build Action -> "Archive the artifacts"
└── Files to archive: **/*
├── Add Post Build Action -> "Build other projects"
└── Projects to build: MavenJava_Test
└── Trigger: Only if build is stable
└── Apply and Save
└── Step 3: Create Freestyle Project (e.g., MavenJava_Test)
├── Enter project name (e.g., MavenJava_Test)
├── Click "OK"
└── Configure the project:
├── Description: "Test demo"
├── Build Environment:
└── Check: "Delete the workspace before build starts"
├── Add Build Step -> "Copy artifacts from another project"
└── Project name: MavenJava_Build
└── Build: Stable build only // tick at this
└── Artifacts to copy: **/*
├── Add Build Step -> "Invoke top-level Maven targets"
└── Maven version: MAVEN_HOME
└── Goals: test
└── Post-build Actions:
├── Add Post Build Action -> "Archive the artifacts"
└── Files to archive: **/*
└── Apply and Save
└── Step 4: Create Pipeline View for Maven Java project
├── Click "+" beside "All" on the dashboard
├── Enter name: MavenJava_Pipeline
├── Select "Build pipeline view" // tick here
|--- create
└── Pipeline Flow:
├── Layout: Based on upstream/downstream relationship
├── Initial job: MavenJava_Build
└── Apply and Save OK
└── Step 5: Run the Pipeline and Check Output
├── Click on the trigger to run the pipeline
├── click on the small black box to open the console to check if the build is success 
Note :
7. If build is success and the test project is also automatically triggered with name 
“MavenJava_Test”
8. The pipeline is successful if it is in green color as shown ->check the console of the test 
project
9. The test project is successful and all the artifacts are archived successfully
II. Maven Web Automation Steps:
└── Step 1: Open Jenkins (localhost:8080)
├── Click on "New Item" (left side menu)
└── Step 2: Create Freestyle Project (e.g., MavenWeb_Build)
├── Enter project name (e.g., MavenWeb_Build)
├── Click "OK"
└── Configure the project:
├── Description: "Web Build demo"
├── Source Code Management:
└── Git repository URL: [GitMavenWeb repo URL]
├── Branches to build: */Main or master
└── Build Steps:
├── Add Build Step -> "Invoke top-level Maven targets"
└── Maven version: MAVEN_HOME
└── Goals: clean
├── Add Build Step -> "Invoke top-level Maven targets"
└── Maven version: MAVEN_HOME
└── Goals: install
└── Post-build Actions:
├── Add Post Build Action -> "Archive the artifacts"
└── Files to archive: **/*
├── Add Post Build Action -> "Build other projects"
└── Projects to build: MavenWeb_Test
└── Trigger: Only if build is stable
└── Apply and Save
└── Step 3: Create Freestyle Project (e.g., MavenWeb_Test)
├── Enter project name (e.g., MavenWeb_Test)
├── Click "OK"
└── Configure the project:
├── Description: "Test demo"
├── Build Environment:
└── Check: "Delete the workspace before build starts"
├── Add Build Step -> "Copy artifacts from another project"
└── Project name: MavenWeb_Build
└── Build: Stable build only
└── Artifacts to copy: **/*
├── Add Build Step -> "Invoke top-level Maven targets"
└── Maven version: MAVEN_HOME
└── Goals: test
└── Post-build Actions:
├── Add Post Build Action -> "Archive the artifacts"
└── Files to archive: **/*
├── Add Post Build Action -> "Build other projects"
└── Projects to build: MavenWeb_Deploy
└── Apply and Save
└── Step 4: Create Freestyle Project (e.g., MavenWeb_Deploy)
├── Enter project name (e.g., MavenWeb_Deploy)
├── Click "OK"
└── Configure the project:
├── Description: "Web Code Deployment"
├── Build Environment:
└── Check: "Delete the workspace before build starts"
├── Add Build Step -> "Copy artifacts from another project"
└── Project name: MavenWeb_Test
└── Build: Stable build only
└── Artifacts to copy: **/*
└── Post-build Actions:
├── Add Post Build Action -> "Deploy WAR/EAR to a container"
└── WAR/EAR File: **/*.war
└── Context path: Webpath
└── Add container -> Tomcat 9.x remote
└── Credentials: Username: admin, Password: 1234
── Tomcat URL: https://localhost:8085/
└── Apply and Save
└── Step 5: Create Pipeline View for MavenWeb
├── Click "+" beside "All" on the dashboard
├── Enter name: MavenWeb_Pipeline
├── Select "Build pipeline view"
└── Pipeline Flow:
├── Layout: Based on upstream/downstream relationship
├── Initial job: MavenWeb_Build
└── Apply and Save
└── Step 6: Run the Pipeline and Check Output
├── Click on the trigger “RUN” to run the pipeline 
Note:
10. After Click on Run -> click on the small black box to open the console to check if the build is 
success
11. Now we see all the build has success if it appears in green color
├── Open Tomcat homepage in another tab
├── Click on the "/webpath" option under the manager app 
Note:
12. It ask for user credentials for login ,provide the credentials of tomcat.
13. It provide the page with out project name which is highlighted. 
After clicking on our project we can see output
Week 9: Pipeline Creation using script
Procedure
General :
Description :- provide the description of the project
Build triggers: here we can provide with build triggers of you choice
Advance project option: 
Definition:
Choose pipeline script
Here code for pipeline -script
Copy the code there
pipeline { 
agent any 
tools{
maven 'MAVEN-HOME'
}
stages {
stage('git repo & clean') { 
steps {
//bat "rmdir /s /q mavenjava"
bat "git clone provide your github link" 
bat "mvn clean -f mavenjava"
}
}
stage('install') { 
steps {
bat "mvn install -f mavenjava" #project name#
}
}
stage('test') { 
steps {
bat "mvn test -f mavenjava"
}
}
stage('package') { 
steps {
bat "mvn package -f mavenjava"
}
}
}
}
Apply and save
pipeline { 
agent any 
tools {
maven 'M3'
}
stages{
stage('gitrepo & clean'){ 
steps {
// Remove the old folder if it exists 
bat 'rmdir /s/q 5A7week9 || exit 0'
// Clone your GitHub repo
bat'git clone https://github.com/vd-007-b/SE-Week4.Projects.git 5A7week9'
// Clean the project using Maven
bat 'mvn clean -f 5A7week9/pom.xml'
}
}
stage('install'){ 
steps {
bat 'mvn install -f 5A7week9/pom.xml'
}
}
stage('test'){ 
steps {
bat 'mvn test -f 5A7week9/pom.xml'
}
}
stage('package') { 
steps {
bat 'mvn package -f 5A7week9/pom.xml'
}
}
}
}
WEEK 10
Working with minikube and Nagios
1. Hands-on practice of creating, running and scaling pods in minikube.
2. Running Nginx server on specified port number by explaining the Nginx monitoring tool
3. Running Nagios server and Understanding the Monitoring tool using Docker.
4. AWS-free Trier account Creation steps
5. Upload the screenshots for the tasks
Kubernetes:
Kubernetes is a tool that automates how we run and manage applications inside the container.
Dockers will only run containers, if in any case the container fails/stopped/killed, the docker will not help us, here is 
where Kubernetes plays an important role, Kubernetes cluster will be responsible in creating a new container and 
managing various containers.
POD: In Kubernetes, a Pod is the smallest deployable unit that you can create and manage.
Minikube:
Minikube creates a VM on your local machine and deploys a simple Kubernetes cluster with one node. It's a 
lightweight implementation.Minikube is a version of Kubernetes.
Nagios:
Nagios is an open-source IT infrastructure monitoring tool. It monitors
• Serrvers
• Network devices
• Applications and services
It alerts admnistrators when issues occur and notifies when they are resolved.
Step 1: Install Prerequisites
Before installing Minikube, ensure the following are installed:
1. Virtualization Support:
o Verify virtualization is enabled:
2. Hypervisor:
o Minikube supports multiple hypervisors (e.g., Hyper-V, VirtualBox, or Docker as a driver).
o Install one of the following:
▪ Hyper-V (pre-installed on Windows 10/11 Pro or Enterprise).
▪ Docker Desktop (if you want to use Docker as the driver).
Step 2: Download Minikube
1. Open a PowerShell or Command Prompt with administrator privileges.
2. Download the latest Minikube executable using this command:
3. curl -LO https://storage.googleapis.com/minikube/releases/latest/minikube￾installer.exe
4. Install Minikube by running the installer:
5. .\minikube-installer.exe
Step 3: Add Minikube to PATH
If Minikube is not automatically added to your PATH during installation:
1. Open System Properties → Environment Variables.
2. Add the directory where Minikube isinstalled (e.g., C:\Program Files\Minikube) to your PATH 
variable.
Step 4: Start Minikube
1. Open a terminal (PowerShell or CMD). Do the following commands
2. Start Minikube with a specified driver (e.g., Hyper-V, Docker, or VirtualBox). For example:
o Hyper-V:
o minikube start --driver=hyperv
o Docker:
o minikube start --driver=docker
3. Verify Minikube is running:
4. minikube status
Step 5: Interact with Minikube
kubectl is a command-line tool used in Kubernetes to interact with and manage Kubernetes clusters.
Once Minikube is running:
1. Use kubectl to interact with the cluster.
o Install kubectl if not already installed:
o minikube kubectl -- get pods -A
o Or download itseparately from the official Kubernetessite.
2. Open the Minikube dashboard (optional):
3. minikube dashboard
Optional: Check Your Installation
Run the following to verify the installation:
Minikube version
kubectl version –client
Troubleshooting
1. If Minikube fails to start:
o Ensure your hypervisor (Hyper-V/Docker/VirtualBox) isinstalled and running.
o Check the Minikube logs:
o minikube logs
2. Updating Minikube:
3. minikube update-check
4. minikube update
Minikube Automation Steps
Step 1: Start Minikube Cluster
 Open your terminal and run the command:
minikube start
Step 2: Create and Manage Deployment
1. Create an application in Kubernetes:
o Command:
kubectl create deployment mynginx --image=nginx
if already created then 
kubectl set image deployment/myngnix nginx=nginx:latest
o Verify the deployment using: Kubernetes responds by showing you a list that includes 
the names of your deployment groups
kubectl get deployments
▪ Ensure mynginx appears in the output.
Check the following commands:
■ kubectl get pods
■ kubectl describe pods
2. Expose Deployment as a Service:
o Command:
kubectl expose deployment mynginx --type=NodePort --port=80 --target￾port=80
Step 3: Scale the Deployment
Command:Scales the Nginx deployment to 4 replicas (pods). 
kubectl scale deployment mynginx --replicas=4 
kubectl get service myngnix
Step 4: Access the Nginx App
1. Using Port Forwarding:
o Command:
kubectl port-forward svc/mynginx 8081:80
▪ Access the app via http://localhost:8081.
If Error, use this option, Using Minikube Tunnel:
o Start the tunnel:
minikube tunnel
o Retrieve the service URL:
minikube service mynginx --url
o Open the provided URL in your browser.
o Open the kubernets dashboard
• Open the minikube dashboard
Minikube dashboard
Step 5: Stop and Clean Up
1. Stop Nginx Deployment:
o Commands:
kubectl delete deployment mynginx 
kubectl delete service mynginx
2. Stop Minikube (Optional):
o Command:
minikube stop
3. Delete Minikube Cluster (Optional):
o Command:minikube delete
Nagios Automation Steps
Step 1: Pull the Nagios Docker Image
 Open a terminal and run:
docker pull jasonrivers/nagios:latest
Step 2: Run Nagios
 Command:
docker run --name nagiosdemo -p 8888:80 jasonrivers/nagios:latest
Step 3: Access Nagios Dashboard
 Open your browser and navigate to:
http://localhost:8888
o Login Credentials:
▪ Username: nagiosadmin
▪ Password: nagios
o Once logged in, explore:
▪ Hosts: View systems being monitored.
▪ Services: Check tasks being monitored (e.g., CPU usage).
▪ Alerts: Access recent notifications.
Step 4: Monitoring Host Details
1. Navigate to the Host Information Page:
o Select a host from the Hosts menu.
2. Key Details:
o Host Status: Indicates if the system is UP or DOWN.
o Metrics: View CPU usage, memory status, and network activity.
o Actions: Reschedule checks, disable notifications, or schedule downtime.
Step 5: Stop and Remove Nagios
1. Stop the Container:
o Command:
docker stop nagiosdemo
2. Delete the Container:
o Command:
docker rm nagiosdemo
3. Remove the Image (Optional):
o List images:
docker images
o Delete the Nagios image:
docker rmijasonrivers/nagios:latest
4. Observe the docker containers in DockerHub, we can see the latest Nagios 
Installed running on port:8888
-------------------------------------------------------------------------------------------------------------------------------
Steps for AWS-free trier account creation
• open https://aws.amazon.com
• click on create AWS account
• Provide email id and name details for AWS account creation then a screen will appear as 
below
• Enter verification code received in your mail
• Provide your contact details and agree Terms and conditions, then click on create
• Provide billing details, click on verify and continue
• Amazon chagres 2 rs and it will be credit back into your account once verification is over
• Once payment success a screen appear as below, provide your working contact number 
after selecting country, and click on send SMS after entering the details
• Provide verification code received in your mobile
• Now select basic plan and click on complete sign up
• Now a screen appear as follows then click on AWS management console
• You will navigating to the aws page ..where you need to Select role as Academic/Researcher 
and interest as DevOps and click on submit
• Sign into AWS console as Root user
• A console screen appears aws will appear
LAB ACTION PLAN FOR WEEK 11
Jenkins-CI/CD
14. CI-Continous Integration using Webhooks .
15. Sending E-mail Notification on Build Failure or success
16. Upload the screenshots for the tasks
Lab
Setting Up Jenkins CI------using GitHub Webhook with Jenkins
Step 1: Configure Webhook in GitHub
17. Go to your GitHub repository.
18. Navigate to Settings → Webhooks.
19. Click “Add webhook”.
20. In the Payload URL field:
1. Enter the Jenkins webhook URL in the format: 
http://<jenkins-server-url>/github-webhook/
Note: If Jenkinsis running on localhost, GitHub cannot access it directly.
Use ngrok to expose your local Jenkins to the internet:
2. ngrok.exe http <Jenkins local host:8080>
1. Use the generated ngrok URL, e.g.:
2. http://abc123.ngrok.io/github-webhook/
21. Set Contenttype to: 
application/json
22. Under “Which events would you like to trigger this webhook?”, select:
1. Just the push event
23. Click “Add webhook” to save.
Step 2: Configure Jenkinsto Accept GitHub Webhooks
24. Open Jenkins Dashboard.
25. Select the job (freestyle or pipeline) you’ve already created.
26. Click Configure.
27. Scroll down to the Build Triggers section.
28. Check the box: ⬛ GitHub hook trigger for GITScm polling
29. Click Save.
30.
Step 3: Test the Setup
31. Make any code update in your local repo and push it to GitHub.
32. Once pushed, GitHub will trigger the webhook.
33. Jenkins will automatically detect the change and start the build pipeline.
outcome
34. You’ve successfully connected GitHub and Jenkins using webhooks.
35. Every time you push code to GitHub, Jenkins will automatically start building your project without 
manual intervention.
Set-uping the ngrok
How to Install and Use ngrok 
Step 1. Download ngrok
https://ngrok.com/download
Download and extract it for your OS (Windows, macOS, or Linux).
Step 2. Connect Your ngrok Account (optional but useful)
After you sign up (free), ngrok gives you an auth token.
CREATE AUTHENTICATOR [https://dashboard.ngrok.com/get-started/your-authtoken] 
Run this command (replace <your_token> with yours):
ngrok config add-authtoken <your_token>
This ensuresstable sessions and more control. 
Step 3. Start a Tunnel for Jenkins
Assuming Jenkins runslocally on port 8085:
ngrok http 8085
You’llsee output like:
Session Status online
Forwarding https://1234abcd.ngrok.io -> http://localhost:8080
Copy the HTTPS URL (https://1234abcd.ngrok.io) — this is your public Jenkins URL for webhooks. 
Step 4. Use it in GitHub Webhook
In your GitHub repo → Settings → Webhooks:
36. Payload URL: [paste the url generated by ngrok]
https://1234abcd.ngrok.io/github-webhook/ [please include this – remaining all default]
Now, whenever you push code, GitHub sends an event to that URL, which ngrok forwards to your local 
Jenkins.
------------------------------------------------------------------------------------------------------------------------------------------
Setting Up Jenkins Email Notification Setup (Using Gmail with App Password)
Creation of app password
1. Gmail: Enable App Password (for 2-Step Verification)
i. Go to: https://myaccount.google.com
ii. Enable 2-Step Verification
37. Navigate to:
1. Security → 2-Step Verification
2. Turn it ON
3. Complete the OTP verification process(via phone/email)
iii. Generate App Password for Jenkins
38. Go to:
1. Security → App passwords
39. Select:
1. App: Other (Custom name)
2. Name: Jenkins-Demo
40. Click Generate
41. Copy the 16-digit app password
1. Save it in a secure location (e.g., Notepad)
2. Jenkins Plugin Installation
i. Open JenkinsDashboard
ii. Navigate to:
1. Manage Jenkins → Manage Plugins
iii. Install Plugin:
2. Search for and install:
a. Email Extension Plugin
3. Configure Jenkins Global Email Settings
i. Go to:
3. Manage Jenkins → Configure System
A. E-mail Notification Section 
Field Value
SMTP Server smtp.gmail.com
Use SMTP Auth ⬛Enabled
User Name Your Gmail ID (e.g., 
archanareddykmit@gmail.com)
Password Paste the 16-digit App Password
Use SSL ⬛Enabled
SMTP Port 465
Reply-To Address Your Gmail ID (same as above)
> Test Configuration
1. Click: Test configuration by sending test e-mail
2. Provide a valid email address to receive a test mail
3. ⬛Should receive email from Jenkins
B. Extended E-mail Notification Section 
Field Value
SMTP Server smtp.gmail.com
SMTP Port 465
Use SSL ⬛Enabled
Credentials Add Gmail ID and App Password as Jenkins credentials
Default Content Type text/html or leave default
Default Recipients Leave empty or provide default emails
Triggers Select as per needs(e.g., Failure)
Field Value
4. Configure Email Notificationsfor a Jenkins Job
i. Go to:
4. Jenkins → Select a Job → Configure
ii. In the Post-build Actions section:
5. Click: Add post-build action → Editable Email Notification
A. Fill in the fields:
Field Value
Project Recipient List Add recipient email addresses (comma-separated)
Content Type Default (text/plain) or text/html
Triggers Select events(e.g., Failure, Success, etc.) 
Attachments (Optional) Add logs, reports, etc.
iii. Click Save
Now your Jenkinsjob is set up to send email notifications based on the build status!
1.
Takeaway :
Students learned how to integrate Jenkins with GitHub using webhooksto automate build triggers and 
configure email notifications to monitor build success or failure effectively.
Week 12: Creation of virtual machine for Ubuntu OS and Deploying the web application
1. Creation of virtual machine
2. Deploying the web application 
3. Accessing it publicly
ssh -i "A7ADkeypair.pem" ubuntu@ec2-34-229-172-6.compute-1.amazonaws.com


12.Creation of virtual machine for Ubuntu OS and Deploying the web application
DEPLOYMENT OF INDEX.HTML USING EC2 INSTANCE in AWS
Step 1: Click on Modules.
Step 2: Scroll down and select Lunch AWS Academy Lab
Step 3: click on start lab
Step 4: click on AWS and in the services select EC2
Step 5: select instances and select instance click on launch instance
Step 6: Give the name of the machine “week-122”
Step 6: Select the ubuntu server
Step 7: select architecture as 64-bit and instance type as t3.micro(i.e., they are free)
Step 8: Create a new keypair and select type as RSA and .pem option and click on create key pair
Step 9: In network settings select “create security group” and give the security group name
Step 10: Click on edit button on the top right corner and select
Type: ssh
Source: anywhere
Step 11: in configure storage give 8GB and give number of instances as 2 and click on launch instance
Step 12: The launching of instance will start and successful message will be shown
Step 13: In the instances the created ones will be shown, you can also rename the instance , changed 
week-1222 to “webapp”
Step 14: click on connect and select “SSH Client” and copy the ssh command
Step 15: Navigate to the path where the file with .pem extension is present(week-122.pem) and paste 
the command
Step 16: check the docker and git version
If they are not present, then go to administrative terminal using command 
“sudo su”
Then update using the command “sudo apt-get update”
Step 17: use command “sudo apt-get install docker.io” to install docker
Step 18: Clone the git repo that has maven project and change to that directory
Step 19: change to the project directory and check for Dockerfile, if not present create the Dockerfile –
“nano Dockerfile” and then build the image
“sudo docker build -t image_name .” name of image:img1
Step 20: Run the image “sudo docker run -d -p 8081:8080 img1”
Step 21: Chcek the images and the containers
Step 22: Take the public IP address from the instances in AWS and open it in chrome along with the port 
number mapped.
Public IP- 13.222.21.231
Port used: 8081
Use: 13.222.21.231:8081, you will find your application that is deployed