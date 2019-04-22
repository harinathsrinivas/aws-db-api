# Document-count rest API
API to return Document Count data stored in AWS RDS (postgres) database. 

## Guidelines
This document provides guidelines and examples for using the Document-count rest API framework. 
White House Web APIs, encouraging consistency, maintainability, and best practices across applications. Document-count API aims to deliver the count of the given type of ducument from the data available in the RDS database.


## RESTful URLs
This API provides document details stored in the db based on 3 attributes of the documents stored, which are

    DocumentType    - http://localhost:8000/DocumentType/
    Language        - http://localhost:8000/Language/
    Confidentiality - http://localhost:8000/Confidentiality/

These are 3 endpoints of the API.
Example: DocumentType API can be used to "display the count of documents of type Email", 
         Language API can be used to "display the count of documents which are in English"
         Confidentiality can be used to "display the number of documents which are Highly Confidential"
         

## Return type
This API returns the json with the correspondig data for the given URL / GET request.
Example:
The following can be one return value for DocumentType API.

{
    "id": 2,
    "url": "http://localhost:8000/DocumentType/2/",
    "name": "Excel",
    "total_docs": 57506
}

## Authentication
All the 3 APIs here will allow only authenticated users to perform any request (like POST). Requests for unauthorised users will only be permitted if the request method is one of the "safe" methods; GET, HEAD or OPTIONS.


## Database
The application connects to a AWS RDS database (postgres) to get all the data, to be displayed and modified. This doesn't use an internal DB, so a DB need not be built before starting the application and can directly start the aplication with commands mentioned below. 


## Dockerized
This App is dockerised with docker, and can be simply started or built with the following commands.

cd document-count-api/
docker-compose up

## Test
We can use the URL's directly to get the data from the database 
	http://localhost:8000
	http://localhost:8000/DocumentType   --- Displays all items (in json) with URL's as hyperlink
	http://localhost:8000/DocumentType/4 --- Displays contents of only the 5th item from DocumentType API endpoint.
or we can use get method from the postman to hit the same service.  
