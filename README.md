# Web Application to display Continuous Integration and Continuous Deployment in action.

Basic CI/CD Pipeline
![image](https://github.com/velvet-jedi/webapp/assets/132247456/290925a3-9c92-4622-b7db-944c7afa6b6a)



# How to THINK?
1. What needs a security check?
2. What can be automated? 
3. Where can we get metrics from?
4. Dealing with false positives.
5. SSDLC can't replace an actual pentest.

# Project Timeline
1. Set up Jenkins server on EC2 instance.
   - Installing Java JDK, docker, maven, and plugins (maven integration, SSH agent, Blue Ocean)

2. Set up the Tomcat server on the EC2 instance.

3. Creating Build Pipeline in Jenkins.
   - Used Jenkinsfile stages

4. Automated Deployment to Tomcat
   - Adding SSH creds for the Tomcat server in the Jenkins server using SCP.
  
5. Checking leaked secrets in the pipeline **before** building.
   - Trufflehog
  
6. Source Composition Analysis
   - Use Snyk / Owasp Dependency Check
   - Maven uses pom.xml to consolidate the configuration and dependency-related information for scanning prior to build.

 
# DefectDojo
We consolidate the metrics from all the security checks between the CI and the artefactory, to feed into JIRA as one.
