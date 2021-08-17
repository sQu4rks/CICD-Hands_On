# CICD-Hands_On

## Project

Simple flask application with redis backend - guestbook

## Structure

60 minutes

1. Introduction to CI/CD - 10"
2. Introducing the code project - 5"
3. Hands-On: Running the project locally - 15"
    * Run Redis Container
    * Clone github repository
    * Build docker image
    * Run docker images (app + redis) locally
4. Introduction to testing - 5"
5. Hands-On: Writing a unit test and scenario test - 15"
    * Write a unit test using `unittest`
    * Write a scenario test using `selenium`
6. Introduction to deploying a modern web application - 10"
7. Hands-On: Deploying a web app to Kubernetes - 15"
    * Use K8s files to deploy application by hand
9. Hands-On: Automate the deployment to Kubernetes - 15"
    * Automatically deploy application from gitlab
10. Hands-On: Putting it all together - Build a pipeline - 30"
    * Pipeline to react on code push
    * Pipeline to run tests
    * Pipeline to deploy if tests are succesful
