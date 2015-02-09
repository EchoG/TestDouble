## About This Assignment

This assignment allows you to learn about and use different kinds of test doubles. 
It uses a refactored version of the social network application in which member accounts are persisted using a Data Access Object (DAO) that communicates with an external data store. However the DAO  does not yet exist - it's only stubbed out to allow the application to compile. 

Several unit tests exercise the social network API to verify its functionality, however most tests don't work since the `SocialNetwork` is coupled to the the real DAO whose implementation is still missing. Besides, using the real DAO in the tests would not be desirable even if the full DAO implementation were available (why is this?). Your job is to break the coupling between the real implementation class `AccountDAO` (with yet missing code) and the class `SocialNetwork` to allow the tests to take advantage of test doubles and then create the test doubles. You will exercise different strategies and compare them. Your test doubles should implement the IAccountDAO interface. 

A singleton factory class `DAOFactory` is provided instantiate different kinds of test doubles. Review this class. 

Prep:

1. Download the repo using the [Download ZIP] link. Don't use the [Clone in Desktop] link. Don't try to push your changes back to this repository.  

2. Import the repo into your Eclipse workspace (or other IDE if you're using another IDE).  

3. Add Mockito jar file to your project (so that the code will compile).   
External jar file to add to your project and classpath: mockito-all-2.0.2-beta.jar  
Mockito downloads: https://bintray.com/szczepiq/maven/mockito/2.0.2-beta/view/files/org/mockito/mockito-all/2.0.2-beta  

4. I suggest you use __git__ to manage versions of this assignment. You may commit your code to a private repo at github organization `cmusv-svvt`. Send the TA your github account name to join this organization. 

5. Complete the following tasks.  

## Tasks

T1. Break the dependency between `SocialNetwork` and `AccountDAO` by using dependency injection.

T2. Implement a _fake_ `AccountDAOFake` to stand in for the real DAO. Make the provided tests (except for spy tests at the end) work with your fake. Fix and record any faults found in the test or production code with this approach. The stub for the fake is provided. Let the spy tests fail for now when using the fake as a test double. 

STOP: Create a new git branch for tasks 3 and 4. 

T3. Try a different approach: _mock_ objects. Use the Mockito framework to create a mock version of the `AccountDAO` that will work with the tests provided. Make the provided tests pass, this time substituting the fake with the Mockito mock. Fix and record any faults found in the test or production code with this approach. Let the spy tests continue to fail for now when you use the mock as a test double.  
Mockito documentation: http://mockito.github.io/mockito/docs/current/org/mockito/Mockito.html  
See also lecture slides for a quick Mockito reference.

T4. Now use your fake object to create a test _spy_ using Mockito's spy interface. The sneaky spy test stubs towards the end of the provided test case should make sure that `IAccountDAO`'s persistence operations are called properly to save any required changes of local `Account` objects in the underlying data store. Complete these tests. That way you'll know at least that the right data operations are invoked at the right times and places and with the right parameters, if even you can't definitively check the results of those invocations without a real data store. When the full implementation of `AccountDAO` is available, that implementation can also be substituted to create the Mockito spy. Fix and record any faults found in the code with this approach. 

T5. Substitute your fake object back for the Mockito mock object. You can do this by switching back to the git branch you used during T2.  

T6. Fill out the assignment report inside the `extras` folder. Submit a copy of your assignment report to Blackboard (no formatting necessary). 

T7. Upload your project jar file to WEB-CAT. Tests that rely on Mockito will compile, but they will fail on WEB-CAT due to the server's Java security policy settings that block certain reflection operations that Mockita relies on.  

WEB-CAT instructions are here:

https://github.com/cmusv-svvt/UT-and-TDD#how-to-submit-your-solution-to-web-cat

GOOD LUCK!




