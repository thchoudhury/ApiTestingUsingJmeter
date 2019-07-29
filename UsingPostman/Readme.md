# API Testing Using Postman

## Overview

Here, APIs of Octoperf websites has been tested using Postman and Newman(if CLI is used). 

## Getting Started

* Open Terminal in your local system and redirect to Desktop
   ```
   cd Desktop
   ```
* Copy and Paste the below command

   ```
   git clone <https://github.com/thchoudhury/ApiTestingUsingJmeterAndPostman.git>
   ```
  
* Open Terminal and Go to Desktop and Copy-Paste the below command

    ```
    cd ApiTestingUsingJmeterAndPostman\UsingPostman 
   ```

## Prerequisites

 ### Install Postman & Newman
1. Download [Postman](https://www.getpostman.com/apps)

2. Open Terminal and run the below command to install Newman

   ```
   npm install -g newman
   ```
   
3. In terminal, run the below command to install Newman-html-reporter

     ```
     npm i -g newman-reporter-html
    ```

## To Run Tests

1. To run test using Newman, run below command in Terminal

    ```
    newman run tests\my_test.json
    ```

## List of Tested REST APIs

#### Login API : For logging into the website with valid id and password
* HTTP Method: POST
* API:  https://api.octoperf.com/public/users/login
* Body (form-data): username(string) && password(string)
* Expected Response Code: 200 
* Expected Response Data: {'token': <Generated Token Value (string format)>}

Here, token is stored in variable **AuthToken** for further use.

#### Get All Workspace Details : To get all the workspace details for the logged in user
* HTTP Method: GET
* API:  https://api.octoperf.com/workspaces/member-of
* Headers:
    * Content-Type: application/json;charset=UTF-8
    * Authorization: Bearer {{AuthToken}}
* Expected Response Code: 200 
* Expected Response Data: Return all the workspace details in json format shown as below.
```
  [
    {
        "created": 1563534310522,
        "description": "Workspace Description",
        "id":"workspaceId",
        "lastModified": 1563534310522,
        "name": "WorkspaceName",
        "userId": "pEGWCGwBjlTPLZEzy_-G"
    }
   ]
   ```

Here, random 'id' for workspace is stored in variable **workspaceId** for further use.

#### Get All Project Details : To get all the proejct details under specified workspaceid for the logged in user
* HTTP Method: GET
* API:  https://api.octoperf.com/design/projects/by-workspace/{{workspaceId}}/DESIGN
* Headers:
    * Content-Type: application/json;charset=UTF-8
    * Authorization: Bearer {{AuthToken}}
* Expected Response Code: 200 
* Expected Response Data: Return all the project details under specified workspace id in json format provided below.
```
  {
        "created": 1563534310522,
        "description": "Workspace Description",
        "id": "OWA7I2wB6ANMBjnljPXv",
        "lastModified": 1563534310522,
        "name": "Workspace Name",
        "type" : "Design",
        "userId": "pEGWCGwBjlTPLZEzy_-G",
        "workspaceId" : "workspaceId"
    }
```

#### To Create New Project : To create new project under specified workspaceid for the logged in user
* HTTP Method: POST
* API:  https://api.octoperf.com/design/projects?workspaceId={{workspaceId}}
* Headers:
    * Content-Type: application/json;charset=UTF-8
    * Authorization: Bearer {{AuthToken}}
* Body: 
    ```
    {
    "id": "",
    "created": "2019-07-22T07:50:12.755Z",
    "lastModified": "2019-07-22T07:50:12.755Z",
    "userId": "pEGWCGwBjlTPLZEzy_-G",
    "workspaceId": "{{workspaceId}}",
    "name": "{{projectName}}",
    "description": "{{description}}",
    "type": "DESIGN"
    }
   ```
* Expected Response Code: 200 
* Expected Response Data: A project will be created under specified workspace id in json format provided below. A unique id is also generated for the project. 

   ```
     {
        "created": 1563534310522,
        "description": "Workspace Description",
        "id": "OWA7I2wB6ANMBjnljPXv",
        "lastModified": 1563534310522,
        "name": "Workspace Name",
        "type" : "Design",
        "userId": "pEGWCGwBjlTPLZEzy_-G",
        "workspaceId" : "workspaceId"
     }
   ```

Here, the unique 'id' for new project is stored in variable **createdProjectID** for further use.

#### To Edit Created Project Name : To edit any project name under specified workspaceid for the logged in user
* HTTP Method: PUT
* API: https://api.octoperf.com/design/projects/{{createdProjectID}}?workspaceId={{workspaceId}}
* Headers:
    * Content-Type: application/json;charset=UTF-8
    * Authorization: Bearer {{AuthToken}}
* Body: 
    ```
    {
    "created": 1563781812755,
    "description": "Project is running under test",
    "id": "a1jlGGwB5tgkpL6TQv30",
    "lastModified": 1563785773812,
    "name": "{{projectName}}",
    "type": "DESIGN",
    "userId": "pEGWCGwBjlTPLZEzy_-G",
    "workspaceId": "q0eWCGwB6ANMBjnly4Xn"
    }
   ```
* Expected Response Code: 200 
* Expected Response Data: Project name will be created for specified project id in json format provided below.
   ```
     {
        "created": 1563534310522,
        "description": "Workspace Description",
        "id": "OWA7I2wB6ANMBjnljPXv",
        "lastModified": 1563534310522,
        "name": "Workspace Name",
        "type" : "Design",
        "userId": "pEGWCGwBjlTPLZEzy_-G",
        "workspaceId" : "workspaceId"
      }
   ```

#### To Delete Existing Project: To delete any existing project
* HTTP Method: DELETE
* API:  https://api.octoperf.com/design/projects/{{createdProjectID}}?workspaceId={{workspaceId}}
* Headers:
    * Content-Type: application/json;charset=UTF-8
    * Authorization: Bearer {{AuthToken}}
* Expected Response Code: 204
* Expected Response Data: None


## To Generate Test Report

1. Open Terminal and Go to Desktop and Copy-Paste the below command

   ```
   cd ApiTestingUsingJmeterAndPostman\UsingPostman
   ```
   
2. To run test and generate test report using Newman, run below command in Terminal

   ```
   newman run tests/my_test.json -r html --reporter-html-export reports/test_result.html
   ```
   
3. All test results are found under reports/test_result.html



**All test results are found under reports/test_result.html**
