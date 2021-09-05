# Hands-On: Building a pipeline

In this section we will:

- Configure the pipeline to react on code push
- Configure the pipeline to run tests
- Configure the pipeline to deploy if tests are succesful

In our GitLab repository, we will add a `.gitlab-ci.yml` this file is automatically recognized by GitLab and it is our recipie for our pipeline. With every commit that we push towards this repository, the pipeline will run and excecute all steps it contains. Such pipelines can also be scheduled to run at a certain time.
We have created a YAML file for you that will be used to excecute the pipeline by GitLab.

To run tests for us we will need to add the `test` stage to the file. Comment out?

With the `deploy` stage we will then, if all previous stages have been completed succesfully, go ahead and deploy our app to the Kubernetes cluster.

<div align="right">
   
   [Prev](08_write-test.md) - Next
</div>