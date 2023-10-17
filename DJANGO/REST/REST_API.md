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

 ![image](https://github.com/pratt0007/TIL/assets/100209212/c7b676b3-076e-41a5-8703-64e16fc484d5)

#### Python JSON
- Python has a built in package called json, which is used to work with json data.
- dumps(data) is used to cinvert python object into json string.
```python
import json
python_data = {'name' : sonam , 'roll':101}
json_data = json.dumps(python_data)
```
##### Parsing JSON string
- Parsing a JSON (JavaScript Object Notation) string means extracting structured data from a text-based format.
- converting back data form KSON to python we require loads
- Things done
    - Reading JSON
    - CONVERTING to Data Structure
    - Accesing Data
```python
import json

# Sample JSON string
json_str = '{"name": "John", "age": 30, "city": "New York"}'

# Parse the JSON string into a Python dictionary
data = json.loads(json_str)

# Access data from the dictionary
name = data['name']
age = data['age']
city = data['city']

print(f"Name: {name}, Age: {age}, City: {city}")
```
## Serializers
- In Django REST Framework, serializers are responsible for converting complex data such as querysets and model instances to native Python datatypes (called serialization) that can then be easily rendered into JSON, XML or other content types which is understandable by Front End.
- Serializers are also responsible for deserialization which means it allows parsed data to be converted back into complex types, after first validating the incoming data.

### Creating a Serializer class
- Create a separate seriealizers.py file to write all serializers
```PYTHON
from rest framework import serializers
class StudentSerializer(serializers.Serializer):
 name = serializers.CharField(max_length=100)
 roll = serializers.IntegerFieldO
 city = serializers.CharField(max_length=100)
```
- Here are main focus is to convert our data to JSON data so that it could be sent to the client.
![image](https://github.com/pratt0007/TIL/assets/100209212/c502d9d3-ae14-4709-bc91-d35e58bc09d3)
- Here we make models.py in django and we make a model in it which stores the data in dataabse in the form of a table. Now we need to transmit the data to our client for that first we need to concvert the data in JSON file.
![image](https://github.com/pratt0007/TIL/assets/100209212/cc06c85d-a337-4c57-b56e-814fd7124462)

### Serialization
- The process of converting complex data such as querrysets and model instances to native python datatypes are called serialization in DRF.
- 1. Creating a model instance stu
     stu = Student.objects.get(id=1)
  2. Converting model instance stu to python dic/ serializing object
     serializer = StudentSerializer(stu)
- To see serialized data - serializer.data
### JSON Renderer
- This is used to render Serialized data into JSON which is understandable by Front End.
- Importing JSONRenderer = from rest_framework.renderers import JSONRenderer
- Render the Data into Json = json_data = JSONRenderer.render(serializer.data)
![image](https://github.com/pratt0007/TIL/assets/100209212/540fc0de-d5c2-49ae-b3b3-bf0f8d99253b)



