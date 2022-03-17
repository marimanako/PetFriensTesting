# PetFriensTesting
Pytest и автотесты для REST API
Задание 19.7.2
У нас есть готовая библиотека с реализацией основных методов, но остались ещё два нереализованных метода. Это и будет первым практическим заданием: посмотреть документацию к имеющимся API-методам на сайте. Найти методы, которые ещё не реализованы в библиотеке, и написать их реализацию в файле api.py.

Как вы уже изучали ранее, видов тестирования много, соответственно, и тест-кейсов может быть очень много. Мы с вами написали пять простых позитивных тестов, проверяющих функционал с корректными данными, с ожиданием того, что всё пройдёт хорошо. Наша задача — убедиться, что система возвращает статус с кодом 200. Но как будет реагировать тестируемое приложение, если мы в параметрах передадим слишком большое значение или вообще его не передадим? Что будет, если мы укажем неверный ключ авторизации и так далее?
Подумайте над вариантами тест-кейсов и напишите ещё 10 различных тестов для данного REST API интерфейса. Готовые тест-кейсы разместите на GitHub и пришлите ссылку.


PetFriends API v1
 1.0.0 
[ Base URL: petfriends1.herokuapp.com/ ]/apispec_1.json
API for PetFriends project.
Schemes

HTTPS
default

POST
​/api​/create_pet_simple
Add information about new pet without photo
This method allows to add information about new pet.

Parameters
Try it out
Name	Description
auth_key *
string
(header)	
The API key which is used for authentication. The API key can be achieved with /api/key API endpoint.

auth_key - The API key which is used for authentication. The API key can be achieved with /api/key API endpoint.
name *
string
(formData)	
The name of pet
name - The name of pet
animal_type *
string
(formData)	
The kind of pet (for instance, German Shepherd, Scottish Fold and etc.)

animal_type - The kind of pet (for instance, German Shepherd, Scottish Fold and etc.)
age *
number
(formData)	
The age of the pet
age - The age of the pet
Responses
Response content type

application/json
Code	Description
200	
The status code 200 means that pet was successfully added to the database.
Example Value
Model
{ "age" : 2 , "animal_type" : "немецкая овчарка" , "created_at" : "1587707210.3641336" , "id" : "9C4AEC87-37A4-4EE0-8F1B-3170C816536C" , "name" : "Боб" , "pet_photo " : "" , "user_id" : "ea738148a1f19838e1c5d1413877f3691a3731380e733e877b0ae729" }                            
   
   
   
   
   
   
   
400	
The error code means that provided data is incorrect
403	
The error code means that provided auth_key is incorrect

GET
​/api​/key
Get API key
This method allows to get API key which should be used for other API methods.

Parameters
Try it out
Name	Description
email *
string
(header)	
The email of registered user.
email - The email of registered user.
password *
string
(header)	
The password of registered user.
password - The password of registered user.
Responses
Response content type

application/json
Code	Description
200	
A secret key which can be used in Header "auth_key" for other API methods

Example Value
Model
{
  "key": "ea738148a1f19838e1c5d1413877f3691a3731380e733e877b0ae729"
}
403	
The error code means that provided combination of user email and password is incorrect
GET
​/api​/pets
Get list of pets
POST
​/api​/pets
Add information about new pet
This method allows to add information about new pet.

Parameters
Try it out
Name	Description
auth_key *
string
(header)	
The API key which is used for authentication. The API key can be achieved with /api/key API endpoint.

auth_key - The API key which is used for authentication. The API key can be achieved with /api/key API endpoint.
name *
string
(formData)	
The name of pet
name - The name of pet
animal_type *
string
(formData)	
The kind of pet (for instance, German Shepherd, Scottish Fold and etc.)

animal_type - The kind of pet (for instance, German Shepherd, Scottish Fold and etc.)
age *
number
(formData)	
The age of the pet
age - The age of the pet
pet_photo *
file
(formData)	
The image file with photo of the pet. The file should be in JPG, JPEG or PNG format.

