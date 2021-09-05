# Hands-On: Writing unit and scenario tests

In this hands-on we'll be writing both a unittest and a scenario test. We'll use the `unittest` package for running both types of tests and we'll be using `requests` to make HTTP requests in the scenario test.

## Writing a unit test

As explained previously, the goal of a unit test is to test one unit of code. This can usually be a function or a class that represents one *unit* of functionality. The functionality we are going to test in our unit test is the `get_entry_dict_from_input` that you can find in the `utils.py` file. 

## Writing a scenario test

A scenario test does not test a single unit of code but rather it targets a whole (sub)system. It thus tests the *interactions* between different units of functionality. Scenario testing a service that is based on a REST API usually means sending correct and wrong requests to an endpoint and verifying that it behaves properly. Since we are testing the whole system we'll need a running instance. Luckily, you setup the software to run on your local kubernetes cluster in a previous section! We'll be running the tests against this local instance. In a full CI/CD pipeline we'd ususally deploy the code into a staging environment and run the tests against the system there. 


<div align="right">
   
   [Prev](07_intro-to-testing.md) - [Next](09_pipeline.md)
</div>
