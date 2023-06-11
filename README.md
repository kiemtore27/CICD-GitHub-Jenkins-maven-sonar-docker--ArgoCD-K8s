# CICD-GitHub-Jenkins-maven-sonar-docker--ArgoCD-K8s
1. Install the necessary Jenkins plugins:
   1.1 Git plugin
   1.2 Maven Integration plugin
   1.3 Pipeline plugin
   1.4 Kubernetes Continuous Deploy plugin

2. Create a new Jenkins pipeline:
   2.1 In Jenkins, create a new pipeline job and configure it with the Git repository URL for the Java application.
   2.2 Add a Jenkinsfile to the Git repository to define the pipeline stages.

3. Define the pipeline stages:
    Stage 1: Checkout the source code from Git.
    Stage 2: Build, test and package the Java application into JAR file using Maven.
    Stage 3: Run SonarQube analysis to check the code quality.
    Stage 4: run docker build to create an image from docker file and push that image in docherhub private registry.
    Stage 5: run shell command to update the kubernetes deployment file using the latest image pushed in dockerhub registry.
    Stage 6: run shell command to push the UPDATED K8S DEPLOYMENT FILE into a 2nd github repo dedicated to deployment files.
    Stage 8: Promote the application to a production environment using Argo CD.


4. Set up Argo CD:
    Install Argo CD on the Kubernetes cluster.
    Define K8s cluster URL in ArgoCD UI.
    Define the back github repo URL in ArgoCD UI. 
    These steps will allow ArgoCD to track the changes in Backed Github repo and continuously deploy the YAML File into Kubernetes cluster in prod environment.
    

5. Configure Jenkins pipeline to integrate with Argo CD:
   6.1 Add the Argo CD API token to Jenkins credentials.
   6.2 Update the Jenkins pipeline to include the Argo CD deployment stage.

6. Run the Jenkins pipeline:
   7.1 Trigger the Jenkins pipeline to start the CI/CD process for the Java application.
   7.2 Monitor the pipeline stages and fix any issues that arise.