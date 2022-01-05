# PreetiSharma


**Test Plan**

Test Plan should include the following :

Functional Testing

Stress/Load Testing/Performance Testing

Security Testing

Automation Testing

OS platform compatibility testing with Windows and Mac\linux.


**Test Scope/Coverage Choice**

Test cases should cover positive functional & negative functional flow and Error testing.
I prefer positive,negative abd error testing flow to make sure that system is able to handle all scenarios and does not crash.
Also it will be good from coverage perspective to run following all scenarios on Windows and Mac\linux to make sure that the application is compatible and no issues are seen. Howver for my testing deliverable submission I have only tested it on Windows.

**Pre conditions for all the following test cases**

1 Environment should be set up for hash application.

2 Port environment variable 8088 should be set.

**Positive/Negative Functional Testing & Error Scenarios**

1) **TC-1** 

Steps

Launch the application and verify that the application should wait for http connections.

Launch the application and it should answer in the port environment variable.

**Execution Status-Passed**

2) **TC-2**

Steps

Post to /hash with a password.

Verify it should return a job identifier immediately.

Verify system should wait for 5 seconds and hashing algorithm SHA512 should compute password hash.

**Execution Status Failed-It is not returning job identifier immediately but it is taking appx. 5 seconds.**

3) **TC-3**

Steps

Run Get to /hash and use the identifier returned in test case 3.

Verify it should return base64 encoded password hash for the corresponding POST request.

Verify that the base64 encoded password is matching to the password entered by user in test case 3.

**Execution Status-Passed**

4) **TC-4**

Steps

Post 2 requests to /hash with correct password.

Post 2 requests to /hash with malformed data.

Run Get to /stats with data.

Verify that it shoud not accept any data.

Run Get to /stats without data.

Verify it should return a JSON data structure.

Verify it should show count of Total hash requests since the server started and average time of a hash request is in milliseconds.

**Execution Status-Failed- I think the time dispplayed for average time in milliseconds is not calculated right.**

Also The hash app window does not show the successful requests but only the malformed input count.Not sure if this is expected?
   

5) **TC-5**

Steps

Post to /hash with password from 3 connections on command windows.

Verify the job identifier should be generated for both and both the requests should be counted in total no. of requests in stats command.

Run Get to /hash for these 3 identifiers.

Verify Get to should return 3 base64 encoded password hash for the corresponding 3 POST request.

**Execution Status-Passed**

6) **TC-6** 

Steps

Post to /hash with a password in one window. 

In another window simultaneously run shutdown /hash.

Verify the server should return 200 and shutdown hash application.

Verify the password hashing should be completed in first window even if window is shutdown.

**Execution Status-Failed- Shutdown request does not return 200**

7) **TC-7**

Steps

Run shutdown /hash 

Verify the server should return 200 and shutdown hash.

Post to /hash with a password.

It should reject the new request and throw an error.

**Execution Status-Passed-it shows connection refused error for rejection**

8) **TC-8**

Steps

Run shutdown /hash in one widnow. 

Post to /hash with a new password in another window.

Verify when shutdown is pending no new request should be allowed.

**Execution Status-Unexecuted-Shutdown is so quick so I could not verify this scenario.**

9) **TC-9**

Steps

Post to /hash twice and use same password for both command.

Verify that job identifier is different for both requests.

Run Get to /hash using the job identifiers from above step.

Verify that the base64 encoded password hash value is same for both and matches to the Post to /hash request password.

**Execution Status-Passed**

10)  **TC-10**

Steps

Post to /hash with blank password value.

Verify system should throw an error to enter password or some other error message.

**Execution Status-Failed-It accepted blank password and did not show any message**

11) **TC-11**

Steps

Get to /hash with any random job identifier like 0 or -1

Verify system should return an error that the job identifier does not exist.

**Execution Status-Passed**

12) **TC-12**

Steps

Do not set port 8088 environment variable.

Post to /hash with password.

Verify the application should crash.

**Execution Status-Passed as application did not start**

13) **TC-13**

Stpes

Change Port environment variable to 8089 or 1.

Post to /hash with password.

Verify an error is displayed.

Now Shutdown the application.

**Execution Status-Faiied-I can connect to the application with different port 8089 or 1 but could not post anything with correct error message.
However I was able to shutdown the hash application on port 8089 or 1 using same command which I used for port 8088.**


**Defects**

Defects

**1st Defect**

Steps

Post to /hash with a password.

**Expected Result**

Verify it should return a job identifier immediately.

**Actual Result**

Job identifier takes 5 seconds to return but it should return immediately.

**2nd Defect**

Steps

Post to /hash with a password.
Run Get to /hash and use the identifier returned in above step.
Run Get to /stats with data.

**Expected Result**

Verify average time of a hash request is in milliseconds.

**Actaul Result**

I think the time dispplayed for average time in milliseconds is not calculated right.

**3rd Defect**

Steps

Post 2 requests to /hash with correct password.
Post 2 requests to /hash with malformed data.
Run Get to /stats with data.

**Expected Result**

Verify it should show count of Total hash requests since the server started 

**Actual Result**

The hash app window does not show the successful requests but only the malformed input count.
Not sure if this is expected?

**4th Defect**

Steps

Connect to hash application.
Run shutdown /hash.

**Expected Result**

Verify the server should return 200 and shutdown hash application.

**Actual Result**

The server did not return 200.

**5th Defect**

Steps

Post to /hash with blank password value like this curl -X POST -H "application/json" -d "{\"password\":\"\"}" http://127.0.0.1:8088/hash

**Expected Result**

Verify system should throw an error to enter password or some other error message.

**Actual Result**

Job identifier is returned for blank password and it generated base64 value but it should not.

**6th Defect**

Steps

Change Port environment variable value to 8089 or 1 application is connected.
Now Shutdown the application.

**Expected Result**

I should not be able to connect and shut down hash application if I am not on right port isn't it ?

**Actual Result**

I can connect to the hash application with different port 8089 or 1 and was able to shut it down on port 8089 or 1 using same command which I used for port 8088.**

**Few Observations**

When I connect to the hash window it does not show any message that windows is connected to the hash application should it ?
Should there be a shutdown time like 5-6 seconds or less to test shutdown scenarios ?

**Automation Testing**

Automation testing can be planned for following scenarios :

1 Verify software is able to process multiple connections simultaneously.

2 Verify shutdown scenarios for inflight hashing,reject any new request and no additional password request is allowed when shutdown is pending.

3 Send multiple post requests at same time for multiple connections to check stress/load/performance testing.

4 Run automation scripts for windows and Ma\Linux and make sure both connections work fine togerther and hash application is able to handle all requests.And Total Stats should count server requests from both the platforms.
