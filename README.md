### **Rest Booking API Testing with Postman Newman**
This project demonstrates API testing using Postman, providing a collection of tests to validate various endpoints of the API. 

### **Features**

- Tests for GET, POST, PUT, DELETE requests
- Collection of tests covering different API endpoints
- Environment setup for easy switching between environments
- Pre-request scripts for data setup
- Test scripts for assertions and validations

  
### **Technology used:**
- Postman
- Newman

### **Prerequisite:**
- Node Js
- Newman
- Newman Html Report Library

### **Installation**

1. Postman: If you haven't already, [download and install Postman.](https://www.postman.com/downloads/)
2. Clone the repository:
 ```console 
  git clone https://github.com/Nowshin14/API-Testing-with-Newman.git
```
3. Import the Postman collection:
    - Open Postman.
    - Click on the Import button.
    - Select the file from the repository.
4. Import the Postman environment:
    - In Postman, click on the gear icon in the top right corner.
    - Select **Import** and choose the file.
5. Newman and Report Installation Process:
    - Newman Install Command:
     ```console 
      npm install -g newman
    ```
    - Newman Html Report Install Command:
     ```console 
      npm install -g newman-reporter-htmlextra
    ```
### **Usage**
1. Select Environment:
    -   In Postman, select the appropriate environment (e.g., Development, Production) from the top-right dropdown.
3. Run Collection:
    -   Select the imported collection from the Collections sidebar.
    -   Click on the Runner button to open the collection runner.
    -   Select the desired environment.
    -   Click Start Test to run the collection.
8. View Results:
    -   Once the tests are complete, view the results in the Runner tab.
    -   Detailed test results can be viewed for each request.

## **Testing**

## Test Case Scenarios:

## _**1. Create New Booking**_

### Request URL: https://restful-booker.herokuapp.com/booking/
### Request Method: POST
### Pre-request Script:
```console
//FirstName
var firstName = pm.variables.replaceIn("{{$randomFirstName}}");
console.log(firstName);
pm.environment.set("firstName",firstName)

//LastName
var lastName = pm.variables.replaceIn("{{$randomLastName}}");
pm.environment.set("lastName",lastName);

//TotalPrice
var totalPrice = pm.variables.replaceIn(Math.floor(Math.random() *9000))
pm.environment.set("totalPrice",totalPrice);

//DepositPaid
var depositPaid = pm.variables.replaceIn("{{$randomBoolean}}");
pm.environment.set("depositPaid",depositPaid);
console.log(depositPaid);

//Date
const moment  = require('moment');
const today = moment();
var checkin = today.add(1,'d').add(2,'M').format("YYYY-MM-DD")
console.log(checkin);
pm.environment.set("checkin",checkin);

var checkout = today.add(3,'d').format("YYYY-MM-DD")
pm.environment.set("checkout",checkout);

//Additional Needs
var additionalNeeds = pm.variables.replaceIn("{{$randomProduct}}")
pm.environment.set("additionalneeds",additionalNeeds);
```
  **Request Body:** 
 ```console 
  {
     "firstname" : "{{firstName}}",
     "lastname" : "{{lastName}}",
     "totalprice" : {{totalPrice}},
     "depositpaid" : {{depositPaid}},
     "bookingdates" : {
         "checkin" : "{{checkin}}",
         "checkout" : "{{checkout}}"
     },
     "additionalneeds" : "{{additionalneeds}}"
 }
```
  **Response Body:**
 ```console 
{
    "firstname": "Georgette",
    "lastname": "Hauck",
    "totalprice": 1085,
    "depositpaid": true,
    "bookingdates": {
        "checkin": "2025-02-26",
        "checkout": "2025-03-01"
    },
    "additionalneeds": "Sausages"
}
```

 ## _**2. Get Booking Details By ID**_
