# ![postgis logo](images/post.png) PostgreSQL + PostGIS
<hr>


#### Prerequisites
1.	A **virtual machine** in the DAaaS Environment. See the [VM page](vm.md) for more information.
2.  **pgAdmin** or **Azure Data Studio** and **Visual Studio Code** or **ArcGIS Pro** or**QGIS**. 

Your preferred software will be pre-installed on the **Windows GEO Virtual Machine** based on your onbaording requirments.  
<br>

## Accessing via:

### pgAdmin
This is one of the common tool for PostgreSQL database administration.

1. In your cloud VM install pgAdmin from https://www.pgadmin.org/download/

2. Connect to your cloud VM and launch **pgAdmin**.

   ![LaunchPgAdmin](images/PgSql_01.png)

3. Add the server you need to connect to by right clicking on Servers in the top left corner

   ![CreateServer](images/PgSql_02.png)

4. In the General tab, enter a name for your server. You can write the real name of the server
   In the Connection tab, enter the full Server name and add your Cloud Account  as Username followed by the server name
   or the active directory group you belong to followed by the server name if access to the server was granted to that active directory group.

   ![pgAdminParameters](images/PgSql_03.png)

5. You can now see in the list of server the newly added server. 
   Click on it to connect and you will be asked to enter a password

   ![EnterPassword](images/PgSql_04.png)

6. The password you need to enter is a Azure AD access Token that will be generated for an authenticated Azure AD user. 
   From PowerShell, you can generate this access token by entering the following command

   *az account get-access-token --resource https://ossrdbms-aad.database.windows.net*

   The output is as follow, where you will need to copy the value for accessToken and use it as Password in  pgAdmin

   ![AccessToken](images/PgSql_05.png)

### ArcPro
1. 

2. 

3. 

---

### QGIS
1. 

2. 

3. 

---
### Azure Data Studio

### Azure Data Factory

A linked service can be setup inside Azure Data Factory.
Username is **Cloud account username** or AD group name if access was granted to a AD group, followed by the server name.
Password is an Azure AD access Token as described below in step 6 of pgAdmin section

![ConnectDataFactorySynapse1](images/PgSql_08.png)
or
![ConnectDataFactorySynapse2](images/PgSql_09.png)

Please contact the support team through the https://cae-eac.slack.com channel if you need assistance.
  
---