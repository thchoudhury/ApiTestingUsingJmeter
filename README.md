# API Testing Using Jmeter And Postman

## RESTful URLs
### General guidelines for RESTful URLs
* A URL identifies a resource.
* URLs should include nouns, not verbs.
* Use plural nouns only for consistency (no singular nouns).
* Use HTTP verbs (GET, POST, PUT, DELETE) to operate on the collections and elements.
* **URL v. header:**
  * If it changes the logic you write to handle the response, put it in the URL.
  * If it doesn’t change the logic for each response, like OAuth info, put it in the header.
  * Specify optional fields in a comma separated list.
  * Formats should be in the form of api/v2/resource/{id}.json