Файл не выбран
Responses
Response content type

application/json
Code	Description
200	
The status code 200 means that pet was successfully added to the database.
Example Value
Model
{ "age" : 2 , "animal_type" : "немецкая овчарка" , "created_at" : "1587707210.3641336" , "id" : "9C4AEC87-37A4-4EE0-8F1B-3170C816536C" , "name" : "Боб" , "pet_photo " : "data:image/jpeg;base64, ......" , "user_id" : "ea738148a1f19838e1c5d1413877f3691a3731380e733e877b0ae729" }                                                        
   
   
   
   
   
   
   
400	
The error code means that provided data is incorrect
403	
The error code means that provided auth_key is incorrect

POST
​/api​/pets​/set_photo​/{pet_id}
Add photo of pet
This method allows to add photo of a pet.

Parameters
Try it out
Name	Description
auth_key *
string
(header)	
The API key which is used for authentication. The API key can be achieved with /api/key API endpoint.

auth_key - The API key which is used for authentication. The API key can be achieved with /api/key API endpoint.
pet_id *
string
(path)	
The ID of existing pet
pet_id - The ID of existing pet
pet_photo *
file
(formData)	
The image file with photo of the pet. The file should be in JPG, JPEG or PNG format.

Файл не выбран
Responses
Response content type

application/json
Code	Description
200	
The status code 200 means that pet was successfully added to the database.
Example Value
Model
{
  "age": 2,
  "animal_type": "German Shepherd",
  "created_at": "1587707210.3641336",
  "id": "9C4AEC87-37A4-4EE0-8F1B-3170C816536C",
  "name": "Bob",
  "pet_photo": "data:image/jpeg;base64, ......",
  "user_id": "ea738148a1f19838e1c5d1413877f3691a3731380e733e877b0ae729"
}
400	
The error code means that provided data is incorrect
403	
The error code means that provided auth_key is incorrect

DELETE
​/api​/pets​/{pet_id}
Delete pet from database
This method allows to delete information about pet from database.

Parameters
Try it out
Name	Description
auth_key *
string
(header)	
The API key which is used for authentication. The API key can be achieved with /api/key API endpoint.

auth_key - The API key which is used for authentication. The API key can be achieved with /api/key API endpoint.
pet_id *
string
(path)	
The ID of pet which should be deleted from database.
pet_id - The ID of pet which should be deleted from database.
Responses
Response content type

application/json
Code	Description
200	
200 status code means that the pet was removed from database successfully.
403	
The error code means that provided auth_key is incorrect

PUT
​/api​/pets​/{pet_id}
Update information about pet
This method allows to update information about pet.

Parameters
Try it out
Name	Description
auth_key *
string
(header)	
The API key which is used for authentication. The API key can be achieved with /api/key API endpoint.

auth_key - The API key which is used for authentication. The API key can be achieved with /api/key API endpoint.
pet_id *
string
(path)	
The id of the pet which should be updated
pet_id - The id of the pet which should be updated
name
string
(formData)	
New name of the pet
name - New name of the pet
animal_type
string
(formData)	
The kind of pet (for instance, German Shepherd, Scottish Fold and etc.)

animal_type - The kind of pet (for instance, German Shepherd, Scottish Fold and etc.)
age
number
(formData)	
The new age of the pet
age - The new age of the pet
Responses
Response content type

application/json
Code	Description
200	
The status code 200 means that the information about pet was successfully updated in the database.
Example Value
Model
{
  "age": 2,
  "animal_type": "German Shepherd",
  "created_at": "1587707210.3641336",
  "id": "f1b2c449-a41b-43fe-a9f7-d5493e9dd911",
  "name": "Bob",
  "pet_photo": "data:image/jpeg;base64, ......",
  "user_id": "ea738148a1f19838e1c5d1413877f3691a3731380e733e877b0ae729"
}
400	
The error code means that provided data is incorrect
403	
The error code means that provided auth_key is incorrect
