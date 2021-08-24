# Introduction to testing

Testing software has become a crucial aspect in every development process. While software testing used to be carried out by a Quality Assurance department after the development was finished most modern software is tested while being developed.

We can thus define testing as follows:

> In software development testing is the process of verifying that a application meets a certain standard or functionality and quality. In testing we differentiate the types of visibility into the inner workings of the software with white-box, black-box and hybrid testing as well as the level of testing with unit testing, integration testing (sometimes also called scenario testing) and system testing.

In *white-box* testing the test developer has full visibility in the source code of the software. Often the person writing the test is the developer herself.

In *black-box* testing the test developer has no visibility into the software and treats the component under test as a black box where inputs can be changed and outputs can be observed.

Finally, *grey-box* testing is a hybrid approach. Here the tester has (at least partial) visibility into data structures and algorithms but tests the software from a user perspective. A typicall example of grey-box testing is penetration testing of software where information about internal structures or boundary values have been discovered by reverse engineering the binary but the exploit/test is run from a user perspective.

With the visibility settled we differentiate the level of components being tested. To reiterate the terminology again, a software (or system) is usually made of components that in turn are made of units. A unit can be defined as the smallest testable piece of code. This is usually a function or a class.

## Unit testing

A unit test tests a unit of code and is usually written by the developer in a white-box approach. Unit tests (aim to) verify that a unit of code works in isolation. A unit test for a function that validates if a string is a valid email address or not might check that the function returns the correct results for valid and invalid email strings. Unit testing is often linked with metrics like code coverage. Code coverage checks what percentage of the source code is being covered by unit tests cases.

Let’s look at an example how a unit test in python might look like. For this example we are going to use the following simple multiplication function as our test object:

```python
def mult(a, b):
    return a * b
```

For this we will define two test cases. One test case will check if the multiplication of two numbers returns the (correct) positive number and one that checks that the multiplication of a positive and a negative number return the (correct) negative number.

```python
import unittest

def mult(a, b):
    return a * b

class TestMult(unittest.TestCase):
    def test_positive_number_multiplication(self):
        self.assertEqual(mult(2, 2), 4, "2 x 2 should be 4")

    def test_positive_negative_number_multiplication(self):
        self.assertEqual(mult(2, -2), -4, "2 x (-2) should be -4")

if __name__ == "__main__":
    unittest.main()
```

Lets go through this example step by step.

In line 6 we define our test case class. Each test case class can have multiple test cases (the functions in line 7 and line 10).

The test assumptions itself are done in line 8 and line 11. Here we are checking (or asserting) equality of the return of our function and our desired outcome.

Line 13 and 14 then tell our python interpreter to run the all test cases defined when being executed from the command line.

Besides the equality assertion we can also test for. The function names are pretty much self-explanatory.


* assertNotEqual(a, b)
* assertTrue(x)
* assertFalse(x)
* assertIs(a, b)
* assertIsNot(a, b)
* assertIsNone(x)
* assertIsNotNone(x)
* assertIn(a, b)
* assertNotIn(a, b)
* assertIsInstance(a, b)
* assertIsNotInstance(a, b)
* assertRaises(e, func, args, *kwds)
* assertAlmostEqual(a, b) Checks that a-b is 0 up to the 7 digit after the comma
* assertNotAlmostEqual(a, b)
* assertGreater(a, b)
* assertGreaterEqual(a, b)
* assertLess(a, b)
* assertLessEqual(a, b)
* assertItemsEqual(a, b) Sorts the two lists a and b and checks that they are equal


## Integration testing

A integration test (sometimes also referred to as a scenario test) tests the interaction between modules. It tests that modules work as expected when integrated together. An example would be a login component correctly working together with a database to authenticate a user. Usually progressivly larger groups of componets get tested until the software can be seen as a system.

A typical example for a scenario test would be running a set of request (with a known outcome) against a REST API. Check the source code repository for this documentation (the one you cloned during the previous lab) to see an example of a integration test running against a very simple REST API.

## System testing

A system test verifies that a scenario a user caries out on the fully integrated application runs as expected. This is also called End-to-End testing. An example would be to test that, on a forum webpage, a user can register, login, open the page of a topic, leave a comment and log out. This scenario involves a variety of components as well as the user interface.

User-acceptance Testing (UAT) can be seen as system testing.

<div align="right">
   
   [Prev](06_automate-k8s.md) - [Next](08_write-test.md)
</div>