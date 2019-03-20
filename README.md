# SCM_API_Library
A work in progress library of SpringCM API calls in Postman. This JSON is data dump including Collections, Globals( w/out keys/ids), and Header Presets

## Import and Configuration

### Import

There are two different ways to Import this postman Library into your Postman workspace. Option 1 is to individually download the collections and environments(as needed) and then add them into your library. Option 2 is to download and then import the entire "Dump" file into your postman workspace. If you decided to use option 2, then you will potentially overwrite existing data in your workspace. If you have no data in your workspace, then this option is safe.

#### Option 1 - Import Collections and Environments separately

Clone this repo and then select "Import" from the top left of the Postman Workspace:

![Image of Import Button](https://github.com/Heintzdm/SCM_API_Library/blob/master/images/Import_Image.png)


Finally, select all of the files ending in collection.json. You will see your postman collections tab populate with all of the collections. 

To import environmets, select the cog wheel at the top righthand side of Postman:

![Image of Cog Wheel here](https://github.com/Heintzdm/SCM_API_Library/blob/master/images/cog_wheel.png)

Select "Import" and then choose all environments that you wish to import (UAT,EU11,NA11,NA21 **missing EU 21**)

#### Option 2 - Import Dump File

Clone this repo and then click on the wrench at the top right of the Postman console and select "Settings". From the "Data" tab, select "Choose Files" and then select the file named "SCM_Library_Dump.json" from this repo. This will import collections and environments at once.


### Configuration

This library requires access to a SpringCM account and a key/secret REST API combo. You will likely not get access to either unless you are a SpringCM customer. Once you are a customer you may reach out to the support team to request an API Key/Secret. For the purpose of this guide, I will assume you are setting up this library with a UAT account. There are also three differnent common ways to authenticate in SpringCM ( API User, Salesforce Client, and Oauth 2.0 ), for this guide I will explain the API User flow as it is the easiest to use for testing.

## API User Authentication Flow Set up

1. First log into your SpringCM account and map your ClientID to an API user. This setup is discussed here:
[Api User Auth Setup](https://developer.springcm.com/guides/api-user-authentication-flow)

2. From Postman, select the cog wheel at the top right and click on "UAT" to open up UAT specific environment variables
3. Add two variables "client_id" and "client_secret". Set the values with respective ID/Secret that you retrieved from SpringCM support and save.
4. Now you should be able to authenticate in Postman by opening the "Authentication" collection, finding the "API User Authentication Flow" call, and hitting the blue "SEND" to make the call. The response will be parsed and the auth token will be captured as a variable that is auto added to other collections.

## Other variables that need to be set up

Most of these calls center around either a "Folder" or a "Document" object. These calls will not work unless you are passing a SpringCM Folder or Document into the call. Please create an environment or global variable for docid and folderid in order to make the calls. You can create/upload a folder/document into SpringCM and then retrieve it's ID from the URL. 

Other variables: There are some other variables that you may need to set. In the call you will see the variable name between curly braces in RED if the variable value isn't set. 







