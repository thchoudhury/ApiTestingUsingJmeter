# API Testing Using Jmeter And Postman

## Overview
Here, APIs of [Octoperf](https://doc.octoperf.com/) websites has been tested [using Jmeter](https://github.com/thchoudhury/ApiTestingUsingJmeterAndPostman/tree/master/UsingJmeter) and [using Postman](https://github.com/thchoudhury/ApiTestingUsingJmeterAndPostman/tree/master/UsingPostman)

## Getting Started

* Open Terminal in your local system and redirect to Desktop
  > ```cd Desktop```

* Copy and Paste the below command
  > ```git clone <https://github.com/thchoudhury/ApiTestingUsingJmeterAndPostman.git>```

## Prerequisites
 ### Install Jmeter
 #### Dependencies
1. Install JAVA(8+)
2. Downalod [Jmeter 5.1.1](http://jmeter.apache.org/download_jmeter.cgi) in Desktop
3. Download [plugins-manager.jar](https://jmeter-plugins.org/get/) and put it into lib/ext directory, then restart JMeter.
4. Install below plugin: a)JSON/YAML Plugins (deprecated) The installer will also install several JMeter Plugins, which can be used directly or within a continuous integration server such as Jenkins

 ### Install Postman & Newman
1. Download [Postman](https://www.getpostman.com/apps)
2. Open Terminal and run the below command to install Newman
   > npm install -g newman
3. In terminal, run the below command to install Newman-html-reporter
   > npm i -g newman-reporter-html

## To Run Tests

#### Using Jmeter
1. Open Terminal and Go to Desktop and Copy-Paste the below command
   > cd apache-jmeter-5.1.1\apache-jmeter-5.1.1\bin
2. To run the test in Jmeter, run the below command in Terminal
   **UserName should be replaced before executing command**
   > jmeter -n -t C:\Users\<UserName>\Desktop\ApiTestingUsingJmeterAndPostman\UsingJmeter\tests\my_test.jmx -l C:\Users\<UserName>\Desktop\ApiTestingUsingJmeterAndPostman\UsingJmeter\results\my_test.jtl

#### Using Postman & Newman
1. Open Terminal and Go to Desktop and Copy-Paste the below command
   > cd ApiTestingUsingJmeterAndPostman\UsingPostman
2. To run test using Newman, run below command in Terminal
   > newman run tests\my_test.json


## List of Tested REST APIs

### Login API : For logging into the website with valid id and password
* HTTP Method: POST
* API:  https://api.octoperf.com/public/users/login
* Body (form-data): username(string) && password(string)
* Response Code: 200 
* Response Data: {'token': <Generated Token Value (string format)>}

Here, token is stored in variable **AuthToken** for further use.

### Get All Workspace Details : To get all the workspace details for the logged in user
* HTTP Method: GET
* API:  https://api.octoperf.com/workspaces/member-of
* Headers:
    * Content-Type: application/json;charset=UTF-8
    * Authorization: Bearer {{AuthToken}}
* Response Code: 200 
* Response Data: Return all the workspace details.

Here, random 'id' for workspace is stored in variable **workspaceId** for further use.

### Get All Project Details : To get all the proejct details under specified workspaceid for the logged in user
* HTTP Method: GET
* API:  https://api.octoperf.com/design/projects/by-workspace/{{workspaceId}}/DESIGN
* Headers:
    * Content-Type: application/json;charset=UTF-8
    * Authorization: Bearer {{AuthToken}}
* Response Code: 200 
* Response Data: Return all the project details under specified workspace id.

### To Create New Project : To create new project under specified workspaceid for the logged in user
* HTTP Method: POST
* API:  https://api.octoperf.com/design/projects?workspaceId={{workspaceId}}
* Headers:
    * Content-Type: application/json;charset=UTF-8
    * Authorization: Bearer {{AuthToken}}
* Body: 
    ```{
    "id": "",
    "created": "2019-07-22T07:50:12.755Z",
    "lastModified": "2019-07-22T07:50:12.755Z",
    "userId": "pEGWCGwBjlTPLZEzy_-G",
    "workspaceId": "{{workspaceId}}",
    "name": "{{projectName}}",
    "description": "{{description}}",
    "type": "DESIGN"
   ```
* Response Code: 200 
* Response Data: A project will be created under specified workspace id. A unique id is also generated for the project. 

Here, the unique 'id' for new project is stored in variable **createdProjectID** for further use.

### Edit Created Project Name : To edit any project name under specified workspaceid for the logged in user
* HTTP Method: PUT
* API: https://api.octoperf.com/design/projects/{{createdProjectID}}?workspaceId={{workspaceId}}
* Headers:
    * Content-Type: application/json;charset=UTF-8
    * Authorization: Bearer {{AuthToken}}
* Body: 
    ```{
    "created": 1563781812755,
    "description": "Project is running under test",
    "id": "a1jlGGwB5tgkpL6TQv30",
    "lastModified": 1563785773812,
    "name": "{{projectName}}",
    "type": "DESIGN",
    "userId": "pEGWCGwBjlTPLZEzy_-G",
    "workspaceId": "q0eWCGwB6ANMBjnly4Xn"
   ```
* Response Code: 200 
* Response Data: Project name will be created for specified project id. 

### To Delete Existing Project: To delete any existing project
* HTTP Method: DELETE
* API:  https://api.octoperf.com/design/projects/{{createdProjectID}}?workspaceId={{workspaceId}}
* Headers:
    * Content-Type: application/json;charset=UTF-8
    * Authorization: Bearer {{AuthToken}}
* Response Code: 204
* Response Data: None


## To Generate Test Report

 #### Using Jmeter
 
 1. Open Terminal and Go to Desktop and Copy-Paste the below command
    > cd apache-jmeter-5.1.1\apache-jmeter-5.1.1\bin
2. To run the test and generate report using Jmeter, run the below command in Terminal
   **UserName should be replaced before executing command**
   > jmeter -g C:\Users\<UserName>\Desktop\ApiTestingUsingJmeterAndPostman\UsingJmeter\results\my_test.jtl -o C:\Users\<UserName>\Desktop\ApiTestingUsingJmeterAndPostman\UsingJmeter\reports\my_test_report
3. Generated HTML Report can be found in 
   C:\Users\<UserName>\Desktop\ApiTestingUsingJmeterAndPostman\UsingJmeter\reports\my_test_report\index.html
Test result is generated in html format.

#### Using Postman and Newman

1. Open Terminal and Go to Desktop and Copy-Paste the below command
   > cd ApiTestingUsingJmeterAndPostman\UsingPostman
2. To run test and generate test report using Newman, run below command in Terminal
   > newman run tests/my_test.json -r html --reporter-html-export reports/test_result.html
3. All test results are found under reports/test_result.html
