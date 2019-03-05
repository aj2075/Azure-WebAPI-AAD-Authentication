# Accessing Azure App Service Web API  using Azure AD bearer token (OAuth 2.0 client credentials grant flow)

## Summary
This article shows how to invoke an Azure AD protected Web API from any client (native or web) using [OAuth 2.0 client credentials grant flow](https://docs.microsoft.com/en-us/azure/active-directory/develop/v1-oauth2-client-creds-grant-flow).
Below are the key charateristics of the Web API. 

- Web API is deployed to Azure App Service
- Web API is protected by Azure AD Authentication

The above described flow involves aquiring a bearer token from Azure AD token service and then invoking the Web API with that token.This method can be used by any client (native or web) to access the Web API from anywhere.


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

## 1.Building a simple Web API with ASP.Net Core

First make sure you have successfully installed .Net Core and Git on your desktop. Then open a command propmt either directly or from visual studio code (Terminal > new Terminal). It's perfectly fine if you chose not to install visual studio code, just open the command prompt by typing "cmd" in the search box in the lowerleft corner. After that simply execute the following commands in the command prompt.

**1. Create a Web API starter project**
```msdos
dotnet new webapi -o RetailApi
```
*The preceding command uses an ASP.NET Core project template, aliased as webapi, to scaffold a C#-based starter web API project. A directory named RetailApi is created that contains an ASP.NET Core project targeting .NET Core. The project name matches the directory name.*

**1. Change directory to the newly created RetailApi folder
```msdos
cd ./RetailApi
```

please visit [Build a web API with ASP.NET Core](https://docs.microsoft.com/en-us/learn/modules/build-web-api-net-core/) on microsoft learn for detailed instructions on building a simple ASP.NET Code web API. disclaimer: Some of the above steps are a copy-paste from the preceeding link.

