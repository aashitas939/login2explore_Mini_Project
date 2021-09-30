# JsonPowerDB
## Description
This project is about basics of JsonPowerDB (JPDB), CRUD Operation and creating a form, validating it and adding the user data to the JPDB.
## Benefits of Using JsonPowerDB
1)Simplest way to retrieve data in a JSON format.  

2)Schema-free, Simple to use, Nimble and In-Memory database.

3)It is built on top of one of the fastest and real-time data indexing engine - PowerIndeX.

4)It is low level (raw) form of data and is also human readable.

5)It helps developers in faster coding, in-turn reduces development cost.

## Table of Content

1)Performing Crude operations 

Here we are using Talend API Tester(TAT) to execute CRUD operations.

i. Creating (inserting) a row.
   
   a) We need to specify api Base url and End-Point url in TAT in order to use it. 
   
   b) We need to mention PUT request command in the body of Talend API.
   
   Following is the code for the same:
   
   {
    "token": "90936110|-31948821198377600|90944048",
    
    "cmd": "PUT",
    
    "dbName": "Employee",
    
    "rel": "index",
    
    "jsonStr": {
    
        "name": "Sulbha Mishra",
        
        "email": "sulbhamishra@gmail.com",
        
        "password": "323",

    }
}

After execution, a record is being created.

ii. Reading a row using get

   a) We need to specify api Base url and End-Point url in TAT in order to use it. 
   
   b) We need to mention GET request command in the body of Talend API.
   
   Following is the code for the same:
   
   {
   
    "token": "90936110|-31948821198377600|90944048",
    
    "cmd": "GET",
    
    "dbName": "Employee",
    
    "rel": "Emp-Rel",
    
    "jsonStr": {
    
     "name":"Aashita Singh"

    }
    
}

*Like wise we need to do it for update and delete command using post method.

2)Creating an Html form and adding user details to the JPDB.

 i. Creating a simple HTML form.
 
 ii.Adding adding data to the database:
    
    a)Validate Form Data.
    
    b)Create JPDB Request String.
    
    c)Execute the data.
    
    d)Reset the Form data.
    
 Code:
 
 <!DOCTYPE html>
 
<!--

To change this license header, choose License Headers in Project Properties.

To change this template file, choose Tools | Templates

and open the template in the editor.

-->

<html lang="en">

<head>

<title>Bootstrap Example</title>

<meta charset="utf-8">

<meta name="viewport" content="width=device-width, initial-scale=1">

<link rel="stylesheet"

href="https://maxcdn.bootstrapcdn.com/bootstrap/3.4.1/css/bootstrap.min.css">

<script

src="https://ajax.googleapis.com/ajax/libs/jquery/3.5.1/jquery.min.js"></script>

<script

src="https://maxcdn.bootstrapcdn.com/bootstrap/3.4.1/js/bootstrap.min.js"></script>

<script

src="https://login2explore.com/jpdb/resources/js/0.0.3/jpdb-commons.js"></script>

</head>

<body>

<div class="container">

<h2>Vertical (basic) form</h2>

<form id="empForm" method="post">

<div class="form-group">

<span><label for="empId">Employee ID:</label> <label id="empIdMsg">

</label></span>

<input type="text" class="form-control" name="empId" id="empId"

placeholder="Enter Employee ID" required>

</div>

<div class="form-group">

<label for="empName">Employee Name:</label>

<input type="text" class="form-control" id="empName"

placeholder="Enter Employee Name" name="empName">

</div>

<div class="form-group">

<label for="empEmail">Email:</label>

<input type="email" class="form-control" id="empEmail"

placeholder="Enter Employee Email" name="empEmail">

</div>

<input type="button" class="btn btn-primary" id="empSave" value="Save"

onclick="saveEmployee();">

</form>

</div>

    <script>
    
        function validateAndGetFormData() {
        
var empIdVar = $("#empId").val();

if (empIdVar === "") {

alert("Employee ID Required Value");

$("#empId").focus();

return "";

}

var empNameVar = $("#empName").val();

if (empNameVar === "") {

alert("Employee Name is Required Value");

$("#empName").focus();

return "";

}

var empEmailVar = $("#empEmail").val();

if (empEmailVar === "") {

alert("Employee Email is Required Value");

$("#empEmail").focus();

return "";

}

var jsonStrObj = {

empId: empIdVar,

empName: empNameVar,

empEmail: empEmailVar

};

return JSON.stringify(jsonStrObj);

}

function resetForm() {

$("#empId").val("");

$("#empName").val("");

$("#empEmail").val("");

$("#empId").focus();

}

       function saveEmployee() {
       
var jsonStr = validateAndGetFormData();

if (jsonStr === "") {

return;

}

var putReqStr = createPUTRequest("90936110|-31948821198377600|90944048",

jsonStr, "SAMPLE", "EMP-REL");

alert(putReqStr);

jQuery.ajaxSetup({async: false});

var resultObj = executeCommandAtGivenBaseUrl(putReqStr,

"http://api.login2explore.com:5577", "/api/iml");

alert(JSON.stringify(resultObj));

jQuery.ajaxSetup({async: true});

resetForm();

}
    
        </script>
</body>
</html>

  
    

   
## Release History
 0.2.1
 1. Basic CRUD operation
 
 2. Basic Form Validation
 
 3. Adding Form Details to JPDP

0.2.0

1) Work in Progress
