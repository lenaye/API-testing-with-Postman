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
1. Clone the repo: `https://github.com/lenaye/cyberSmartChallenge`
2. Download and install the Postman app to your local machine.
3. Once installed, start up Postman and import the test cases file CyberSmart.postman_collection.json, using File-Import menu option.
4. Likewise, import the environment file CyberSmart.postman_environment.json, using the File-Import menu.
5. The test case collection CyberSmart will appear under the Collections group, and the environment settings CyberSmart will apppear under the Environments group.

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

## Notes & Observations
1. The data appears to be unstable and changing quite frequently. This makes running repeated automated tests difficult as they keep on failing.

2. There appeared to be duplicate record IDs with different data in the system, i.e. querying using one Id returned different pet info at different times , so when calling a GET request for a particular pet with an Id, the expected result is not always guaranteed to be returned.

3. In the case of status field, when calling the request for a Store inventory, there appear to be many more statuses of pets than what's listed in the Swagger UI.  According to the model, the only acceptable status values are `[ available, pending, sold ]`
   And yet, I managed to add new pets using POST /pet endpoint using a status of 'happy' and 'missing' and were both accepted. This indicates that there's no validation of this status on the back-end.

4. Likewise, when I submti a request for GET /pet/{petId} where the {petId} is a long numeric number, i.e. > 200 digits the API throws an error "java.lang.NumberFormatException:". This kind of error should be handled properly by the API.

5. The Swagger UI showed different response codes for each endpoint, i.e. 200, 400, and 404, but I was unable to get a 400 response in most cases when I supplied an invalid Id in the request. In such cases only 404 (Pet not found or User not found) is returned.

6. There appear to be no validation on checking the mandatory parameters in POST /pet endpoint when adding a new pet. According to the model, the name and photoUrls are mandatory fields (indicated by red asterisks), i.e.
   `Pet{
       id	integer($int64)
       category	Category{
                   id	integer($int64)
                   name	string
                   }   
       name*	    string
                   example: doggie
       photoUrls*	[
                   xml: OrderedMap { "wrapped": true }
                   string
                   xml: OrderedMap { "name": "photoUrl" }
                   xml:
                       name: photoUrl]
       tags	    [
                   xml: OrderedMap { "wrapped": true }
                   Tag {
                       id	integer($int64)
                       name	string
                   }]
       status	    string
                   pet status in the store
                   Enum:
                   [ available, pending, sold ]
   }`

   However, I was able to add a new pet without name and photoUrls fields .

   



