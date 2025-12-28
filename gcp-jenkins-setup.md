Step 1: Create GCP VM Instance  
1. Go to Google Cloud Console → Compute Engine → VM Instances
2. Click Create Instance
3. Choose Machine type: e2-medium
   OS: Ubuntu 22.04 LTS
4. Under Firewall, allow:
Allow HTTP traffic
5. Click Create
Step 2: Configure Firewall Rules (Jenkins + SSH)  
1. Go to VPC Network → Firewall Rules
2. Create rule:
3. Name:jenkins
4. Direction: Ingress
5. Targets: All instances
6. Source IP ranges: 0.0.0.0/0
7. Protocols & ports:ssh:22
    tcp:8080
8. Save the rule  
Step 3: Generate SSH Key (Local Machine)  
1. ssh-keygen -t rsa -b 4096 -C "gcp-jenkins"
2. Copy public key cat ~/.ssh/id_rsa.pub
3. Add the ssh key in console and paste the result of above command  
Step 4: Connect gcp vm  
Connect to GCP VM Using SSH  
ssh username@VM_EXTERNAL_IP  
Step 5 : Install packages  
1. Install JDK
2. Install Jenkins  
Step 6: Access jenkins  
1. In browser, <ip>:8080 opens the jenkins
2. Copy the path and paste in terminal as sudo cat <path>
3. Paste the password shown in jenkins
4. Set username and password  
Step 7:Create Jenkins Pipeline Job
1. Create a Pipeline job - enter the name and type of pipeline
2. Configure Jenkinsfile by writing pipeline script or pipeline script from SCM
3. Define steps to execute a sample Python file including the push, build, test, deploy stages.  
Step 6: Test pipeline
     The output will be displayed in jenkins