### Request URL: https://restful-booker.herokuapp.com/booking/bookingid
### Request Method: GET
### Response Body:
 ```console 
{
    "firstname": "Georgette",
    "lastname": "Hauck",
    "totalprice": 1085,
    "depositpaid": true,
    "bookingdates": {
        "checkin": "2025-02-26",
        "checkout": "2025-03-01"
    },
    "additionalneeds": "Sausages"
}
```

## _**3. Create A Token For Authentication.**_
### Request URL: https://restful-booker.herokuapp.com/auth
### Request Method: POST
### Pre-request Script: None
### Request Body:
 ```console 
{
	"username": "admin",
	"password": "password123"
}
```
  **Response Body:**
 ```console 
{
    "token": "a17a80741efb184"
}
```
 ## _**4. Update the Booking Details**_
### Request URL: https://restful-booker.herokuapp.com/booking/bookingid
### Request Method: PUT
### Pre-request Script:
 ## _**4. Update the Booking Details**_
### Request URL: https://restful-booker.herokuapp.com/booking/bookingid
### Request Method: PUT
### Pre-request Script:
```console 
//FirstName update
var updated_firstName = pm.variables.replaceIn("{{$randomFirstName}}");
console.log(updated_firstName);
pm.environment.set("updatedFirstName",updated_firstName)

//LastName Update
var updated_lastName = pm.variables.replaceIn("{{$randomLastName}}");
pm.environment.set("updatedLastName",updated_lastName);

//TotalPrice Update
var updatedTotalPrice = pm.variables.replaceIn(Math.floor(Math.random() *9000))
pm.environment.set("updatedTotalPrice",updatedTotalPrice);

//DepositPaid Update
var updated_depositPaid = pm.variables.replaceIn("{{$randomBoolean}}");
pm.environment.set("updatedDepositPaid",updated_depositPaid);

//Date Update
const moment  = require('moment');
const today = moment();
var updated_checkin = today.add(2,'d').add(2,'M').format("YYYY-MM-DD")
console.log(updated_checkin);
pm.environment.set("updatedCheckin",updated_checkin);

var updated_checkout = today.add(5,'d').format("YYYY-MM-DD")
pm.environment.set("updatedCheckout",updated_checkout);

//Additional Needs Update
var updatedAdditionalNeeds = pm.variables.replaceIn("{{$randomProduct}}")
pm.environment.set("updatedAdditionalneeds",updatedAdditionalNeeds);


```
  **Request Body:** 
 ```console 
{
    "firstname": "{{updatedFirstName}}",
    "lastname": "{{updatedLastName}}",
    "totalprice": {{updatedTotalPrice}},
    "depositpaid": {{updatedDepositPaid}},
    "bookingdates":{
        "checkin": "{{updatedCheckin}}",
        "checkout": "{{updatedCheckout}}"
    },
    "additionalneeds": "{{updatedAdditionalneeds}}"
}
```
  **Response Body:**
 ```console 
{
    "firstname": "Roslyn",
    "lastname": "Jacobs",
    "totalprice": 2607,
    "depositpaid": true,
    "bookingdates": {
        "checkin": "2025-02-27",
        "checkout": "2025-03-04"
    },
    "additionalneeds": "Chips"
}
```

 ## _**5. Delete Booking Record**_

### Request URL: https://restful-booker.herokuapp.com/booking/bookingid
### Request Method: DELETE
### Response Body: None 
## Run Command:  
- Run Command for Console: 
```console 
newman run Restful_Booker_API_Testing.postman_collection.json -e Restful_Booker_API_Testing.postman_environment.json 
```
- Run Command for Report: 
```console 
newman run Restful_Booker_API_Testing.postman_collection.json -e Restful_Booker_API_Testing.postman_environment.json -r htmlextra
```

## Newman Report Summary:


![image](https://github.com/user-attachments/assets/aeda8889-09c5-4875-a830-eac7713a22ac)
![image](https://github.com/user-attachments/assets/6572b3c9-fe42-4bad-892c-329effcfcd81)
![image](https://github.com/user-attachments/assets/e68b97d1-e9df-4e05-8cbb-fbd05501399f)







