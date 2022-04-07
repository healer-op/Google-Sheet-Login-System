# Google-Sheet-Login-System
📝 Google Sheet Login System

### Preview
https://healer-op.github.io/Google-Sheet-Login-System/
![image](https://user-images.githubusercontent.com/65026164/162122749-0985b2f8-9d93-4094-bb70-56d3b91b9f34.png)
![image](https://user-images.githubusercontent.com/65026164/162122770-9fdb81de-5e88-4742-88e9-bfb03fc3882d.png)

##### code.gs
```
// Made by
// https://github.com/healer-op
function doGet(e) {
  var x = HtmlService.createTemplateFromFile("index");
  var y = x.evaluate();
  var z = y.setXFrameOptionsMode(HtmlService.XFrameOptionsMode.ALLOWALL);
  return z;
}


function checkLogin(username, password) {
  var url = 'https://docs.google.com/spreadsheets/d/YOURSHEETS';
  var ss= SpreadsheetApp.openByUrl(url);
  var webAppSheet = ss.getSheetByName("DATA");
  var getLastRow =  webAppSheet.getLastRow();
  var found_record = '';
  for(var i = 1; i <= getLastRow; i++)
  {
   if(webAppSheet.getRange(i, 1).getValue().toUpperCase() == username.toUpperCase() && 
     webAppSheet.getRange(i, 2).getValue().toUpperCase() == password.toUpperCase())
   {
     found_record = 'TRUE';
   }    
  }
  if(found_record == '')
  {
    found_record = 'FALSE'; 
  }
  
  return found_record;
  
}

function AddRecord(usernamee, passwordd, email) {
  var url = 'https://docs.google.com/spreadsheets/d/YOURSHEETS';
  var ss= SpreadsheetApp.openByUrl(url);
  var webAppSheet = ss.getSheetByName("DATA");
  webAppSheet.appendRow([usernamee,passwordd,email]);
  
}
```
