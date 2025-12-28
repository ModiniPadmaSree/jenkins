Document shows the implementation of CI/CD pipeline using Azure and Jenkins  
Step 1: Create a New Azure Virtual Machine  
1. Log in to Azure Portal
2. Navigate to Virtual Machines
3. Create a new VM with:
4. OS: Ubuntu 22.04 LTS
5. Size: Standard B1s
6. Authentication: SSH key
7. Configure Security:  
    22 for SSH  
    8080 for Jenkins UI  
  
Step 2:Connect to Azure VM  
       Connect using SSH from local machine  
       ssh -i key.pem ubuntu@<ip_of_VM>  
  
Step 3: Install required packages  
1. Update system packages
2. Install OpenJDK 17
3. Install Jenkins package
4. Start Jenkins service  
  
Step 4: Access Jenkins Dashboard  
        Access Jenkins using: <ip_of_VM>:8080  
  
Step 5: Create Jenkins Pipeline Job
1. Create a Pipeline job - enter the name and type of pipeline
2. Configure Jenkinsfile by writing pipeline script or pipeline script from SCM
3. Define steps to execute a sample Python file including the push, build, test, deploy stages.
  
Step 6: Test pipeline  
     The output will be displayed in jenkins.
