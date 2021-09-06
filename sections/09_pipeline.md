# Hands-On: Building a pipeline

To begin with our pipeline, we will push our repository to a GitLab project, that we created for you. You can push the existing repo into the new GitLab project using the following commands:

```shell

cd existing_repo
git remote rename origin old-origin
git remote add origin <URL of new repo>
git push -u origin --all

```

In our GitLab repository, we will add a `.gitlab-ci.yml` this file is automatically recognized by GitLab and it is our recipie for our pipeline. With every commit that we push towards this repository, the pipeline will run and excecute all steps that we specify in the file. Such pipelines can also be scheduled to run at a certain time, like once every day.

We have created a YAML file `.gitlab-ci.yml.tpl` for you that will be used to excecute the pipeline by GitLab. In your repository, rename the file to `.gitlab-ci.yml`, so GitLab can understand it. When you commit and push the changes towards the repository, a pipeline will be automatically started executing the first defined steps.

Every pipeline can consist of a number of `stages` under which we can use different images and execute different things in regard to the code in our repository. An example for a pipeline is the one we have pepared for you to play around with here:

```yaml
final gitlab-ci.yml

```

It consists of the three stages `run`, `test`, and `push`. In every one of those stages, we are going to do different things, chained together with the pipeline - which will execute one stage after the other. If one stage fails to complete, the pipeline will fail and we will be notified per E-Mail, so that we can investigate the errors and resolve them before pushing our code to a new version of our image or even towards a production cluster.

First, we will check whether our app can still be run successfully after our recent code changes in the `run` stage.

After it was run successfully, we want to test the functionality of our app. We will need to add the `test` stage for this. Remove the **#** comments for the `test` stage for it to be added to our pipeline.

With the `push` stage we will then, if all previous stages have been completed succesfully, build our app and push it to Docker Hub. For this to work, you need to remove the **#** comments from the `push` stage and add some variables into GitLab that our script can work with.
In your Project, go to `Settings` and open the `CI / CD ` menu. 

Add the following variables and fill them with the required information:

`CI_REGISTRY`: docker.io

`CI_REGISTRY_IMAGE`: index.docker.io/<your_docker_hub_user>/<your_image_name>

`CI_REGISTRY_USER`: <your_docker_hub_user>

`CI_REGISTRY_PASSWORD`: <your_docker_hub_password>

If every stage of the pipeline is excecuted successfully, your image will be pushed towards Docker Hub for a cluster to pull it from there.

<div align="right">
   
   [Prev](08_write-test.md) - Next
</div>