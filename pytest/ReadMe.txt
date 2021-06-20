Hello

There are two Pytest scripts in this folder: 
	- test_pet_endpoint.py 
	- test_user_endpoint.py.
	
I made use of pytest, requests and unittest libraries for this exercise.
For test_pet_endpoint.py, I only used pytest and request libraries and used Python's native assertion methods for verification of reponses.
For test_user_endpoint.py, I used unittest library and used assertion methods provided by unittest.

General notes:
There are a few fundamental features that are missing in this petstore API that prevented me from writing proper tests. For example:-
a) There is no authentication requirements so tests to ensure only the authenticated users can access the service and likewise tests for rejection of invalid authentications could not be created.
b) There is no documentation indicating the valid range of values for parameters in the requests, so again, tests to ensure acceptance of valid values (and edge-cases, boundary conditions and equivalence partitioning) and rejection of invalid input values could not be created.
c) There is no documentation as to which are mandatory and and which are optional input parameters in the requests, so tests to ensure correct error messages returned in cases where mandatory parameters are missing could not be created. Similarly, I have no knowledge of what default values are taken for optional parameters, so tests could not be created to check for those either. 
