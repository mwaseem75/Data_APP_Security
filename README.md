# Data_APP_Security

## Summary
Web Application build on InterSystems IRIS for Health and Docker to demonstrate Authentication, Authorization AND Auditing basics.
By using the application New user can be created programmatically along with auditing, roles and SQL privileges, Option to Enable/Disable, Authenticate/Unauthenticate web application and OAuth2 Authentication with GitHub

## Features
* Authentication, Authorization and Auditing basics
* OAuth2 Authentication with GitHub
* Create New User by code
* Add Audit Log Programatically
* Create Role and Assign SQL table priviliges by code
* Grant all privileges to user by assigning %All role by code
* Enable/Disable Web Terminal Application by code
* Authenticate/Unauthenticate Web Terminal Application by code

## Community Articles
https://community.intersystems.com/post/programmatically-create-users-grant-privileges-enabledisable-and-authenticateunauthenticate-web 
For OAuth2 GitHub authentication
https://community.intersystems.com/post/oauth2-authentication-github-account-iris-web-application

## Installation with ZPM
```
zpm:USER>zpm "install scw-Patient"
```
## Application Layout
![image](https://user-images.githubusercontent.com/18219467/143904440-21d604b6-43e5-46f6-b19f-0f3292aa5152.png)

## Recommendation 
 * InterSystems online course (InterSystems Security Basics) : https://learning.intersystems.com/course/view.php?id=1774 
 * Read related documentations (Authentication and Authorization) : https://docs.intersystems.com/latest/csp/docbook/DocBook.UI.Page.cls?KEY=TSQS_preface
 * Read related documentations (Auditing Guide) : https://docs.intersystems.com/irislatest/csp/docbook/DocBook.UI.Page.cls?KEY=AAUDIT

## Repo Contents   
* Dockerfile, docker-compose.yml, and Installer.cls to create container
* iris.script, contains script to execute during container initialization 
* /src with source files 
* /.vscode/settings.json for automatic server connections when opened in VS Code.

## Requirements:  
* [Docker desktop]( https://www.docker.com/products/docker-desktop)
* Get the latest InterSystems IRIS for Health image for use in the Dockerfile: https://hub.docker.com/_/intersystems-iris-for-health  

## To Run on Windows:  
```
	git clone https://github.com/mwaseem75/Data_APP_Security.git  
	cd Data_APP_Security  
	docker-compose up -d  
```
## To Run on macOS:  

```
	git clone https://github.com/mwaseem75/Data_APP_Security.git 
	cd Data_APP_Security 
	docker-compose up -d  
```
Log in with credentials: SuperUser | SYS


## Getting Started 

## AUTHENTICATION
* Navigate to http://localhost:52773/csp/user/index.csp index page, First of all create New user by cliking "Create TestUser" button. Make sure to login as SUPERUSER OR _SYSTEM in order to create new User.
Newly created user can be viewed from management portal (System > Security Management > User)
![image](https://user-images.githubusercontent.com/18219467/143899649-a1f630de-fff5-4e08-ae11-30185c83b718.png)

## LOGIN With Github OAUTH2
![image](https://user-images.githubusercontent.com/18219467/144722058-47423b00-f862-4e21-811b-316e7becc684.png)
* 1-Navigate to online Demo https://dappsecurity.demo.community.intersystems.com/csp/user/index.csp by using SuperUser | SYS
* 2-Select menu option "Login with Github account" 
* 3-Enter your github credentials in Github login screen
* 4-For details see the article : https://community.intersystems.com/post/oauth2-authentication-github-account-iris-web-application

## AUDITING
Upon creating user, record with Description "Audit Log inserted from DATA_APP_Security" is added in auditing database which can be viewed from Management portal 
(Security > Security Management > View Audit Database)
![image](https://user-images.githubusercontent.com/18219467/144225356-f285bf7b-226d-45e8-bad6-6ccc525301a5.png)

## AUTHORIZATION
* Navigate to http://localhost:52773/csp/user/scw.DataForm.cls data form by using *TestUser | demo* 
By clicking search button system will raise error: 	
"ERROR #5580: SQL Privilege Violation: 'User TestUser is not privileged for the operation'"
![image](https://user-images.githubusercontent.com/18219467/143900764-fe45525c-3942-415d-8aa9-e90bc550c3a5.png)

* Navigate to http://localhost:52773/csp/user/index.csp by using SuperUser | SYS and assign read access by clicking "Grant Read/Write Access"
Now navigate back to http://localhost:52773/csp/user/scw.DataForm.cls for data form by using *TestUser | demo* and data can be viewed and updated successfully

![image](https://user-images.githubusercontent.com/18219467/143901209-ec5d2e19-a6c5-4670-af52-95983fc6f269.png)

## GRANTING ALL PRIVILEGES
* Log in to management portal from docker http://localhost:52773/csp/sys/%25CSP.Portal.Home.zen using *TestUser | demo*
System will raise the "ERROR #940: Insufficient privilege for operation"
![image](https://user-images.githubusercontent.com/18219467/143904877-714ddd94-bdfb-4fa6-a2bf-e69952fcb24a.png)

* Navigate to http://localhost:52773/csp/user/index.csp index page by using SuperUser | SYS and Grant all privileges to TestUser by pressing "Grant All Privilege" button.
Now login to management portal http://localhost:52773/csp/sys/%25CSP.Portal.Home.zen by using *TestUser | demo* and now user has all privileges
![image](https://user-images.githubusercontent.com/18219467/143905675-2415fc00-cb9d-4099-a2ed-e93ecaf151c3.png)


## ENABLE/DISABLE WEB APPLICATION
* Navigate to web terminal application by clicking Web Terminal menu option
![image](https://user-images.githubusercontent.com/18219467/143905910-8e65a149-8fc2-48f9-bf95-bf0771aeb6b2.png)

* After providing credentials web terminal application will open
![image](https://user-images.githubusercontent.com/18219467/143906332-e884bc13-488a-409a-aec7-bdfb812f8177.png)

* Let's disable web terminal application by clicking "Disable WebTerminal Application". 
 Now Navigate to web terminal application by clicking Web Terminal menu option and system will display message that application not found
 ![image](https://user-images.githubusercontent.com/18219467/143906819-b37e725d-d023-471f-a065-56b07bf971a5.png)

Web terminal application can be enabled by clicking "Enable WebTerminal Application" button.


## AUTHENTICATE/UNAUTHENTICATE WEB APPLICATION
 * Now Let's disable all the authentications for Web Terminal Application by pressing "Disable WebTerminal Authentication". 
 System will not allow to enter even providing correct credentials
 ![image](https://user-images.githubusercontent.com/18219467/143907300-e6177d2b-5b38-4d67-9b2d-3e11fa19169c.png)

Web terminal application Authentication can be enabled by clicking "Enable WebTerminal Authentication" button.



Thanks


## Special Thanks to:
Evgeny Shvarov for: https://openexchange.intersystems.com/package/secured-rest-api template for guidance



