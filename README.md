# Azure_set_up

The project shows the step to step to set up Azure and connect Azure to SSMS(SQL Server Management Studio) and shows the basic activity like copying data from SSMS to Snowflake using Azure data factory.

## overview
- create resource group
- create sql database
- create storage account
- connnect to ssms
- create a data factory
- add link service
- create pipeline and copy data from ssms to snowflake

## flow chart
<img src= "images/flow_chart.png">

### create resource group
   A resource group is a container that holds related resources for an Azure solution. A resource group is a logical grouping of models that manages access to and provides security for the models within it. When you create a resource group, it is assigned to the root resource group. You assign roles that grant specific privileges to a user within a resource group, and not to a model directly.
   create a resource group (if it does not exist)
 <img src= "images/resource_group_1.jpg">
  
  fill up basic information
 <img src= "images/resource_group_2.jpg">
  
  if it has been created successfully, it shows in the notification
 <img src= "images/resource_group_3.jpg">
    
### create sql database
  when we are trying to create SQL database, we need to create SQL database server if it is not exist
  create SQL database server
  <img src= "images/database_server.jpg">
  There is no Azure AD admin, so we should search "aad" to the default directory, and we can click user on the left of the page to create a user.
  <img src= "images/create_new_user.jpg">
  The page shows the user we created successfully. We can copy the user_name.
 <img src= "images/user_created.jpg">
  Then we can choose the user as Azure AD admin and create a database server.
 <img src= "images/database_server2.jpg">
  
### create storage account
  <img src= "images/storage_account.jpg">
  
### connnect to ssms
We should download ssms first, and open the application.
Copy the server name from the database server we created before.
Copy server name from database server we created before.
If you fail to connect SQL server, go to the SQL server you created and click 'network' under security on the left of the page and add the client IP address.
  <img src= "images/ssms_connect.jpg">
Then you can connect the database to ssms
  <img src= "images/ssms_1.jpg">
Click 'new Query' on the top bar and type the code to create a simple table
  <img src= "images/ssms_create_table.jpg">
  
 ### create a data factory
 create a data factory
  <img src= "images/create_data_factories.jpg">
  
manage identities to make true we have a role to contribute to SQL server.
add Azure role assignments
  <img src= "images/data_factory_identities.jpg">
  
Then we launch the studio.
  
 ### add link service
  link SQL database
 <img src= "images/link_service.jpg">
 
 set up link service
 <img src= "images/link_service_2.jpg">
 
 add a user to ssms
  <img src= "images/add_user_ssms.jpg">
  
  add link service to snowflake
  <img src= "images/link_snowflack.jpg">

  add link service to the storage account 
  <img src= "images/link_blob_storage.jpg">
  
  To get the URL, we need to add containers
  <img src= "images/create_container.jpg">
   and give the permission
  <img src= "images/permission.jpg">
  add role assignment for the account storage
  <img src= "images/add_role_ass.jpg">  
  <img src= "images/add_role_ass_2.jpg">  
  
  Copying the URL to the storage account to add the link service, then a new link service has been added.
  
  ### copy data from ssms to snowflake
create a pipeline, name it, and use the 'copy data' activity in factory resources
 <img src= "images/copy_data_1.jpg"> 
create source dataset
 <img src= "images/copy_data_2.jpg"> 
create sink dataset
 <img src= "images/copy_data_3.jpg"> 
enable staging and compression so that it can be published and saved
 <img src= "images/copy_data_4.jpg"> 
 
add a trigger to schedule a certain time to run the procedure
  <img src= "images/add_trigger.jpg"> 
 
