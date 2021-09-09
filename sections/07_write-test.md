# Hands-On: Writing unit and scenario tests

In this hands-on we'll be writing both a unittest and a scenario test. We'll use the `unittest` package for running both types of tests and we'll be using `requests` to make HTTP requests in the scenario test.

## Writing a unit test

As explained previously, the goal of a unit test is to test one unit of code. This can usually be a function or a class that represents one *unit* of functionality. The functionality we are going to test in our unit test is the `get_entry` function that you can find in the `utils.py` file. 

Let's have a look at what the functions code does:

```python
def get_entry(text, author):
    ret = {}

    # Check that text and author are not None
    if any(e is None for e in [text, author]):
        raise Exception(f"Property can't be none")
    ret['text'] = text
    ret['author'] = author
    ret['timestamp'] = time.time()

    return ret
```

As you can see, the function takes two arguments `text` and `author`. It then checks that
neither of them is `None`. The code throws an exception if either `text` or `author` is `None`.
We then create a new dictionary that contains the previously passed `author` and `text` as 
key-value pairs as well as the current UNIX timestamp from the `time` module. Finally, that 
dictionary is returned.

When writing a test we want to test success *and* failure scenarios. A skelleton test case
is already defined in `test/unit/test_entry.py`

```python
import unittest

from guestbook.utils import get_entry

class TestEntry(unittest.TestCase):
    pass
```

You can run this (currently empty) unit test by running the following command **in the main
directory** `CICD-Hands_On-Demo`

```bash
$ python3 -m unittest discover tests/unit 
```

The command will come back with the information that no tests were run and everything went ok.

Let's implement our first test case. A test case is a function within the `TestEntry` class.
As previously noted, test cases should test both *success* and *failure*. Let's start with 
*success* by implementing a simple test that checks that, when passing a *text* and *author*
to `get_entry()` the returned object won't be `None`. 

```python
import unittest

from guestbook.utils import get_entry

class TestEntry(unittest.TestCase):
    def test_succesful_init(self):
        e = get_entry("text", "author")
        self.assertIsNotNone(e)
```

Re-running our unittest as described above will now show one passing test. We use the
`self.assertIsNotNone()` function to verify that the returned value is not `None`.

Now it's your turn: Implement test cases based on the descriptions and function
skelletons:

Test Case #1: Verify that `None` values being passed as argument values for `text` or 
`author` result in an Exception being raised. 

```python
def test_none_arg_raises_exception(self):
   # Implement your test case here
```

You can check for a function raising an exception by using the [`assertRaises` function](https://docs.python.org/3/library/unittest.html#unittest.TestCase.assertRaises).
The function signature looks like this: `assertRaises(exception, callable, *args, **kwargs)`. 

Test Case #2: Verify that, in the returned dictionary, the three keys `text`, `author`, and 
`timestamp` are present.

```python
def test_keys_present(self):
   # Implement your test case here
```

You can check for a dictionary containing a key by using the [`assertIn` function](https://docs.python.org/3/library/unittest.html#unittest.TestCase.assertIn). The function signature looks 
like this: `assertIn(member, container)`. 

## Writing a scenario test

A scenario test does not test a single unit of code but rather it targets a whole (sub)system. It thus tests the *interactions* between different units of functionality. Scenario testing a service that is based on a REST API usually means sending correct and wrong requests to an endpoint and verifying that it behaves properly. Since we are testing the whole system we'll need a running instance. Luckily, you setup the software to run on your local kubernetes cluster in a previous section! We'll be running the tests against this local instance. In a full CI/CD pipeline we'd ususally deploy the code into a staging environment and run the tests against the system there. 

Unit tests can be written in many different formats. A simple python script that, using the `requests`
package makes a series of requests would work as well. To make our life easier though we'll 
be using `behave`. Behave (by using the `gherkin` language) allows us to describe scenarios
in a natural language while making it easy to translate the natural language instructions into 
executable code. 

Navigate your terminal to the `tests/scenario` directory. You'll find the setup for `behave` is 
already done. Make sure that you have a local instance of the application running. 

In the directory(`tests/scenario` **not** the main directory) you can run behave by typing:

```bash
$ behave
```
`behave` will inform you that it ran checks for 0 features, 0 scenarios and 0 steps. 

Open up the `posts.feature` file. A `.feature` file, as the name suggests, describes
one feature that you want to have. A `feature`, in this case the feature to create and 
read posts, can then have several scenarios. 

We'll start by defining the feature. 

```gherkin
Feature: Create and retrieve a new entry
```

With the name and description of our feature described we can get started with our 
scenario (mind the indention, scenarios are indented with one tap to group them under
the feature).

```gherkin
   Scenario: Add a new entry
```

Next, we need to define the steps that we want to take. We first use the `Given` keyword
to define our request URL. Mind the indention again!

```gherkin
      Given a request url http://127.0.0.1:8010/api/posts
```

Thinking about the request process we'd next define a json payload to send to the server. 
So let's use the `And` directive from `gherkin` to define our json payload. 

```gherkin
         And a request json payload
            """
            {
               "author": "integration test",
               "text": "Hello from our integration test"
            }
            """
```

If we were to do this request by hand, the next step would be to send the request and then
check the response code to be a `201 - CREATED`. In our integration test, we'll use the 
two `gherkin` keywords `When` and `Then`. 

```gherkin
         When the request sends POST
         Then the response status is OK
```

Run the scenario by running behave again. You can also open up a browser and navigate to 
http://127.0.0.1:8010/api/posts and see for yourself that the post has been added. 

### Extra - Write a second scenario to GET all posts

In the previous step we verified that the integration test had created an entry manually. 
We can of course also do that in another scenario test. Below example shows that you can 
verify not only single properties but also the schema of the returned JSON. 

```gherkin
    Scenario: Get all entries
        Given a request url http://127.0.0.1:8010/api/posts
        When the request sends GET
        Then the response status is OK
            And the response json matches
                """
                {
                    "title": "PostPage",
                    "type": "object",
                    "properties": {
                        "size": {"type": "number"},
                        "length": {"type": "number"},
                        "start": {"type": "number"},
                        "items": {"type": "array"}
                    },
                    "required": ["size", "length", "start", "items"]
                }
                """
            And the response json at $.start is equal to 0
```
<div align="right">
   
   [Prev](06_intro-to-testing.md) - [Next](08_pipeline.md)
</div>
