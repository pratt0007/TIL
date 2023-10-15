  # REST API
- REST is an acronym name of Representational State Transfer, a standardized way to provide data to other applications.
- In other words, it is used for building and communicating with web services. It is the best way to transfer data across the applications and can be used by the application.
- It mandates resources on the web are represented in JSON, HTML, or XML. Sometimes APIs are used in the other application to change the data.

## API 
- An API is an acronym for Application Programming Interface, an interface that defines the interaction between different software components.
- An API is a software intermediary that allows two or more applications to talk to
each other.
- Web APIs determine what exactly request is made to the component.
- For example We define an endpoint to get the list of the students of a particular branch.
### API types in terms of Release Policies:-
- Private - It can be used within the organization.
- Partner - It can be used within Business Partner.
- Public It can be used by any 3rd part developer.

### Web API
![image](https://github.com/pratt0007/TIL/assets/100209212/e57a6292-a0aa-46e0-9db5-b8920cbcb37b).


### Keys of REST API
- GET It is most common method for get some data from component. It returns some data from the API based on the endpoint we hit and any parameter we pass.
- POST It creates the new records and updates the new created record in the database.
- PUT It takes the new records at the given URI. If the record exists, update the record. If record is not available, create a new record.
- PATCH It takes one or more fields at the given URI. It is used to update one or more data fields. If the record exists, update the record. If the record is not available, create a new record.
- DELETE It deletes the records at the given URI.
- The API URL can not have HTTPS only HTTP is there
- Eg http://geekyshows.com/api/student  is the url for studemt api

```
CREATE --> POST
READ ----> GET
UPDATE---> PUT
DELETE---> DELETE
```
![image](https://github.com/pratt0007/TIL/assets/100209212/1f7b98e3-7ca4-4a3b-9d41-664440589471)

### What is Django Rest Framework?
- Django Rest Framework (DRF) is a package built on the top of Django to create web APIs. It provides the most extensive features of Django, Object Relational Mapper (ORM), which allows the interaction of databases in a Pythonic way.
- Hence the Python object can't be sent over the network, so we need to translate Django models into the other formats like JSON, XML, and vice-versa. This process is known as serialization, which the Django REST framework made super easy.

