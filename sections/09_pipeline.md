# Hands-On: Building a pipeline

In this section we will:

- Configure the pipeline to react on code push
- Configure the pipeline to run tests
- Configure the pipeline to deploy if tests are succesful

In our GitLab repository, we will add a `.gitlab-ci.yml` this file is automatically recognized by GitLab and it is our recipie for our pipeline. With every commit that we push towards this repository, the pipeline will run and excecute all steps that we specify in the file. Such pipelines can also be scheduled to run at a certain time, like once every day.
We have created a YAML file for you that will be used to excecute the pipeline by GitLab. Some parts of our instruction file are commented out, so they will be ignored until we add the necessary steps.

```yaml
final gitlab-ci.yml

```
To run tests for us we will need to add the `test` stage for example.

With the `push` stage we will then, if all previous stages have been completed succesfully, build our app and push it to Docker Hub.

<div align="right">
   
   [Prev](08_write-test.md) - Next
</div>