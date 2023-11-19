# Web Application to display Continuous Integration and Continuous Deployment in action.

## Basic CI/CD Pipeline
![image](https://github.com/velvet-jedi/webapp/assets/132247456/290925a3-9c92-4622-b7db-944c7afa6b6a)

## Secure SDLC / DevSecOps Pipeline
![image](https://github.com/velvet-jedi/webapp/assets/132247456/43bdc993-3d6d-424f-b56a-8b50a7f97893)


# How to Think?
1. What needs a security check?
2. What can be automated? 
3. Where can we get metrics from?
4. Dealing with false positives.
5. SSDLC can't replace an actual pentest.

# Project Timeline
## 1. Deploy Ubuntu EC2 instances.
   - Create a new SSH key pair to log into the machines using CLI.
   - Set the security groups.
   - edit the hosts file and add the new hosts for reachability from the local machine.
     ```sudo nano /etc/hosts
     ``` IP jenkins
     ``` IP tomcat
   - Restart the host networking service ```sudo /bin/systemctl restart systemd-hostnamed```
   - SSH into the machines <br>
   ```chmod 0600 keyfile.pem```<br>
   ```ssh -i keyfile.pem ubuntu@jenkins```<br>
   ```ssh -i keyfile.pem ubuntu@tomcat```

## 2. Setup Jenkins Server
   - Installing JAVA JDK, docker, maven, and suggested plugins (maven integration, SSH agent, Blue Ocean).
   - Activate Jenkins.
   - Configure maven installation from ```/usr/share/maven```

## 3. Set up the Tomcat server on the EC2 instance.
   - Install JAVA

## 4. Creating Build Pipeline in Jenkins.
   - Build the webapp pipeline project in Jenkins using Github url.
   - Automate in Build Triggers 
   - **Jenkinsfile.old** file stages.

## 5. Continuous Deployment to Tomcat through Jenkins pipeline.
   - Adding SSH creds for the Tomcat server in the Jenkins server
   - To transfer the .war file from the build to the tomcat server using SCP.
  
## 6. Checking leaked secrets in the pipeline before building.
   - Trufflehog (regex-based) docker image
  
## 7. Source Composition Analysis
   - The OWASP Dependency Checker script is downloaded on the Jenkins server and run.
   - It checks the NVD for vulnerabilities in the dependencies.
   - Maven uses pom.xml to consolidate the configuration and dependency-related information for scanning prior to build.

## 8. SAST integration in Jenkins pipeline using SONARQUBE
   - Run SONARQUBE in the docker container
     ```docker run -d -p 9000:9000 sonarqube```
   - Install SONARQUBE scanner plugin and configure it in Jenkins, generate the auth token, give the server URL
     ```http://jenkins_IP:9000

## 9. Integrating DAST with ZAP-Baseline Scan in Pipeline
   - Add a dedicated server for ZAP docker image to run.
   - Use baseline scan as opposed to authenticated scan for faster results.
   - Add SSH private key as credential for ZAP server in Jenkins
 
# DefectDojo
We consolidate the metrics from all the security checks between the CI and the artefactory, to feed into JIRA as one.
