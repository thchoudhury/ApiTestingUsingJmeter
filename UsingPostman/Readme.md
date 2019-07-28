# API Testing Using Postman
This document provides instruction of testing of RESTful APIs using Postman and Newman(if CLI is used)

# Install Postman and Newman 
* Download Postman from <https://www.getpostman.com/apps>
* Install Newman using **npm install -g newman**
* Newman-html-reporter using **npm i -g newman-reporter-html**

# Run Test using CLI
* In terminal, run the below command
	__newman run tests/my_test.json -r html --reporter-html-export reports/test_result.html__
	 
	 where  --reporter-html-export <path> denotes path where the output HTML file will be written to disk.
			-r html denotes the report type. It could be json, junit, csv also



**All test results are found under reports/test_result.html**
