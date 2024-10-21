# YahyaSadekMohammedSadek 

# This is a CI/CD Pipeline of a Java Web App stack using Jenkins using Docker and on Kubernetes Cluster
# Prequisites for this project is divided into 3 parts (JenkinsServer,SonarQubeServer,KopsServer) 

# JenkinsServer #
# first we'll create a jenkins server from the documentation, install following plugins in Jenkins
# (SonarQube,BuildTimestamp,PipelineMavenIntegrationPlugin,Docker-Pipeline,Docker,PipelineUtility)
# and the following tools (maven & sonarqube scanner 4.7)
# connect sonarqube server to jenkins with credentials, connect dockerhub's credentials to jenkins
# we'll also install docker engine on the jenkins server and make jenkins user in docker's group
# Set Kops VM (Ubuntu user) as a Jenkins slave (node) using its SSH key, using also non verifying verification strategy       

# SonarQubeServer #
# setting up the server using the sonar-setup.sh, once it's made can be logged to by username:admin, password:admin
# after the first pipeline run, use webhook in sonarQube so that it can reply back to jenkins with the acceptance or denial of the Quality Gates

# KopsVM #
# Launch EC2 instance, install on it (Kops, Helm, Kubectl, AWS CLI, jdk8 (for Jenkins slave)) and create Route53 & S3 Bucket & purchase DNS 
# Domain for the K8s Cluster
# make sure java is installed, create a directory which will be specified in jenkins as a remote dir in which jenkins will have its workspace
# Give ubuntu user the ownership of the remote directory
# Create the cluster using Kops
# in a directory, using "helm create <chartname>", and go into the template and replace its content with the kubernetes definition files
# add the namespace "prod" in order to isolate the resources
# For DB I've created EBS mapped to the container configurations file /var/lib/mysql
# An EBS must be created in the same region as the MySQL Pods & tagged with Key=KubernetesCluster, Value=""the name of the k8s cluster we chosen""
# so label the node thats in the same region as the EBS and matchLabel all the MySQL Pods to that node through Deployment


# The Pipeline contains the following by Jenkins server:- 1) building the artifact [maven], 2) testing it using unit test
# 3) integrity test 4) Checkstyle test, 5) then using code-analysis and sending all the reports to the sonarqube server
# 6) the sonarqube server responds with the qualitygate verdict, 7) building the application image using docker with the dockerhub registry name
# 8) Pushing this image to dockerhub registry. 9) cleaning up the jenkins server. 
# 10) Deploying through the KubernetesCluster using Helm Charts (on KOPS VM as a Jenkins slave) the application stack using the Kubernetes 
# Definition files  .

# the application stack on Kubernetes is typically the following objects (Secret file for sensitive data, 3 ClusterIP Services for backend services)
# (1 LoadBalancer Service for the frontend service, 4 Deployments for all of the services of the app stack)  [FE: Tomcat, BE: MySQL, Memcache, RabbitMQ]






