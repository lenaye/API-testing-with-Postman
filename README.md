# API Testing with Postman

# Introduction

This repository contains automated tests for free and open Petstore API https://petstore.swagger.io/v2/ using Postman.

The info on the endpoints as well as input/output parameters and schema for the Petstore API can be found here: https://petstore.swagger.io

The Postman API tool is available from: https://www.postman.com/downloads/

## Installation and Set Up
1. Clone the repo.
2. Download and install the Postman app to your local machine.
3. Once installed, start up Postman and import the test cases file ```PetStoreAPI.postman_collection.json```, using File-Import menu option.
4. Likewise, import the environment file ```PetStoreAPI.postman_environment.json```, using the File-Import menu.
5. The test case collection ```PetstoreAPI``` will appear under the Collections group, and likewise the environment settings ```PetstoreAPIEnv``` will apppear under the Environments group.

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

Ideally, in a Continuous Integration environment, Postman tests should be run with a command-line tool such as newman (available from https://www.npmjs.com/package/newman) and execute as part of the built process. The above example tests can then be executed with the following command:
`newman run CyberSmart.postman_collection.json -e CyberSmart.postman_environment.json`

## A few issues with the API
Since this is an open and publi API without authentication, the data that it returns is not always of the best quality. A few points to note:

1. The data appears to be unstable and changing quite frequently. This makes run reliable and repeatable automated tests difficult as they tend to fail now and then.

2. There appeared to be duplicate record IDs with different data in the system, i.e. querying using one Id returned different pet info at different times , so when calling a GET request for a particular pet with an Id, the expected result is not always guaranteed to be returned.

3. In the case of status field, when calling the request for a Store inventory, there appear to be many more statuses of pets than what's listed in the Swagger UI.  According to the model, the only acceptable status values are `[ available, pending, sold ]`
It is possible to add new pets using POST /pet endpoint using a status of 'happy' and 'missing' and were both accepted. This indicates that there's no validation of this status on the back-end.

4. Likewise, when you submti a request for GET /pet/{petId} where the {petId} is a long numeric number, i.e. > 200 digits the API throws an error "java.lang.NumberFormatException:". This kind of error should be handled properly by the API.

5. The Swagger UI showed different response codes for each endpoint, i.e. 200, 400, and 404, but it will return a 400 response in most cases when you supply an invalid Id in the request. In such cases only 404 (Pet not found or User not found) is returned.




