# Azure_set_up

## overview
- create resource group
- create sql database

## flow chart

### create resource group
   A resource group is a container that holds related resources for an Azure solution. A resource group is a logical grouping of models that manages access to and provides security for the models within it. When you create a resource group, it is assigned to the root resource group. You assign roles that grant specific privileges to a user within a resource group, and not to a model directly.
   create resource group (if it is not exist)
    <img src= "images/resource_group_1">
    fill up basic imformation
    <img src= "images/resource_group_2">
    if it has created successfully, it shows in notifition
    <img src= "images/resource_group_3">
    
### create sql database
  when we are trying to create sql databse, we need to create sql datdabase server if it is not exist
  create sql database server
  <img src= "images/database_server">
  There is no azure AD admin, so we should search "aad" to default directory, and we can click user on the left of the page to create user.
  <img src= "images/create_new_user">
  The page shows the user we created successfully. We can copy the user_name.
 <img src= "images/user_created">
  Then we can choose the user as azure AD admin and create database server
 <img src= "images/database_server2">
  
### create storage account
  <img src= "images/storage_account">
  
### connnect in ssms
We should download ssms first, and open the application.
Copy server name from database server we created before.
If you fail to connect sql server, go to sql server you created and click 'network' under security on the left of the page and add client IP address.
  <img src= "images/ssms_connect">
Then you can connect database to ssms
  <img src= "images/ssms_1">
 click 'new Query' on the top bar and type code to create a simple table
  <img src= "images/ssms_create_table">
  
 ### create a data factory
 create a data factory
  <img src= "images/create_data_factory">
  
  manage identities to make true we have a role to contribute to sql server.
  add azure role assignments
  <img src= "images/data_factory_identities">
  
  Then we launch studio.
  
 ### add link service
  link sql database
 <img src= "images/link_service">
 
 set up link service
 <img src= "images/link_service">
 
 add user to ssms
  <img src= "images/add_user_ssms">
  
  add link service to snowflack
  <img src= "images/link_snowflack">

  add link service to storage account
  <img src= "images/link_blob_storage">
  To get the URL, we need to add containers
  <img src= "images/create_container">
   and give the permission
  <img src= "images/permission">
