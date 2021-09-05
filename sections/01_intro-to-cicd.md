# Introduction to CI/CD

CI/CD is short for continuous integration/continuous deployment. CI and CD are related but have different definitions so let’s take a look at each separately.

Continuous integration is a development practice that involves developers on a team checking-in (integrating) their work frequently (usually multiple times a day). Once the work is checked-in, an automated build and testing process kicks off to see if it conflicts with existing code (these conflicts are called integration errors).

The CI process allows teams to quickly detect and correct integration problems and keep everyone’s development code relatively up to date while they are working. Without CI and frequent check-ins, builds, and tests, code different developers are working on could get so out of sync, that productivity and code quality is negatively impacted. Why? Because with fewer check-ins and tests, a developer may work on code for days before they attempt to merge it with the main branch. If they do and there are conflicts, they now have to work through days – as opposed to hours – of their own and their teammates’ code to resolve integration issues.

Continuous delivery a.k.a. CD is the next logical step after CI. After the build tests pass in CI, the code is deployed to a staging environment of some sort. At this point, additional automated tests and integration tests are run. If all tests pass, the code is “production-ready” but the code is not automatically deployed to the production environment. Generally, there is manual testing or approval before deployment to production.

This CD process helps speed up deployment times and catch bugs faster thanks to automated testing.

In addition to continuous delivery, there is another “CD” related to CI/CD: continuous deployment. This CD goes even further than continuous delivery. With continuous deployment, if all tests pass, the code is automatically deployed to production.

The benefit of continuous deployment is simple: production users get the most up-to-date code that was able to pass all required tests.

[Reference](https://jfrog.com/knowledge-base/an-introduction-to-devops-and-ci-cd/)

<div align="right">
   
   [Prev](00_pre-req.md) - [Next](02_intro-to-code.md)
</div>