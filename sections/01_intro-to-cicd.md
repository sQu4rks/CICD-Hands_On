# Introduction to CI/CD
CI/CD, shorthand for **Continous Integration/Continous Delivery**, is a practice used in software engineering to deploy a software. Before CI/CD most software was developed and then released in long cycles. A software engineer would develop a feature, throw it over a wall for QA to check that it meets all quality criteria and then, months or sometimes *years* later, the feature would be pushed to the public. This is not the case anymore. Companies like amazon push new code to their systems (production and testing) more then once a second and even seemingly stall pages like google update multiple times every time. 

**Continuous Integration** or CI is the process of continuously integrating new changes/components of the source code into the application. Instead of having one big “push day” where changes are merged we continuously add changes as they are made available by the development team.

Continuous Integration Pipelines usually start with a Source Code Management (SCM) change. New code has been pushed by a developer. What happens next depends on the organization but some common steps are

  1. Clone the code
  2. Compile the code (if needed)
  3. Test the code - This can include running unit, integration and static tests as well as testing for code coverage(what percentage of source code is actually tested by test cases) or memory leak tests.
  4. Report - Either via a dashboard, e-mail, chat or other means of communication
  5. (Deploy) - Code could be automatically deployed into production or staging environments - this last part then makes it a **Continous Delivery** (CD) process.

In this workshop we are going to have a look at such a CI/CD pipeline from the ground up. But in order to continously deliver code we first need *code*.

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
