# API Testing Using Jmeter And Postman

## Overview
Here, APIs of [Octoperf](https://doc.octoperf.com/) websites has been tested [using Jmeter](https://github.com/thchoudhury/ApiTestingUsingJmeterAndPostman/tree/master/UsingJmeter) and [using Postman](https://github.com/thchoudhury/ApiTestingUsingJmeterAndPostman/tree/master/UsingPostman)


## List of REST APIs
* For Login => https://api.octoperf.com/public/users/login
* Get All Workspace Details => https://api.octoperf.com/workspaces/member-of
* Get All Project Details => https://api.octoperf.com/design/projects/by-workspace/{{workspaceId}}/DESIGN
* To Create New Project => https://api.octoperf.com/design/projects?workspaceId={{workspaceId}}
* Edit Created Project Name => https://api.octoperf.com/design/projects/{{createdProjectID}}?workspaceId={{workspaceId}}
* To Delete Existing Project => https://api.octoperf.com/design/projects/{{createdProjectID}}?workspaceId={{workspaceId}}


## Tested API Details
### Login API
* HTTP Method: POST
* API:  https://api.octoperf.com/public/users/login
* Response Code: 200 

### Get All Workspace Details
* HTTP Method: GET
* API:  https://api.octoperf.com/workspaces/member-of
* Response Code: 200 

### Get All Project Details
* HTTP Method: GET
* API:  https://api.octoperf.com/design/projects/by-workspace/{{workspaceId}}/DESIGN
* Response Code: 200 

### To Create New Project
* HTTP Method: POST
* API:  https://api.octoperf.com/design/projects?workspaceId={{workspaceId}}
* Response Code: 200 

### Edit Created Project Name
* HTTP Method: PUT
* API: https://api.octoperf.com/design/projects/{{createdProjectID}}?workspaceId={{workspaceId}}
* Response Code: 200 

### To Delete Existing Project
* HTTP Method: DELETE
* API:  https://api.octoperf.com/design/projects/{{createdProjectID}}?workspaceId={{workspaceId}}
* Response Code: 204

## To Generate Test Result
Test result is generated in html format.
