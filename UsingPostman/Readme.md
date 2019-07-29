# API Testing Using Postman

## Overview

Here, APIs of Octoperf websites has been tested using Postman and Newman(if CLI is used). 

## Install Postman and Newman 

* Download Postman from <https://www.getpostman.com/apps>
* Install Newman using **npm install -g newman**
* Newman-html-reporter using **npm i -g newman-reporter-html**

## Run Test using CLI

* In terminal, run the below command
	__newman run tests/my_test.json -r html --reporter-html-export reports/test_result.html__


**All test results are found under reports/test_result.html**
