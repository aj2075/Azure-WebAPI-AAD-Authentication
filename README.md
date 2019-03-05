# Accessing Azure App Service Web API  using Azure AD bearer token (OAuth 2.0 client credentials grant flow)

## Summary
This article shows how to invoke an Azure AD protected Web API from any client application (native or web) using [OAuth 2.0 client credentials grant flow](https://docs.microsoft.com/en-us/azure/active-directory/develop/v1-oauth2-client-creds-grant-flow).
Below are the key charateristics of the Web API. 

- Web API is deployed to Azure App Service
- Web API is protected by Azure AD Authentication

The [OAuth 2.0 client credentials grant flow](https://docs.microsoft.com/en-us/azure/active-directory/develop/v1-oauth2-client-creds-grant-flow) as shown below below involves aquiring a bearer token from Azure AD token service and then invoking the Web API with that token.This method can be used by any client (native or web) to access the Web API from anywhere.

![client credentials grant flow](/images/ccgf.PNG)

This document provides step by step instructions for doing the following

- build a simple Web API with ASP.Net Core
- deploy the Web API to Azure App Service
- enable Azure AD authentication for the Web API
- successfully invoke the API from Postman using the bearer token obtained from Azure AD.


## Prerequisites
1. [Install Git](https://git-scm.com/)
1. [Install .Net Core](https://dotnet.microsoft.com/learn/dotnet/hello-world-tutorial/intro)
1. [Install Postman for windows](https://www.getpostman.com/downloads/)
1. **optional:** [Install visual studio code](https://code.visualstudio.com/Download)
1. **optional:** [Install python](https://www.python.org/downloads/)

# Step by step instructions

## 1. Build a simple Web API with ASP.Net Core

First make sure you have successfully installed .Net Core and Git on your desktop. Then open a command propmt either directly or from visual studio code (Terminal > new Terminal). It's perfectly fine if you chose not to install visual studio code, just open the command prompt by typing "cmd" in the search box in the lowerleft corner. 
 
**1. Run the following command in the command shell to create a Web API starter project**
```msdos
dotnet new webapi -o RetailApi
```
*The preceding command uses an ASP.NET Core project template, aliased as webapi, to scaffold a C#-based starter web API project. A directory named RetailApi is created that contains an ASP.NET Core project targeting .NET Core. The project name matches the directory name.*

**2. Run the following command in command shell to change directory to the newly created RetailApi folder**
```msdos
cd ./RetailApi
```
*Make sure the following files and directories are created Controllers/ , Program.csm RetailApi.csproj, Startup.cs*

**3. Run the following command in command shell to build and test the API**
```msdos
dotnet run
```
*The preceding command will start the Web API locally The Web API will be hosted at both ```http://localhost:5000``` and ```https://localhost:5001```*

**4. Verify the API**  
Open a browser and type ```https://localhost:5001/api/values```. You should see the following

![browser output](/images/retailapibrowseroutput.PNG)

alternatively,  you can also use the following to verify the output from your Web API
```curl
curl -k -s https://localhost:5001/api/values | python -m json.tool
```

please visit [Build a web API with ASP.NET Core](https://docs.microsoft.com/en-us/learn/modules/build-web-api-net-core/) on microsoft learn for detailed instructions on building a simple ASP.NET Code web API. **Disclaimer**: Some of the above steps are a copy-paste from the preceeding link.

    ![browser output](/images/deploymentcredentials.PNG)
## 2.Deploy the Web API to Azure App Service

**1. Create a Web App in Azure** following the instructions [here](https://docs.microsoft.com/en-us/learn/modules/host-a-web-app-with-azure-app-service/2-create-a-web-app-in-the-azure-portal). I named my app "RetailApi" and the app service plan "RetailApi-app-service-plan". You could choose any name you like.

**2 Prepare the local git for the Web App you created**

   1. Click on Deployment Center > Local Git > Continue > App Service Kudu build server >continue > finish
   
    
  
   
   1. Create deployment credentials for your Web App. Go to your Web App > Click on Deployment Center > Click on Deployment Credentials     > User Cedentials > Enter a user name and password and click on save. 
   
    ![deployment credentials](/images/deploymentcredentials.PNG)
    
    
   1. Select the build server

## 3.Enable Azure AD authentication for the Web API

## 4.Invoke the API from Postman using the bearer token obtained from Azure AD

