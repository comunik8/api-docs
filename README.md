## Insurance Revolution - Leads

This documentation will describe to partners how they can submit or delete leads in the dialler system.

Submitting leads is done by sending a HTTP **POST** request to our server with a valid request body in JSON format.

The HTTP response to this request contains any validation issues needing to be fixed in the POST request or a success message.

---

### Adding Leads
### Request
#### URL
https://{example.com}/lead/add?key={API_KEY}  
Your website and API_KEY will be given to you when you start using the dialler system.

#### BODY
Content-type: application/json  
Content: valid JSON object

#### FIELDS
| field | description | validation | required |
| ----- | ----------- | ---------- | :------: |
|email|e-mail address|valid e-mail address|yes|
|first_name|first name||yes|
|surname|surname||yes|
|mobile|primary phone number||yes|
|type|lead type|a valid type name|yes|
|other_phone|any other phone number||no|
|data|any other additional data|valid JSON string|no|
|test|used only for testing whether data provided is valid, does not save lead |"true" or no data |no|

---
### Removing Leads

### Request
#### URL
https://{example.com}/lead/cancel?key={API_KEY}  
Your website and API_KEY will be given to you when you start using the dialler system.

#### BODY
Content-type: application/json  
Content: valid JSON object

#### FIELDS
| field | description | validation | required |
| ----- | ----------- | ---------- | :------: |
|type|lead type|a valid type name|yes|
|mobile|primary phone number||yes|

---
### DATA
To include additional information within the dialler system about a lead, you can include other data not specified by us. You will need to format the data in JSON string format with escaped quote marks.  
e.g:
"data": "{\"vehicle_make\":\"Ford\",\"addresss\":\"123 Greenacre Road\"}"
### TYPES
To create or delete a valid lead, you must specify the lead type. These types will be given to you when you start using the dialler system.

---

### EXAMPLES
#### CREATING LEADS
##### Successful Submission of lead
```
curl -X POST -H "Content-Type: application/json" -H "Cache-Control: no-cache" -d '{
    "first_name":"John",
    "surname":"Doe",
    "mobile":"07840258823",
    "email":"john.doe@test.com",
    "type":"motor-trade"
  }' "https://{example.com}/lead/add?key={API_KEY}"
```
Will receive:
```
{
    "saved": true,
    "processed": true
}
```
This means that the data has been saved and also the data has been accepted as a new lead.  
##### Correct format lead test
```
curl -X POST -H "Content-Type: application/json" -H "Cache-Control: no-cache" -d '{
    "first_name":"John",
    "surname":"Doe",
    "mobile":"07840258823",
    "email":"john.doe@test.com",
    "type":"motor-trade",
    "test": true
  }' "https://{example.com}/lead/add?key={API_KEY}"
```
Will Receive:
```
{
    "test": "ok"
}
```
This means that your data format is correct and you can submit this to create a valid lead.
