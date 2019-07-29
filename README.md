# API Testing Using Jmeter And Postman

## Overview
Here, APIs of [Octoperf](https://doc.octoperf.com/) websites has been tested [using Jmeter](https://github.com/thchoudhury/ApiTestingUsingJmeterAndPostman/tree/master/UsingJmeter) and [using Postman](https://github.com/thchoudhury/ApiTestingUsingJmeterAndPostman/tree/master/UsingPostman)


## List of REST APIs

### Login API
* HTTP Method: POST
* API:  https://api.octoperf.com/public/users/login
* Body (form-data): username(string) && password(string)
* Response Code: 200 
* Response Data: {'token': <Generated Token Value (string format)>}

Here, token is stored in variable **AuthToken** for further use.

### Get All Workspace Details
* HTTP Method: GET
* API:  https://api.octoperf.com/workspaces/member-of
* Headers:
    * Content-Type: application/json;charset=UTF-8
    * Authorization: Bearer {{AuthToken}}
* Response Code: 200 
* Response Data: Return all the workspace details.

Here, random 'id' for workspace is stored in variable **workspaceId** for further use.

### Get All Project Details
* HTTP Method: GET
* API:  https://api.octoperf.com/design/projects/by-workspace/{{workspaceId}}/DESIGN
* Headers:
    * Content-Type: application/json;charset=UTF-8
    * Authorization: Bearer {{AuthToken}}
* Response Code: 200 
* Response Data: Return all the project details under specified workspace id.

### To Create New Project
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

### Edit Created Project Name
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

### To Delete Existing Project
* HTTP Method: DELETE
* API:  https://api.octoperf.com/design/projects/{{createdProjectID}}?workspaceId={{workspaceId}}
* Headers:
    * Content-Type: application/json;charset=UTF-8
    * Authorization: Bearer {{AuthToken}}
* Response Code: 204
* Response Data: None

## To Generate Test Result
Test result is generated in html format.



## Test Result

Test result is generated in html format.
