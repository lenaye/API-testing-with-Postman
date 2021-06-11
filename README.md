# cyberSmartChallenge

# Introduction


A repository containing both manual and automated tests for a technical challenge excercise for CyberSmart.

The Petstore Swagger was used for this exercise, located at: https://petstore.swagger.io

# Manual test cases
The Excel spreadsheet contains manual tests for the Petstore API. The list of test cases are:-
* Find all available pets
* Find all sold pets
* Add a new pet
* Find pet by Id
* Find pet not found
* Add a new user
* Add user without username
* Find user by username
* Find user-invalid username

Each test can be manually executed by following the step-by-step description and expected results described in the spreadsheet.

# Automated test cases

There are created using Postman API tool, available from: https://www.postman.com/downloads/

## Installation and Set Up
1. Download and install the app to your local machine.
2. Once installed, start up Postman and import the test cases file CyberSmart.postman_collection.json, using File-Import menu option.
3. Likewise, import the environment file CyberSmart.postman_environment.json, using the File-Import menu.
4. The test case collection CyberSmart will appear under the Collections group, and the environment settings CyberSmart will apppear under the Environments group.

## Descriptions of the Postman test case Collection

The Postman collection consists of 2 groups of tests: Pets and Users. Each group in turn is divided into the following test cases:

* Pets
  * FindbyStatus
  * Add new pet
  * Find pet by Id
* Users
  * Add new user
  * Get user


## Running the tests (from Postman)
To run the tests, simply select ... next to the collection name CyberSmart and choose Run collection.

A Runner tab will be displayed along with the list of tests in the collection all preselected for execution. Optionally, each test can be de-selected or selected at this state prior to execution.

Then simply hit the button Run CyberSmart to start the test execution.


