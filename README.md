# PreetiSharma


**Test Plan Strategy**

For hash application the Test Plan can include the following type of testing:

A) Functional/Negative/Error Testing

B) Stress/Load Testing/Performance Testing

C) Security Testing

D) Automation Testing

E) OS platform compatibility testing with Windows and Mac\linux.

However for my deliverable submission I will be doing only A)Manual testing and will cover some points on D)automation testing :

**Test Scope/Coverage Choices**

Test cases should cover positive & negative functional flows and error testing.
I have chosen positive,negative and error testing flows to make sure that software is able to handle all functional and edgecase scenarios.
Stress/Load/Performance/Security testing will help to make sure that software is scalable and secure for clients.
Also it will be good to run following all scenarios on both Windows and Mac\linux to make sure that the application is compatible and no issues are seen. 
And for my testing deliverable submission I have only tested it on Windows.
Automation testing will help to run regression suites to make sure software still works as expected even if any defect is fixed or enhancement is implemented and also when we need to run same test cases on multiple connections.

**Positive/Negative Functional & Error testing test cases,execution results and defect report can be found here**

https://docs.google.com/spreadsheets/d/1ZftcZHGmJe8wQp5eh1Ys8qFZl1of7iMtgNNwt7WpmNk/edit#gid=0


**Few more Observations**

1) When I connect to the hash software window it does not show any message that windows is connected to the hash application should it ?

2) Should there be a shutdown time like 5-6 seconds or less to test shutdown scenarios ?



**Automation Testing **

Automation testing can be planned for following scenarios :

1 Verify software is able to process multiple connections simultaneously.

2 Verify shutdown scenarios for inflight hashing,reject any new request and no additional password request is allowed when shutdown is pending.

3 Send multiple post requests at same time using multiple connections for stress/load/performance testing.

4 Run automation scripts for windows and Mac\Linux and make sure both connections work fine togerther and hash application is able to handle all requests.
  And Total Stats should count server requests from both the platforms.
  
  
 Thank you
 
  
