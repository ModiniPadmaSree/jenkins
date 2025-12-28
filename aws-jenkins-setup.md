Jenkins CI/CD pipeline setup on AWS  
This setup uses only Jenkins master without agents.  
Step-1: Launch an EC2 instance in AWS  
1. AWS Console → EC2 → Launch Instance
2. AMI: Ubuntu 22.04 LTS
3. Instance Type: t2.micro
4. Key pair: Use existing key key.pem file or Create a new key pair
5. Security group configure:  
SSH port 22; Custom TCP port 8080(for jenkins); HTTP port 80  
6. Launch instance  
Step-2: Connect to EC2  
In local terminal, command  
ssh -i key.pem username@<EC2_PUBLIC_IP>  
This will connect to the AWS instance.  
Step-3: Installation  
1. Install java  
sudo apt update  
sudo apt install -y openjdk-17-jdk
2. Install Jenkins  
curl -fsSL https://pkg.jenkins.io/debian-stable/jenkins.io-2023.key | sudo tee \  
/usr/share/keyrings/jenkins-keyring.asc > /dev/null  
echo deb [signed-by=/usr/share/keyrings/jenkins-keyring.asc] \  
https://pkg.jenkins.io/debian-stable binary/ | sudo tee \  
/etc/apt/sources.list.d/jenkins.list > /dev/null  
sudo apt update  
sudo apt install -y jenkins
3. Check status and start of jenkins  
sudo systemctl start jenkins  
sudo systemctl enable jenkins
4. In browser, <ip of instance>:8080 to use jenkins
5. Get password by pasting the path in terminal visible on jenkins UI - sudo cat <path> which shows the password, that has to be pasted in jenkins.
6. Install suggested plugins and create username, password and login.  
Step-4:Setup pipeline  
1. Enter the name and type of pipeline
2. In general, choose github project, then insert repo URL which contains the application to be built.
3. Triggers section - choose Github hook which should be established in webhook section of github repo where that application lies.
4. Define pipeline script which has stages - checkout, build, test, deploy or create script in repo and use pipeline script from SCM
5. This executes file(python) which is present in repo  
Step-5: Test the deployment  
It should display the output of file in jenkins  
For python file, run - python <file> in terminal
