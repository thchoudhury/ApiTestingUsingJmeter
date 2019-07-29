# API Testing Using Jmeter 

## Overview
Here, APIs of Octoperf websites has been tested using Jmeter.


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


## To Run Tests

1. Open Terminal and Go to Desktop and Copy-Paste the below command

   > cd apache-jmeter-5.1.1\apache-jmeter-5.1.1\bin
   
2. To run the test in Jmeter, run the below command in Terminal. 

      **UserName should be replaced before executing command**
      
   > jmeter -n -t C:\Users\<UserName>\Desktop\ApiTestingUsingJmeterAndPostman\UsingJmeter\tests\my_test.jmx -l C:\Users\<UserName>\Desktop\ApiTestingUsingJmeterAndPostman\UsingJmeter\results\my_test.jtl


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
* Response Code: 204
* Response Data: None


## To Generate Test Report

 #### Using Jmeter
 
 1. Open Terminal and Go to Desktop and Copy-Paste the below command
 
    > cd apache-jmeter-5.1.1\apache-jmeter-5.1.1\bin
    
2. To run the test and generate report using Jmeter, run the below command in Terminal.

     **UserName should be replaced before executing command**
   
   > jmeter -g C:\Users\<UserName>\Desktop\ApiTestingUsingJmeterAndPostman\UsingJmeter\results\my_test.jtl -o C:\Users\<UserName>\Desktop\ApiTestingUsingJmeterAndPostman\UsingJmeter\reports\my_test_report
   
3. Generated HTML Report can be found in 

   C:\Users\<UserName>\Desktop\ApiTestingUsingJmeterAndPostman\UsingJmeter\reports\my_test_report\index.html
   
Test result is generated in html format.

