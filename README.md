## Insurance Revolution - Leads

This documentation will describe to partners how they can submit or delete leads in the dialler system.

Submitting leads is done by sending a HTTP **POST** request to our server with a valid request body in JSON format.

The HTTP response to this request contains any validation issues needing to be fixed in the POST request or a success message.

---

### Adding Leads
### Requests
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

### Requests
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

### TYPES
To create or delete a valid lead, you must specify the lead type. These types will be given to you when you start using the dialler system.

### EXAMPLES
